IIS
========================================

IIS 6.0
----------------------------------------
- 后缀解析 ``/xx.asp;.jpg``
- 目录解析 ``/xx.asp/xx.jpg`` (xx.asp目录下任意解析)
- 默认解析 ``xx.asa`` ``xx.cer`` ``xx.cdx``
- PROPFIND 栈溢出漏洞
- RCE CVE-2017-7269
- PUT漏洞
    - 开启WebDAV
    - 拥有来宾用户 且来宾用户拥有上传权限
    - 课任意文件上传

IIS 7.0-7.5 / Nginx <= 0.8.37
----------------------------------------
在Fast-CGI开启状态下，在文件路径后加上 ``/xx.php`` ，则 ``xx.jpg/xx.php`` 会被解析为php文件

Windows特性
----------------------------------------
Windows不允许空格和点以及一些特殊字符作为结尾，创建这样的文件会自动取出，所以可以使用 ``xx.php[空格]`` ， ``xx.php.``， ``xx.php/``， ``xx.php::$DATA`` 可以上传脚本文件

文件名猜解
----------------------------------------
在支持NTFS 8.3文件格式时，可利用短文件名猜解目录文件。其中短文件名特征如下：

- 文件名为原文件名前6位字符加上 ``~1`` ，其中数字部分是递增的，如果存在前缀相同的文件，则后面的数字进行递增。
- 后缀名不超过3位，超过部分会被截断
- 所有小写字母均转换成大写的字母
- 文件名后缀长度大于等于4或者总长度大于等于9时才会生成短文件名，如果包含空格或者其他部分特殊字符，则无视长度条件

参考链接
----------------------------------------
- `利用Windows特性高效猜测目录 <https://xz.aliyun.com/t/2318>`_
