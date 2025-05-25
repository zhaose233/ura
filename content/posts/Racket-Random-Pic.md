---
title: 用racket重写随机图片API！
date: 2021-07-11 04:33:09


---

# 用racket重写随机图片API！

之前我写过一篇用nodejs进行随机图片的API，作为一个lisp信徒我决定用racket——一门sheme的方言来重写它

### 先安装racket

以下是Ubuntu上的安装方法
```bash
sudo apt install racket
```

然后在一个目录下新建data.txt，把你的图片的链接都放进去

接着新建一个web.rkt：
```racket
#lang racket

(require web-server/servlet)
(require web-server/servlet-env)

(define url-list '())

(call-with-input-file "data.txt"
  (lambda (in)
    (let loop ((this-line (read-line in)))
      (cond ((not (eof-object? this-line)) (set! url-list (append url-list (list this-line)))
                                          (loop (read-line in))
                                          )
           )
      )))

(define (random-url req)
  (response/xexpr (list-ref url-list (random (length url-list))))
  )

(define (random-html req)

  (response/xexpr `(html (head (title "zhaose's api"))
                        (body (h1 "zhaose's api")
                             (p (img (( src ,(list-ref url-list (random (length url-list)))))))
                             )
                        )
                 ))

(define (my-random req)
  (if (empty? (url-query (request-uri req))) (random-html req)
     (random-url req)
     ))


(serve/servlet my-random #:port 8080 #:listen-ip "0.0.0.0" #:servlet-path "/")
```

保存好之后用racket web.rkt就可以运行了

这是要注意的是如果你不加get请求参数返回的是一个html界百，加了get请求参数的话则会返回一个链接或者303跳转，可以用于机器人等的使用，如：

<http://49.234.70.34:8080>是html界面

<http://49.234.70.34:8080?mode=text>返回的是链接

<http://49.234.70.34:8080?mode=jump>是303跳转

这确实是lisper的自我修养

**by 从晴朗的朝色泛起之际开始**
