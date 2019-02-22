CGI,FastCGI,PHP-FPM

+ CGI（Common Gateway Interface）
 
        CGI 是Web 服务器运行时外部程序的规范,按CGI 编写的程序可以扩展服务器功能。CGI 应用程序能与浏览器进行交互,还可通过数据库API 与数据库服务器等外部数据源进行通信,从数据库服务器中获取数据。格式化为HTML文档后，发送给浏览器，也可以将从浏览器获得的数据放到数据库中。几乎所有服务器都支持CGI,可用任何语言编写CGI,包括流行的C、C ++、VB 和Delphi 等。CGI 分为标准CGI 和间接CGI两种。标准CGI 使用命令行参数或环境变量表示服务器的详细请求，服务器与浏览器通信采用标准输入输出方式。间接CGI 又称缓冲CGI,在CGI 程序和CGI 接口之间插入一个缓冲程序，缓冲程序与CGI 接口间用标准输入输出进行通信

+ FastCGI
 
        FastCGI像是一个常驻(long-live)型的CGI，它可以一直执行着，只要激活后，不会每次都要花费时间去fork一次(这是CGI最为人诟病的fork-and-execute 模式)。它还支持分布式的运算, 即 FastCGI 程序可以在网站服务器以外的主机上执行并且接受来自其它网站服务器来的请求。
FastCGI是语言无关的、可伸缩架构的CGI开放扩展，其主要行为是将CGI解释器进程保持在内存中并因此获得较高的性能。众所周知，CGI解释器的反复加载是CGI性能低下的主要原因，如果CGI解释器保持在内存中并接受FastCGI进程管理器调度，则可以提供良好的性能、伸缩性、Fail- Over特性等等。

+ php-fpm

        php-fpm是常和nginx搭配使用的程序，php-fpm实际上就是对FASTCGI协议的一个加强实现，已经被纳入PHP内核，可以通过--enable-fpm编译选项来启用，php-fpm支持配置的平滑变更（通过fork新的worker进程），性能好，内存使用效率高，这也是为什么nginx+php-fpm的配置组合会替代apache+mod_cgi以及apache+mod_php的重要原因

+ 关系
 
        CGI针对每个http请求都是fork一个新进程来进行处理，处理过程包括解析php.ini文件，初始化执行环境等，然后这个进程会把处理完的数据返回给web服务器，最后web服务器把内容发送给用户，刚才fork的进程也随之退出。 如果下次用户还请求动态资源，那么web服务器又再次fork一个新进程，周而复始的进行。
        而Fastcgi则会先fork一个master，解析配置文件，初始化执行环境，然后再fork多个worker。当请求过来时，master会传递给一个worker，然后立即可以接受下一个请求。这样就避免了重复的劳动，效率自然是高。而且当worker不够用时，master可以根据配置预先启动几个worker等着；当然空闲worker太多时，也会停掉一些，这样就提高了性能，也节约了资源。这就是Fastcgi的对进程的管理。大多数Fastcgi实现都会维护一个进程池。
        cgi、fastcgi 通常指 Web 服务器与解释器通信的协议规范，而 php-fpm 是 fastcgi 协议的一个实现