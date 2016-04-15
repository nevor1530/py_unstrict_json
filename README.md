# py_unstrict_json
支持不严谨的json串转成 python的dict类型
参考http://www.json.org.cn/的文法，修改文法的定义如下
pair: string ':' value
    | id ':' value
string: ""
      | " chars "
      | ' chars '
json串支持下面两种注释
// comment
/* comment */
