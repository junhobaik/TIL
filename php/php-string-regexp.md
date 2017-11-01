# PHP 문자열 처리 & 정규표현식

## 문자열 처리

문자와 문자를 더할 때는 '.'(마침표)를 사용한다.

```php
<?php
$a = "hello";
$b = "world";
echo $a.$b;
?>
```

문자열 안에서 변수를 사용하려면 쌍따옴표 안에서 {, }(중괄호)를 사용한다.

```php
<?php
$a = array('hello', 'world');
echo "{$a[0]} {$a[1]}";
echo '$a[0].' '.$a[1];
?>
```

#### 주요 함수

##### strpos

문자열이 처음 나타나는 위치를 찾습니다

http://us1.php.net/manual/en/function.strpos.php

```php
mixed strpos ( string $haystack , mixed $needle [, int $offset = 0 ] )
```

```php
$mystring = 'abc';
$findme   = 'a';
$pos = strpos($mystring, $findme);
echo $pos //0
```

##### implode

문자열로 배열 원소를 결합

```php
<?php

$array = array('lastname', 'email', 'phone');
$comma_separated = implode(",", $array);

echo $comma_separated; // lastname,email,phone

?>
```

##### explode

문자열을 문자열로 나눔

```php
<?php
$pizza  = "piece1 piece2 piece3 piece4 piece5 piece6";
$pieces = explode (" ", $pizza);
echo $pieces[0]; // piece1
echo $pieces[1]; // piece2
```

##### htmlspecialchars

특수 문자를 HTML 엔터티로 변환

```php
<?php
$new = htmlspecialchars("<a href='test'>Test</a>", ENT_QUOTES);
echo $new; // &lt;a href=&#039;test&#039;&gt;TEST&lt;/a&gt;
?>
```

## 정규표현식

#### preg_match

검색을 수행하고 일치하는 내용을 반환

```php
preg_match("/php/i", "PHP is the web scripting language of choice."))
```

#### preg_replace

검색한 다음 치환명령을 수행

```php
<?php
$string = 'April 15, 2003';
$pattern = '/(\w+) (\d+), (\d+)/i';
$replacement = '${1}1,$3';
echo preg_replace($pattern, $replacement, $string);
?>
```

<br/><br/><br/><br/><br/>

---

## Reference

- [생활코딩 PHP 기본 강의](https://opentutorials.org/module/6)