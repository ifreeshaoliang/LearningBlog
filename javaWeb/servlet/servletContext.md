## servletContext
### 介绍
>ServletContext，是一个全局的储存信息的空间。服务器开始，其就存在，服务器关闭，其才释放。

>request，一个用户可有多个；session，一个用户一个；而servletContext，所有用户共用一个。

>所以，为了节省空间，提高效率，ServletContext中，要放必须的、重要的、所有用户需要共享的线程又是安全的一些信息。
