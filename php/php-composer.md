# PHP Composer

## Composer

컴포저는 PHP의 의존성 관리도구이다. 필요한 확장 기능을 쉽게 설치해주는 기능도 제공하지만, 프로젝트에서 필요한 확장 기능을 통합해서 관리해주는 도구이다.

NPM과 같은 역활을 한다고 할 수 있다.

### 설치 (Unix)

`curl -sS https://getcomposer.org/installer | php`

##### global 사용을 위한 설정

`mv composer.phar /usr/local/bin/composer`

### 사용

packagist 에서 모듈을 검색하여 설치, 사용할 수 있다.

#### markdown 사용 관련 라이브러리 설치 예제

- 패키지를 설치해 composer.json에 추가

`$ composer require michelf/php-markdown`

- 또는 composer.json에 추가 후 명령어를 통해 설치

```json
{
    "require": {
        "michelf/php-markdown": "^1.7"
    }
}
```

`$ composer install`

- 사용

```php
<?php
require 'vendor/autoload.php';
//vendor 폴더의 패키지를 모두 자동으로 로드한다.
use Michelf\Markdown;
echo $m_html = Markdown::defaultTransform("# TEST");
//TEST 라는 h1 형식 텍스트 출력
?>
```
<br/><br/><br/><br/><br/>

---

## Reference

- [생활코딩 PHP 기본 강의](https://opentutorials.org/module/6)