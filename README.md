# 33.IDCode
php 根据自增id创建唯一编号类

## 介绍
在开发过程中，我们数据表一般都使用自增数字作为id主键，而id是数字型，不容易理解。我们把id按一定格式转为编号后，很容易根据编号知道代表的是什么内容。
<br>
<br>
例如订单表id=20160111197681234，只看id我们并不知道这个id是订单表的id，而转为编号O-20160111197681234，则很容易看出是订单表的记录，然后可以根据id在订单表中搜寻。
<br>
<br>
编号创建的规则
<br>
1.唯一
<br>
使用自增id生成，保证唯一性
<br>
2.尽可能短
<br>
可使用数字求余对应字母的方式处理，创建较短的编号
<br>
<br>
算法原理
<br>
1.加自定义前缀，用于标识
<br>
2.格式使用前缀＋字母＋数字组成，数字只保留N位，超过的使用数字求余的方式使用字母对应
<br>
例如:
<br>
id=1
<br>
前缀=F
<br>
数字保留3位
<br>
则创建的编号为：F-A-001
<br>
<br>
## 演示代码
```php
<?php
require 'IDCode.class.php';

$test_ids = array(1,9,10,99,100,999,1000,1009,2099,3999,9999,14999,99999);

foreach($test_ids as $test_id){
    echo $test_id.' = '.IDCode::create($test_id, 3, 'F').'<br>';
}
?>
```

<br>

## 输出

```
1 = F-A-001
9 = F-A-009
10 = F-A-010
99 = F-A-099
100 = F-A-100
999 = F-A-999
1000 = F-B-000
1009 = F-B-009
2099 = F-C-099
3999 = F-D-999
9999 = F-J-999
14999 = F-O-999
99999 = F-VD-999
```
