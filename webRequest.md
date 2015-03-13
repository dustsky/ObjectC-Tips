#### POST网络请求
---
##### 使用苹果自带api 进行网络POST网络请求
1. 初始化url
		
		NSString *urlStr = @"myurl";
	  	NSMutableURLRequest *request = [[NSMutableURLRequest alloc] initWithURL:[NSURL URLWithString:urlStr]];
	  	
2. 设置请求类型，所带参数
    
		request.HTTPMethod = @"POST";
		request.HTTPBody = data;
		[request setValue:@"application/json" forHTTPHeaderField:@"Content-Type"];
	   
3. 新建队列 
   
    	NSOperationQueue *queue = [[NSOperationQueue alloc]init]; //新建队列
    	//---1.SBJson库  nsdictionary ---> nsdata
	    SBJsonWriter *writer = [[SBJsonWriter alloc] init];
	    NSData *data = [writer dataWithObject:params];
	   	//---2.系统自带库 nsdictionary ----> nsdata
	    NSData *data = [NSKeyedArchiver archivedDataWithRootObject:params];
4. 发送异步请求
    
    	[NSURLConnection sendAsynchronousRequest:request queue:queue completionHandler:^(NSURLResponse *response, NSData *data, NSError *connectionError) {
    	//1.0 SBJson库 nsdata ---->nsdictionary
        SBJsonParser *parser = [[SBJsonParser alloc] init];
        NSDictionary *dic = [parser objectWithData:data];
       //2.0 系统自带库 nsdata ---->nsdictionary
       NSDictionary *dict = [NSJSONSerialization JSONObjectWithData:responseObject options:NSUTF8StringEncoding error:nil];
       }];
       
---
##### AFNetworking实现POST网络请求

url所带参数使用dictionary 类型params传递，不需要我们自己再次转换，真的很伟大的网络库。 在请求成功之后拿到data数据之后如上所述进行类型转换。

	 AFHTTPClient *httpClient = [[AFHTTPClient alloc]initWithBaseURL:url];
	 
    [httpClient postPath:nil parameters:params success:^(AFHTTPRequestOperation *operation, id responseObject) { 
    	//
     } failure:^(AFHTTPRequestOperation *operation, NSError *error) {
        //
    }];
    
---
##### 支付宝在请求签名时注意事项
假如在签名放在服务端实现，根据订单order 进行post网络请求(AFNetworking)之后拿到数据字典，如：

	NSDictionary *dict = [NSJSONSerialization JSONObjectWithData:responseObject options:NSUTF8StringEncoding error:nil];
	//得到签名字符串
如果此时网络请求得到的签名字符串包含有特殊字符串/,=等,在请求支付宝订单支付之前，需要将signString中所含特殊字符转换为符合url请求字符,因此在下面代码中不该用~~signString~~

	NSString *signString = dict[@"sign"];
        orderString = [NSString stringWithFormat:@"%@&sign=\"%@\"&sign_type=\"%@\"",orderSpec, signString , @"RSA"];
    //
而用代码转换之后的字符串[self urlValueEncode:signString],所使用函数如下所示
	
	- (NSString *)urlValueEncode:(NSString*)str
	{
   		 NSString *result = (NSString*)CFBridgingRelease(CFURLCreateStringByAddingPercentEscapes(kCFAllocatorDefault,(CFStringRef)str,                                                       NULL,CFSTR("!*'();:@&=+$,/?%#[]"),                                                        kCFStringEncodingUTF8));
    	NSLog(@"Sign=%@",result);
    	return result;
	}


