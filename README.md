<p align="center">
    <a href="https://github.com/yiisoft" target="_blank">
        <img src="https://avatars0.githubusercontent.com/u/993323" height="100px">
    </a>
    <h1 align="center">Yii2 Swagger Extension</h1>
    <br>
</p>
This is fork from lichunqiang/yii2-swagger with swagger-ui 3.4.5 support. 

[swagger-php](https://github.com/zircote/swagger-php) intergation with yii2.

Integration [swagger-ui](https://github.com/swagger-api/swagger-ui) with [swagger-php](https://github.com/zircote/swagger-php).


Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist light/yii2-swagger "~1.0.4" --dev
```

or add

```
"light/yii2-swagger": "~1.0.4"
```

to the require section of your `composer.json` file.


Usage
-----

Configure two action as below:

```
public function actions()
{
    return [
        //The document preview addesss:http://api.yourhost.com/site/doc
        'doc' => [
            'class' => 'light\swagger\SwaggerAction',
            'restUrl' => \yii\helpers\Url::to(['/site/api'], true),
        ],
        //The resultUrl action.
        'api' => [
            'class' => 'light\swagger\SwaggerApiAction',
            //The scan directories, you should use real path there.
            'scanDir' => [
                Yii::getAlias('@api/modules/v1/swagger'),
                Yii::getAlias('@api/modules/v1/controllers'),
                Yii::getAlias('@api/modules/v1/models'),
                Yii::getAlias('@api/models'),
            ],
            //The security key
            'api_key' => 'balbalbal',
        ],
    ];
}
```

> For security, you can config api key for protection.

Caching
-------

```
public function actions()
{
    return [
        // ...
        'api' => [
            // ...
            'cache' => 'cache',
            'cacheKey' => 'api-swagger-cache', // default is 'api-swagger-cache'
        ],
    ];
}
```

#### Clear cache

Access clear cache url `YOUR_API_URL?clear-cache` or `YOUR_API_URL?api_key=YOUR_API_KEY&clear-cache`

Example: `curl 'http://localhost/v1/swagger/api?clear-cache'`

you will see: `Succeed clear swagger api cache.`


License
-------
![MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)
