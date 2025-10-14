#.gitignore学习
> .gitignore文件匹配规则
- 空行或者以#开头的行会被Git忽略
- *通配任意字符,可匹配任意长度的字符,比如 *.log能匹配当前目录下所有带.log扩展名的文件（如app.log、error.log）,但不能匹配子目录中的src/app.log
- ?仅匹配1个任意字符，多1个或少1个字符都不匹配。比如?.jpg，能匹配a.jpg、1.jpg，但无法匹配ab.jpg、.jpg
- []匹配括号内的任意1个字符，支持单个字符或字符范围。例如file[0-9].txt，可匹配file0.txt到file9.txt；file[abc].txt则能匹配filea.txt、fileb.txt、filec.txt
- ** 能匹配任意层级的目录，例如dist/**/*.jpg，可匹配dist目录下所有子目录中的.js文件，像dist/app.jpg、dist/src/happy.jpg都能被匹配到
- !表示取反,需放在对应的匹配规则之后。比如先写*.log（忽略所有.log文件），再写!important.log（不忽略important.log），这样就能实现忽略大部分.log文件，仅保留important.log
- /可限定匹配。比如/logs/，仅忽略根目录下的logs目录（如logs/error.log），不会忽略子目录中的log目录（如src/logs/error.log）
---
> 下面是一些实战用法
- 直接写名称**dist**,如下图.可以发现不管是文件还是文件夹都可以匹配到,不只是第一层,子目录里面的文件和文件夹都可以匹配
![示例](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a2641e25b82f4e328e987d43a6489f15~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1920&h=888&s=111314&e=png&b=ffffff)
- /在前面 **/dist**,如下图.当/在前面的时候,/dist只能匹配gitignore当前根目录下的dist文件或文件夹
![示例](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/dbd04152ca554140b5a55789ae5c4e38~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1908&h=872&s=109817&e=png&b=ffffff)
![示例](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f34250f54c4446d0822b011fa3e00b94~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1800&h=1000&s=115044&e=png&b=ffffff)
