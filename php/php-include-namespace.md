# PHP include & namespace

## include

a.php

```php
<?php
function welcome(){
    return 'Hello world';
}
?>
```

b.php

```php
<?php
include 'a.php';
echo welcome();
?>
```

### require

include와 require의 차이점

include: 존재하지 않는 파일을 로드 시도시, Warning

require: 존재하지 않는 파일을 로드 시도시, fatal error



**외부 파일의 로드 방법은 4가지가 있다**

- include
- include_once
- require
- require_once

_once가 붙으면 파일을 로드 할 때 단 한번만 로드하면 된다는 의미

## namespace

#### 문제 상황

a.php & b.php

```php
<?php
function welcome(){
    return 'Hello world';
}
?>
```

c.php

```php
<?php
require_once 'a.php';
require_once 'b.php';
echo welcome(); // Fatal error: ...
?>
```

#### namespace 사용

a.php

```php
<?php
namespace type\a;
function welcome(){
    return 'Hello world';
}
?>
```

b.php

```php
<?php
namespace type\b;
function welcome(){
    return 'Hello world';
}
?>
```

c.php

```php
<?php
require_once 'a.php';
require_once 'b.php';

echo type\a\welcome();
echo type\b\welcome();
?>
```

#### 하나의 파일에 복수의 네임 스페이스가 존재할 수 있다.

```php
<?php
namespace language\en;
function welcome(){
    return 'Hello world';
}
namespace language\ko;
function welcome(){
    return '안녕세계';
}
```

```php
<?php
require_once 'greeting_lang.php';
echo language\ko\welcome();
echo language\en\welcome();
?>
```

<br/><br/><br/><br/><br/>

---

## Reference

- [생활코딩 PHP 기본 강의](https://opentutorials.org/module/6)