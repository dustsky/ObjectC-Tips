### UIWebView

使用`UIWebView`加载Web内容到应用中，在此之前，需要创建一个UIWebView对象,以及有一个webpage.

- `loadRequest:`开始加载网页
 
-  `stopLoading`停止加载网页
 
- 在使用这两个方法期间，可以使用属性`loading`检测web view 是否在jiazai进程中.
 
- 若允许用户可以向前或向后浏览历史数据，可以使用`goBack` `goForward`方法

- `detectsPhoneNumbers`属性可以设置能否自动转换电话号码格式显示

- `delegate`设置代理

- `scalesPageToFit`适应屏幕的大小展示网页内容，设置此属性为YES之后用户便可通过手势操作显示网页的缩放.


### UIWebViewDelegate

- `- (BOOL)webView:(UIWebView *)webView
shouldStartLoadWithRequest:(NSURLRequest *)request
 navigationType:(UIWebViewNavigationType)navigationType`
navigationType可以设置为`UIWebViewNavigationTypeLinkClicked`拦截到用户点击事件，使用Safari打开相应网页[[UIApplication sharedApplication] openURL:request.url]

- `- (void)webViewDidStartLoad:(UIWebView *)webView` 开始请求

- `- (void)webViewDidFinishLoad:(UIWebView *)webView`结束请求

- `- (void)webView:(UIWebView *)webView
didFailLoadWithError:(NSError *)error`