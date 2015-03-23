#### 存储读取下载文件
* objective-c
	
###### 存储文件 
	
		NSString *stringURL = @"http://www.somewhere.com/thefile.png";
			NSURL  *url = [NSURL URLWithString:stringURL];
			NSData *urlData = [NSData dataWithContentsOfURL:url];
			if (urlData)
				{
				  NSArray       *paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES); 
				  NSString  *documentsDirectory = [paths objectAtIndex:0];  
		
		  NSString  *filePath = [NSString stringWithFormat:@"%@/%@", documentsDirectory,@"filename.png"];
		  [urlData writeToFile:filePath atomically:YES];
		}

###### 读取文件
	// Read both back into new NSArray and NSDictionary object
	NSArray *arrayFromFile = [NSArray arrayWithContentsOfFile:arrayPath];
	NSDictionary *dictFromFile = [NSDictionary dictionaryWithContentsOfFile:dictPath];
	 
	// Print the contents
	for (NSString *element in arrayFromFile) 
	  NSLog(@"Beer: %@", element);
	 
	for (NSString *key in dictFromFile) 
	  NSLog(@"%@ : %@", key, [dictionary valueForKey:key]);
* swift



#### 存储用户名密码等全局变量型数据

`CHUserManager.h`

	+ (void)setM_id:(NSString *)m_id;
	+ (NSString *)getM_id;
`CHUserManager.m`

	+ (void)setM_id:(NSString *)m_id
	{
	    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
	    [defaults setObject:m_id forKey:@"CH_MID"];
	    [defaults synchronize];
	}
	+ (NSString *)getM_id
	{
	    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
	    return [defaults objectForKey:@"CH_MID"];
	}
