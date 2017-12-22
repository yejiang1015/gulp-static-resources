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

    html编译任务
    ``
    // html文件编译任务最开始是使用gulp-file-include插件来实现的。但是当更改组件时不能实时编译并且相应到浏览器。并且如果没有修改内容就保存让其编译之前的内容就会报模板语法错误
    // 之后改用gulp-html-import插件来实现，但是这个插件没有实现参数的传递编译功能，只是实现了简单的导入（import）的功能
    // 现在使用gulp-include-html插件来实现，上面遇到的问题都得以解决 并且已经加入到开发环境和生产环境中

    // 代码描述
    var htmlImport = require("gulp-include-html"); // https://www.npmjs.com/package/gulp-include-html

    gulp.task('includefile' , function(){   // 定义编译模板的任务为includefile
    return gulp.src(['src/**/*.html'])      // 对所有的html文件进行编译
        .pipe(htmlImport({                  // 使用插件功能
            baseDir:'src/components/',      // 设置组件的更目录,在使用时直接使用组件名，插件会自动加上这里的路径进行拼接
            ignore: ['src/components/']     // 因为模板里面有<%= title %>这样的语法，在单独编译这个组件html文件时会报错
        }))                                  // 所以屏蔽插件对这里的文件进行编译
        .pipe(debug({title:'编译HTML:'}))    // 打印日志
        .pipe(gulp.dest("dist"));            // 编译之后的地址  
    });

    使用方法：
    index.html -->
        @@include('header.html', {
            contents:'I am so smart',
            title: '阿斯蒂芬'
        })

    header.html -->
        <div class="span4"><%= contents %></div>
        <div class="span4"><%= title %></div>

    ``



...
----------

