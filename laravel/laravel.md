* [1.laravel资料笔记](#1)
    * [1.1 laravel 常用包](#1.1)
    * [1.2 laravel跨库查询方式](#1.2)
    
<h1 id="1">laravel资料笔记</h1>
<h2 id="1.1">laravel常用命令包</h2>
### laravel跨库查询
##### atabase.php 里设计如下
        'mysql' => [
        'driver'    => 'mysql',
        'host'      => env('DB_HOST', 'localhost'),
        'database'  => env('DB_DATABASE', 'forge'),
        'username'  => env('DB_USERNAME', 'forge'),
        'password'  => env('DB_PASSWORD', ''),
        'charset'   => 'utf8',
        'collation' => 'utf8_unicode_ci',
        'prefix'    => '',
        'strict'    => false,
    ],
    'mysql_center' => [
        'driver'    => 'mysql',
        'host'      => env('DB_HOST', 'localhost'),
        'database'  => env('DB_DATABASE_CENTER', 'forge'),
        'username'  => env('DB_USERNAME', 'forge'),
        'password'  => env('DB_PASSWORD', ''),
        'charset'   => 'utf8',
        'collation' => 'utf8_unicode_ci',
        'prefix'    => '',
        'strict'    => false,
    ],
##### model User.php
    class User extends Model implements AuthenticatableContract, CanResetPasswordContract
    {
    protected $connection = 'mysql_center';
    
#### DB 操作
     $results = DB::connection('mysql')->select('...');
     $results = DB::connection('mysql_center')->select('...');
<h2 id="1.2">laravel常用跨库查询方式</h2>
