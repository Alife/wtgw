程序说明：
详细原理请移步http://secsay.com/wordpress/?page_id=52

程序集名称Xss Network Manipulation Detector，简称XNMD。
当前主程序XCapture，使用inception方式的代理手段，对捕获到的http会话进行实时回放攻击测试。
同类优秀产品有google公司出品的ratproxy（C开发）和大名鼎鼎的paros（java开发），本软件在检测原理上并无新的突破，依然是使用代理重放HTTP会话，对各种参数进行暴力尝试。
不同的是，ratproxy安装繁琐，paros使用复杂，且这两者都有很大的误报。当然XNMD的XCapture也存在这样那样的缺点。
比如Xcapture使用了微软的fiddlercore做核心组件（好像很多人对微软的东西都嗤之以鼻），Xcapture使用实时回放导致影响一定的实时网速等等，

但是，但是，这绝对是一款极其容易使用的史无前例的XSS检测工具，有几个优点不得不专门说一下。
1、扫地大妈即可使用，到楼道里拖一个扫地大妈进来也可以做专业的黑色艺术系列安全测试。（不知道这个东西会不会砸掉很多安全测试人员的饭碗）
2、没有UI。嗯对，是没有UI。没有UI不是指使用复杂，相反，你可以远程命令行控制部署，做各种定制，等等等，做符合企业自身特点的配置。
高手都知道一个有UI的产品华而不实，难于扩展。
3、作者（secsay团队）对此还在持续升级，现在在只是0.5版本，你可以私下联系作者admin@secsay.com，给你编译一个特别的版本，或者给出一个建议，当然，有bug反馈，可能的话会请你吃冰激凌。

废话少说
----------------------------------------------------------------------------------------
版本0.5 使用说明：

初始化：
	第一次启动XCapture时候会提示设置程序启动代理端口和检测目标域，默认可一路回车。以后再次启动程序，不会再产生提示。
	初始化的设置可在config.main中进行编辑

使用：
启动主程序后，自动进入xss捕获模式，按d可以设置目标域。
然后自己开启浏览器点击链接或者填写提交表单，或在外面使用其他爬虫程序爬取网站，即可开始检测XSS。
注：程序启动后会默认给IE和chrome浏览器以及其他使用WinINET的程序设置好代理，火狐狸浏览器需要自己手动设置代理。


结果和日志：
捕获到xss后会红色字体写出url，并把对应会话保存到xssresult目录,结果为zip文件格式，可以直接拖到fiddler中打开调试


默认主界面命令：
c=Clear;清掉内存中的http session
d=Domain config; 设置需要捕获的域名，为空时捕获全部http请求
l=List session; 列出内存中的所有session
g=Collect Garbage;内存整理
h=Hosts config; hosts设置
w=write SAZ;手动写文件到磁盘
s=Toggle Forgetful Streaming; 
t=Toggle Title Counter; 
q=Quit
e=encode tools;一个简单编码工具

其他配置（非安全人员请忽略）：
	ShortMappingList.xml中可制定检测攻击字符串，目前只使用了一个尖括号进行测试。
	安全人员可增加其他字符或者敏感词汇测试。