# PHP Basic

Server side script.

PHP Hypertext Preprocessor (PHP)

## 설치

### Mac에 설치하기

Mac은 기본으로 apache와 php가 설치되어있기 때문에 따로 설치할 필요는 없고 활성화만 해주면 된다.

`apachectl -v`, `php -v` 로 설치된 버전을 확인해볼 수 있다.

간단히 사용하기 위해서는 아래 과정을 거치면 된다.

1. `sudo vi /etc/apache2/httpd.conf`를 이용하여 설정 파일을 연다
2. LoadModule 중에서 php를 찾아 맨 앞의 # 을 제거한다.
3. `sudo apachectl start`로 서버를 시작한다.
4. `/Library/WebServer/Documents` 경로가 루트 작업 폴더가 된다.

하지만 위의 방법인 RootDocuments를 사용하기 보다는 UserDir을 사용하는 것을 추천한다, 자세한 설정 방법은 아래 링크를 확인하자.

[Apache : 맥에서 아파치 웹서버 실행하기 - xho95's Swift Life](https://xho95.github.io/macos/apache/webserver/mod_wsgi/2016/10/02/Apache-WebServer.html)

## 기본 구문

`<?php` `?>` 중간에 php 스크립트를 입력한다.

## 숫자와 문자

### 숫자

```php
<?php
  echo var_dump(6); //int(6)
  echo var_dump(6.1); //float(6.1)
?>
```

var_dump : 변수에 대한 정보를 반환한다

### 문자

```php
<?php
echo "Hello world"; //Hello world 
echo var_dump("Hello world")
	//string(11) "Hello world"
echo "Hello 'php' world"
echo "Hello \"php\" world"
?>
```

var_dump( [String] ) : 문자열의 길이를 반환하게 된다.


## 변수

변수의 이름을 지정할 때 이름의 앞에 `$`를 붙인다.

```php
$a = 1;
echo $a + 1; #2
```

PHP에서 주석은 `#`, `// `, `/* */` 을 이용한다.


## 비교

php도 javascript와 비슷하게 `===`가 존재한다.


## 입출력, 폼, HTTP

```php
<?php
  echo $_GET['id']. "님 환영합니다.";
  echo $_GET['month']. "M / ". $_GET['day']. "D"
?>
```

http://localhost/?id=Junho&month=12&day=31

위 URL로 접속했을때의 아래 문구가 출력된다.

 'Junho님 환영합니다. 12M / 31D'

? 뒤에 입력 데이터가 표현되고 여러 데이터들의 구분은 &로 한다.


### GET vs POST

GET : URL에 데이터를 포함시켜서 전달

```php
$_GET['id']
```

POST : URL에 포함시키지 않고 전달

```php
$_POST['password']
```


## 논리 연산자

```php
<?php
if(true and true) {};
if(true && true) {};

if(true or true) {};
if(true || true) {};

if(!true) {};

# 0 = false
# 1 = tru
```

## 함수

```php
function 함수명( [인자...[,인자]] ){
   코드
   return 반환값;
}

함수명(); //반환값
```

### 인자의 기본값

```php
<?php
function get_arguments($arg1=100){
    return $arg1;
}
echo get_arguments(1); //1
echo ',';
echo get_arguments(); //100
?>
```

## 배열

```php
$v = ['a', 'b', 'c'];
echo $v[0]; //a


function get_members(){
    return ['egoing', 'k8805', 'sorialgi'];
}
 
$tmp =  get_members();
echo $tmp[1];

echo get_members()[1];
// 위의 코드는 PHP 5.4 이상 가능한 코드
```

### 배열 크기

```php
$l = [1, 2, 3, 4, 5];
echo count($l); //5
```

## 배열 조작

### 추가

```php
<?php
$arr = ['a', 'b', 'c', 'd', 'e'];
array_push($arr, 'f');
var_dump($arr);
//array(6) { [0]=> string(1) "a" [1]=> string(1) "b" [2]=> string(1) "c" [3]=> string(1) "d" [4]=> string(1) "e" [5]=> string(1) "f" }
?>
```

#### Merge

```php
$li = ['a', 'b', 'c', 'd', 'e'];
$li = array_merge($li, ['f','g']);
var_dump($li);
```

#### unshift

```php
$li = ['a', 'b', 'c', 'd', 'e'];
array_unshift($li,'z');
var_dump($li);
```

#### splice

```php
$li = ['a', 'b', 'c', 'd', 'e', 'z'];
array_splice($li, 2, 0, 'B');
var_dump($li);
```

아래 코드는 b를 제거하고 그 자리에 B를 넣은 코드이다.

```php
$li = ['a', 'b', 'c', 'd', 'e', 'z'];
array_splice($li, 1, 1, 'B');
var_dump($li);
```

### 제거

#### shift

배열의 첫번째 요소 제거

```php
$li = ['a', 'b', 'c', 'd', 'e', 'z'];
array_shift($li);
var_dump($li);
```

#### pop

배열의 마지막 요소 제거

```php
$li = ['a', 'b', 'c', 'd', 'e', 'z'];
array_pop($li);
```

### 정렬

```php
$li = ['c','e','a','b','d'];
sort($li); //정렬
var_dump($li);

rsort($li); //역정렬
var_dump($li);
```

### 연관배열

```php
$grades = array('a'=>1, 'b'=>2, 'c'=>3);
echo $grades[0]."<br/>";
echo $grades[1]."<br/>";
echo $grades[2]."<br/>";
echo $grades['a']."<br/>";
echo $grades['b']."<br/>";
echo $grades['c']."<br/>";
echo count($grades)."<br/>";
echo var_dump($grades);

/*



1
2
3
3
array(3) { ["a"]=> int(1) ["b"]=> int(2) ["c"]=> int(3) }
*/
```

#### 연관 배열의 반복 작업

```php
foreach($grades as $key => $value){
    echo "key: {$key} value:{$value}<br />";
}
/*
key: a value:1
key: b value:2
key: c value:3
*/
```

## 파일

[PHP file function document](http://us1.php.net/manual/en/function.file.php)

### 파일 복사

```php
<?php
  $file = 'readme.txt';
  $newFile = 'readme.txt.bak';

  if(!copy($file, $newFile)){
    echo "faild to copy file\n";
  }
?>
```

### 파일 삭제

```php
<?php
	unlink('deleteme.txt');
?>
```

### 파일 읽기, 쓰기

#### file_get_contents

기존의 파일을 읽어온다, 외부 URL 또한 가능.

```php
<?php
  	$file = './readme.txt';
  	echo file_get_contents($file);
?>
```

#### file_put.contents

문자열을 파일에 저장한다.

```php
file_put_contents($file, 'put contents');
```

**Permission denied 경고 시 해결방법**

파일, 디렉토리의 소유자, 소유권 변경이 필요하다.
참고 링크 : http://brothernsister.tistory.com/27

#### fopen

http://us1.php.net/manual/en/function.fopen.php

```php
resource fopen ( string $filename , string $mode [, bool $use_include_path = false [, resource $context ]] )
```

```php
<?php
	$handle = fopen("c:\\folder\\resource.txt", "r");
?>
```

### 디렉토리 제어

#### getcwd

현재 디렉토리를 알 수 있다.

#### chdir

디렉토리 변경

### 디렉토리 탐색

scandir은 디렉토리를 탐색하는 기능이다. 첫번째 인자는 탐색할 디렉토리의 경로이고, 두번째 인자는 정렬 방법이다.

```php
<?php
$dir    = './';
$files1 = scandir($dir);
$files2 = scandir($dir, 1);
 
print_r($files1);
print_r($files2);
?>
```

### 디렉토리 생성

mkdir은 디렉토리를 생성하는 내장함수이다. 첫번째 인자로 디렉토리의 이름, 두번째 인자로 디렉토리의 권한을 지정 할 수 있다. 세번째 인자의 값으로 true를 지정하면 첫번째 인자로 주어진 경로가 여러개의 디렉토리로 이루어져 있을 때 해당 디렉토리를 한번에 생성하는 기능을 제공한다.

```php
<?php
mkdir("1/2/3/4", 0700, true);
?>
```

### 파일 업로드

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
</head>   
<body>
<form enctype="multipart/form-data" action="1.php" method="POST">
   <input type="hidden" name="MAX_FILE_SIZE" value="30000" />
   <input name="userfile" type="file" />
   <input type="submit" value="upload" />
</form>
</body>
</html>
```

- 사용자가 임의로 변경할 수 있으므로, max file size의 value값에 의존해서는 안된다.
- enctype="multipart/form-data" 지정 중요, 없으면 파일 업로드 불가

```php
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
</head>   
<body>
<?php
ini_set("display_errors", "1");
$uploaddir = 'C:\BitNami\wampstack-5.4.20-0\apache2\htdocs\upload\file\\';
$uploadfile = $uploaddir . basename($_FILES['userfile']['name']);
echo '<pre>';
if (move_uploaded_file($_FILES['userfile']['tmp_name'], $uploadfile)) {
    echo "파일이 유효하고, 성공적으로 업로드 되었습니다.\n";
} else {
    print "파일 업로드 공격의 가능성이 있습니다!\n";
}
echo '자세한 디버깅 정보입니다:';
print_r($_FILES);
print "</pre>";
?>
</body>
</html>
```

- move_uploaded_file([실제 파일의 경로],[이동시킬 경로])
- ini_set : php의 설정을 runtime으로 지정
  기존 설정에서 현 프로젝트에서만 설정을 따로 오버라이드해 사용
- basename : path 정보를 제외한 파일명만을 남기고싶을때 사용
  http://us1.php.net/manual/en/function.basename.php​

#### $_FILES

특수한 약속되어있는 변수, 사용자가 전송한 파일의 정보가 담겨있다.

http://us1.php.net/manual/en/reserved.variables.files.php

## 이미지 다루기

### GD

이미지 처리 작업은 PHP 기본 기능에 포함되어있지 않기 때문에, 대신 라이브러리나 외부 프로그램 연동이 필요하다. 이미지 처리에 가장 많이 사용되는 라이브러리는 GD가 있다.

`phpinfo();` 에서 gd support가 enabled일때는 이미 사용할 수 있는 준비가 되어있는 것이다. 만약 없다면 별도의 설정, 설치가 필요하다.

- Documentation : http://us1.php.net/manual/en/book.image.php

#### 예제

```php
<?php
header("Content-type: image/png");
$string = $_GET['text'];
$im     = imagecreatefrompng("button.png");
$orange = imagecolorallocate($im, 60, 87, 156);
$px     = (imagesx($im) - 7.5 * strlen($string)) / 2;
imagestring($im, 4, $px, 9, $string, $orange);
imagepng($im);
imagedestroy($im);
?>
```

사각형 틀의 이미지가 있다고 가정하면, 그 안에 URL로 전송된 text값을 나타내는 코드이다.

- header : HTTP protocol 지정할 수 있는 코드

---

## Reference

- [생활코딩 PHP 기본 강의](https://opentutorials.org/module/6)
- [PHP Documentation](http://docs.php.net/docs.php)










