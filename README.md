# [API v1] Smart Tribune PHP Wrapper

## Introduction

Provides an easy to use PHP wrapper for the last version of [Smart Tribune API](https://www.smart-tribune.com/developpeurs-documentation-ressources/api/).
This class will help you to authenticate and call Smart tribune API with a few lines of code runing PHP language.

### Prerequisites

Make sure to have the following details:
* Smart Tribune API Key
* Smart Tribune API Secret
* PHP 5.x - 7.x
* This PHP class

## Installation

First clone the repository
```
git clone https://github.com/smart-tribune/apiv1.1-php.git
```

Go into the apiv1.1-php folder and create a file (eg: ```smart-tribune-api-call.php```)
```
cd apiv1.1-php
vim smart-tribune-api-call.php
```

You are now ready to make some api calls !

## Usage

In your smart-tribune-api-call.php file, you need to include the php wrapper :

```php
include("st-wrapper-php-api1.1.php");
```

Now you can start working with the smart-tribune-api-call.php file by creating a new Smart Tribune object with your api key and secret:
```php
$st = new SmartTribune ( $apiKey, $secretKey );
```

Now what you're going to do next depends on what you want to GET, POST, PUT or DELETE from Smart Tribune servers through the API.
Check out our [API documentation](https://www.smart-tribune.com/developpeurs-documentation-ressources/api/) to see all the available endpoints and resources.

We've made api calls even easier, you can now create your method like : **api-method_action-verb**
For example if you want to create a new feedback this would be **feedbacks_create**

Available actions are : get, create, update, delete. 
**Info :** If nothing specified get action will be used. 
Related HTTP VERB are used to send call : GET, POST, PUT, DELETE


So you will need to specify which resource to call this way (resource Feedbacks in this example) with an array of parameters ```$params``` :
```php
$st->feedbacks($params);  ( equivalent to $st->feedbacks_get($params); )
```

## Examples

- Retrieve discussions from a platform :
```php

$st = new SmartTribune();

$params = array(
    'platform_id' => XXX
);
$reponse = $st->feedbacks($params)

```

- Create a new discussion on a platform :
```php

$st = new SmartTribune();

$params = array(
  	'platform_id' => XXX,
  	'category_id' => XXX,
  	'theme_id' => XXX,
  	'title' =>  'title of the discussion',
  	'body' => 'Full description of the discussion',
  	'mood_id' => XXX
);
$reponse = $st->feedbacks_create($params)

```

- Update an existing discussion :
```php

$st = new SmartTribune();

$params = array(
  	'feedback_id' => XXX,
  	'state_id' => XXX
);
$reponse = $st->feedbacks_update($params)

```

## Reporting issues

Open an issue on github.
