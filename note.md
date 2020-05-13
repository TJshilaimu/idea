[top]
# 添加模块到npm
- npm官网注册账号
- npm init -y 创建摸板
- npm config get registry 查看是否为npm 路径,是则下一步，若是淘宝镜像路径则需要修改淘宝镜像路径为npm路径
- npm login 登录username、password
- npm publish (删除用 npm unpublish 模块名 --force)

# md文档设置
- 下载markdown pre插件，首选项中勾上其的允许脚本控制项
- f1>mp .css文件
- f1>mp .parser文件
## less代码

/* Please visit the URL below for more information: */
/*   https://shd101wyy.github.io/markdown-preview-enhanced/#/customize-css */ 

.markdown-preview.markdown-preview {
  // modify your style here
  // eg: background-color: blue;  
  font-family: "consolas", "Noto Sans S Chinese";
  font-size: 1em;
}

.markdown-img-description{
    text-align: center;
    margin-top: -1em;
    color: #666;;
    margin-bottom: 2em;
}

html body img{
    border:2px solid #ccc;
}

.markdown-p-center{
    text-align: center;
}



## js代码(此部分再浏览器中显示有问题)
const scripts = `<script>
    function setCurrent(){
        const links = document.querySelectorAll(".md-sidebar-toc a")
        for(const link of links){
            link.style.color="";
        }
        const hash = location.hash;
        const a = document.querySelector('a[href="'+hash+'"]');
        if(a){
            a.style.color = "#f40";
        }
    }
    setCurrent();
    window.onhashchange = setCurrent;
</script>`;
var fs = require("fs");
module.exports = {
  onWillParseMarkdown: function(markdown) {
    return new Promise((resolve, reject) => {
      const reg = /\!\[(.*)\]\((\S+)\)/gm;
      markdown = markdown.replace(reg, function(match, g1, g2) {
        var width = "100%";
        if (g1) {
          var w = g1.split("|");
          if (w.length > 1) {
            width = w[1] + "px";
            g1 = w[0];
          }
        }
        return `<p class="markdown-p-center">
  <img src="${g2}" alt="${g1}" style="max-width:${width}"/>
</p>
<p class="markdown-img-description">
  ${g1}
</p>`;
      });
      resolve(markdown);
    });
  },
  onDidParseMarkdown: function(html) {
    return new Promise((resolve, reject) => {
      return resolve(scripts + html);
    });
  }
};

