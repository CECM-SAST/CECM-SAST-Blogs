HEXO默认目录结构

├── .deploy：执行hexo deploy命令部署到GitHub上的内容目录
├── public：执行hexo generate命令，输出的静态网页内容目录
├── scaffolds：layout模板文件目录，其中的md文件可以添加编辑
├── scripts：扩展脚本目录，这里可以自定义一些javascript脚本
├── source：文章源码目录，该目录下的markdown和html文件均会被hexo处理。该目录下可新建页面目录。
|  	├── _drafts：草稿文章
|   	└── _posts：发布文章
├── themes：主题文件目录
├── _config.yml：全局配置文件，大多数的设置都在这里
└── package.json：应用程序数据，指明hexo的版本等信息，类似于一般软件中的关于按钮