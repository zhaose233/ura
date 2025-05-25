---
title: Nodejs实现随机图片API
date: 2021-03-20 20:49:47


---

# 用node.js实现随机图片API！

前段时间我们的青河大佬自建了一个基于php的随机图API，然而由于我不愿随大流的性子，决定用不同的方法实现一个［滑稽］

### 都说了是基于node.js那当然要安装node.js啦！

首先要有一些图片，然后有这些图片的链接，把它们放到一个叫做data.txt的文本文件里，在相同目录下新建一个js文件：
```javascript
var http = require("http");
var readline = require('readline');
var fs = require('fs');

var filearr;

function readarr( filename, callback )
{
    var file = fs.createReadStream( filename );
    var line_arr = readline.createInterface(
        {
            input:file
        }
    )
    var arr = new Array();

    line_arr.on('line', (line) => {
        arr.push( line );
//        console.log( arr );
    })

    line_arr.on('close', () =>{
        filearr = arr.concat();
        callback();
    })
}

readarr( 'data.txt', () => {
    console.log("Read data.txt Finished");
    console.log( "The file has " + filearr.length + " lines" );
})

http.createServer( (req, res) => {

    res.writeHead(200, {'Content-Type': 'text/plain'});

    var whicharr = Math.floor( Math.random()*filearr.length );

    res.end( filearr[whicharr] );
}).listen(2880);

http.createServer( (req, res) => {

    res.writeHead(200, {'Content-Type': 'text/html; charset=utf-8'});

    var whicharr = Math.floor( Math.random()*filearr.length );

    res.end( `<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Zhaose's repo</title>
    <style>
      body
      {
	  background-color:#d0e4fe;
      }
      h1
      {
	  color:orange;
	  text-align:center;
      }
      p
      {
	  font-family:"Times New Roman";
	  font-size:20px;
          background-color:#dddddd;
          text-align: center;
      }
    </style>
  </head>
  <body>
    <h1>zhaose's API</h1>
    <p><img src="` + filearr[whicharr] + `"/></p>
  </body>
</html>` );
}).listen(2881);

http.createServer( (req, res) => {

    var whicharr = Math.floor( Math.random()*filearr.length );

    var url = filearr[whicharr]

    res.writeHead(301, {'Location': url });

    res.end();
}).listen(2882);

```

把这些代码输入进去以后，使用
```bash
$ node XXX.js
```
就可以启动API服务了。其中访问2880端口是返回链接，2881是一个随机的html页面，2882是直接跳转到原图链接。
祝大家愉快！

*by 从晴朗的朝色泛起之际开始
