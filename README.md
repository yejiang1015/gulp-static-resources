gulp-static-resources
=========

基于gulp的前端模块化开发，静态模板编译，postcss，代码压缩，图片体积优化，seo友好，浏览器自动刷新，提升开发效率，解放F5和复制粘贴
---------

如何开发
--------

安装依赖``$ npm install/yarn``

开发模式【热替换】``$ yarn/npm run dev``

打包``$ yarn/npm run build``

项目结构说明
----------
```
    conf/                               ---> 项目配置文件
    src/                                ---> 开发模式根目录
        assets/                         ---> 静态资源文件
            css                         ---> 样式
            img                         ---> 图片
            js                          ---> 脚本
            libs                        ---> 第三方插件
        components/                     ---> 公共组件
        home/                           ---> 首页资源文件
            img                         ---> 首页图片
            js                          ---> 首页脚本
            css                         ---> 首页样式
        views/                          ---> 展示视图库
            viewitem/                   ---> 非首页页面
                css                     ---> 非首页页面样式
                img                     ---> 非首页图片
                js                      ---> 非首页脚本
                index.html              ---> 非首页dom文档
            ····                        ---> 非首页页面
            ····                        ---> 非首页页面
        favicon.ico                     ---> ico
        favicon.png                     ---> png
        index.html                      ---> 首页HTML文档
    .bowerrc                            ---> bowerrc
    .editorconfig                       ---> 所有编译器代码风格一致配置文件
    .gitignore                          ---> gitignore
    bower.json                          ---> bower.json
    gulpfile.js                         ---> gulp配置文件
    .eslintignore                       ---> 忽略代码检查的资源
    .eslintrc                           ---> eslint配置
    package.json                        ---> package.json
    README.md                           ---> 本文件
```

功能
---------
### ``npm run dev`` 开发环境
    1. 本地服务器
    2. 自动刷新、
    3. css,html文件编译
    4. 增量任务
### ``npm run build`` 生产环境
    1. 预览服务器
    2. postcss -> css,html模板编译
    3. css打包压缩，版本控制
    4. js模块打包压缩，版本控制，公共模块与业务模块分离
    5. 图片压缩

任务
--------
    > 开发环境配置文件 ``conf/gulp.dev.conf.js``
    > 生产环境任务文件在``conf/gulp.prod.conf.js``

使用
-----------
    > 页面资源路径使用服务器方式，从根地址访问
    > components 组件引入的根目录为components/ 在引入时直接 @import "header.html"
    > 其他的引用从src/为根目录

其他
-----------
    有待完善...

参考地址：``https://github.com/bestsamcn/gulp-config``
---------