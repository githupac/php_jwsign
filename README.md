# Json Wed Sign (RSA)

This is a function wrapping through the Openssl to sign and validate the data, which ensures the integrity and security of the original data.

### Travis CI

[![Travis-ci](https://api.travis-ci.org/yakeing/php_jwsign.svg)](https://travis-ci.org/yakeing/php_jwsign)

### codecov

[![codecov](https://codecov.io/gh/yakeing/php_jwsign/branch/master/graph/badge.svg)](https://codecov.io/gh/yakeing/php_jwsign)

### Packagist

[![Version](http://img.shields.io/packagist/v/yakeing/php_jwsign.svg)](https://github.com/yakeing/php_jwsign/releases)
[![Downloads](http://img.shields.io/packagist/dt/yakeing/php_jwsign.svg)](https://packagist.org/packages/yakeing/php_jwsign)

### Github

[![Downloads](https://img.shields.io/github/downloads/yakeing/php_jwsign/total.svg)](https://github.com/yakeing/php_jwsign)
[![Size](https://img.shields.io/github/size/yakeing/php_jwsign/src/jwsign.php.svg)](https://github.com/yakeing/php_jwsign/blob/master/src/php_jwsign/jwsign.php)
[![tag](https://oauth.applinzi.com/Label/tag/v1.2.0/28a745.svg)](https://github.com/yakeing/php_jwsign/releases)
[![license](https://oauth.applinzi.com/Label/license/MPL-2.0/FE7D37.svg)](https://github.com/yakeing/php_jwsign/blob/master/LICENSE)
[![languages](https://oauth.applinzi.com/Label/languages/php/007EC6.svg)](https://github.com/yakeing/php_jwsign/search?l=php)

### Installation

Use [Composer](https://getcomposer.org) to install the library.

```

    $ composer require yakeing/php_jwsign

```

### JWSign init

```php

    $jwsign = new jwsign();
    $jwsign->SetPrivate($accesskey);

```

### Get Pubkey

```php

    $Pubkey = $jwsign->GetPubkey();

    var_dump($Pubkey);
    array(3) {
        ["pub"]=>string(451) "-----BEGIN PUBLIC KEY-----\nMIIBIjA....NjQIDAQA\n-----END PUBLIC KEY----"
        ["bits"]=>int(2048)
        ["kid"]=>string(43) "cjbdM-CeRfP...5BNYQuksIIgmk"
    }

```

### Sign Message

```php

    $Message = base64_encode('
        {
            "method":"pay",
            "charset":"utf-8",
            "version":"1.0",
            "token":"NAM...YgV"
        }
    ');

    $JsonStr = $jwsign->SignMessage($Message);

    var_dump($JsonStr);
    string(557) "{
        "message":"eyJtZXRiO...Z1YifQ==",
        "nonce":"MmlhaDE1MD...MTgwLjEwNDc1OTAw",
        "kid":"cjOdM-CORfPGa...j-0I5BNYQuksIIgmk",
        "sign":"hXvBULK2wSroVFZ...-HYHG7l8Epixikg"
        }"

```

### Pubkey Verify

```php

    $value = '{
        "message":"eyJtZXRiO...Z1YifQ==",
        "nonce":"MmlhaDE1MD...MTgwLjEwNDc1OTAw",
        "kid":"cjOdM-CORfPGa...j-0I5BNYQuksIIgmk"
        }';
    $sign = 'hXvBULK2wvSroVFZ...-HKbHGDYHG7l8Epixikg';
    $pub = '-----BEGIN PUBLIC KEY-----\nMIIBIjA....NjQIDAQA\n-----END PUBLIC KEY----';

    $Str = $jwsign->PubkeyVerify($value, $sign, $pub);

    var_dump($Str);
    bool(true)

```

### Get Message

```php

    $value = '{
        "message":"eyJtZXRiO...Z1YifQ==",
        "nonce":"MmlhaDE1MD...MTgwLjEwNDc1OTAw",
        "kid":"cjOdM-CORfPGa...j-0I5BNYQuksIIgmk"
        }';
    $Str = json_decode($value, true);

    var_dump(base64_decode($Str['message']));
    string(100) "{
            "method":"pay",
            "charset":"utf-8",
            "version":"1.0",
            "token":"NAM...YgV"
        }"

```

Donate
---
If you've got value from any of the content which I have created, then I would very much appreciate your support by payment donate.

 [Bitcoin](https://btc.com/1FYbZECgs3V3zRx6P7yAu2nCDXP2DHpwt8)

 1FYbZECgs3V3zRx6P7yAu2nCDXP2DHpwt8

 ![Bitcoin](https://raw.githubusercontent.com/yakeing/Content/master/Donate/Bitcoin.png)

 WeChat

 ![WeChat](https://raw.githubusercontent.com/yakeing/Content/master/Donate/WeChat.png)

 Alipay

 ![Alipay](https://raw.githubusercontent.com/yakeing/Content/master/Donate/Alipay.png)

Author
---

weibo: [yakeing](https://weibo.com/yakeing)

twitter: [yakeing](https://twitter.com/yakeing)
