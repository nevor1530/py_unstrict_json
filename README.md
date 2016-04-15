# py_unstrict_json

在爬取网页过程中，有些数据是通过异步加载的json，浏览器实际上是当成js代码执行转成变量的，语法上同js，非json官方定义的严格文法，如字符串可以由单引号括起，key不是字符串，包含注释等情况出现。  
python自带的json模块不支持这样的文法，于是自己实现一个支持不严谨的json串转成python的dict类型工具。

参考http://www.json.org.cn/的文法，修改部分文法的如下

    pair: string ':' value
        | id ':' value

    string: ""
          | " chars "
          | ' chars '

json串支持下面两种注释，同大部分程序语言的单行和多行注释

    // comment
    /* comment */

以module和main两种形式使用，main多用于测试，module用法如下

    # as module
    import py_unstrict_json as exjson

    # json_str is json string which mostly get from websiteimport py_unstrict_json as exjson
    # obj is a python dict
    obj = exjson.loads(json_str)

直接运行，可以带一个参数，表示输入文法，如果不带，则需要从控制台输入或者管道输入

    # as main
    $ python py_unstrict_json/json.py [file]
