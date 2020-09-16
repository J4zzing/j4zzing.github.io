1.Flask类的构造函数是怎么通过主模块或包的名字__name__来决定程序根目录的？

2.app.app_context().push()

3. current_app

4.werkzeug的csrf令牌是如何保护csrf的？


程序bug小记：
1. 用户手动输入/auth/logout


回忆flask
1.什么是WSGI Web服务器网关接口？ page7

2.什么是路由？ page8

3.什么是视图函数？如何构建?

4.什么是请求钩子，如何实现？

4.如何使用flask的flash功能？

5.如何配置flask-sqlalchemy数据库URL？SQLALCHEMY_COMMIT_ON_TEARDOWN的作用是什么？

6.如何用flask-sqlalchemy定义ORM模型类?

7.db.session.remove()
app_context = app.app_context()
app_context.push()


## check these:
- flask secret key and wtf secret key and form csrf token

- confetti or similar effect when finished register

- # pragma: no cover