<h3 id="readme">nodejs写的一个网页爬虫</h3>

1. 简介

    学习nodejs时写的一个网页爬虫，爬取慕课网上某老师的课程信息。利用node的http模块请求网页内容，使用es6的promise对象处理异步回调，将数据根据学习人数排序输出，并利用node的fs模块将数据保存至json文件中。

2. 技术栈

- nodejs + es6 + promise

3. 主要功能

- 爬取sccot老师在慕课网上的课程信息
- 将课程信息按照观看人数排序输出到console
- 将信息保存至本地json文件中

4. 碰到的问题

- promise的运用：js里的回调非常常见，但是多层回调嵌套便回形成回调地狱，node里早就开始应用promise，js里也有async.js等库，es6终于将其标准化了。异步编程真的太反人类了，很多时候不知道异步操作什么时候完成，用promise等方式将异步操作流程化是非常有必要的。es6有promise/generator,es7还有async/await，要学的还有很多。
- 通过ajax获取观看人数：慕课网课程的观看人数是通过ajax获取的，除了需要用get获取页面html还要用ajax获取观看人数，并且是多个页面同时请求，并且依赖观看人数来排序，因此需要所有异步请求完成再来进行数据的处理输出。get人数和get对应的html应该是一起的，与其他页面的并列的，当时这里把我搞懵了。后来去研究了一下promise的玩法，在获取html的promise里面再new一个获取人数的分支promise，待这个分支promise处理后再执行获取html的promise，将；两次请求的数据数据放入对象中传入then处理。

5. 总结

    本想学点后端的东西，给之前那个vue问卷项目弄个数据库，而且听说nodejs非常强大，webpack、npm、还有很多牛比的插件都依赖nodejs，非常渴望去学习一下node。这是学习的时候写的一个小程序，也算是了解一下node的玩法，对后端和整个网站的架构也有了更深的认识。后来发现我的虚拟主机只支持php，于是浅尝辄止，以后再去深入学习神奇的nodejs。