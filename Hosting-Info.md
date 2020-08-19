<img src="/sites/default/files/styles/adaptive/public/article/2016/hosting_whitepaper_header.png?itok=QhGCrSWe" alt="" class="image-style-adaptive" height="439" width="700">

## Русскими словами
* Операционная система: любая
  - мы используем Linux Debian/Ubuntu
* Веб сервер: Apache или Nginx или Microsoft IIS - любая современная версия
  - у нас используется Nginx
* Язык: PHP 7+ - т.е. современная версия PHP (php7.3+ на август 2020)
* База данных: MySQL 5.6+, т.е. любая современная версия или другая совместимая
  - у нас MySQL 5.6 на старых проектах, Mariadb 10.5 на новых и SQLite на сайтах-визитках;
  - друпал поддерживает PostgreSQL SQLite и множество других
* План хостинга: память 128+мб, место на диске 100+мб
  - оперативная память min 32Mb. Для комфортной работы желательно 128Mb
  - место на диске 50Mb+. Для комфортной работы 100Mb+
### Итого:
Для работы сайта на друпале подойдёт любой современный хостинг.
## Для технарей
<p>1) Web-севрер Apache 1.3 или Apache 2.x или Nginx</p>
<ul><li>mod_rewrite</li>
<li>.htaccess (Apache Virtualhost должна содержать директиву "AllowOverride All" для использования файлов .htaccess в Drupal.)</li>
<li>mbstring</li>
<li>iconv</li>
<li>Больше информации о требованиям к веб-серверу на английском&nbsp;<a href="https://www.drupal.org/requirements/webserver">тут</a></li>
</ul><p>2) PHP 5.4</p>
<ul><li>Drupal 8: PHP 5.5.9 or higher</li>
<li>Drupal 7: PHP 5.2.5 or higher (5.4 or higher recommended).</li>
<li>Settings<br>
	- register_globals off<br>
	- safe_mode off<br>
	- session.save_handler user<br>
	- session.cache_limiter nocache<br>
	- error_reporting E_ALL<br>
	- php_memory_limit не менее 100мб<br>
	- The standard PHP extensions (enabled by default) Hash and JSON are required by Drupal 7<br>
	- PDO support (extension=pdo.so and extension=pdo_mysql.so)<br>
	- The PECL version of PDO is not compatible with Drupal 7 and cannot be used</li>
<li>Больше информации о требованиям к PHP на английском&nbsp;<a href="https://www.drupal.org/requirements/php">тут</a></li>
</ul><p>3) MySQL 5.0.15 or higher with PDO</p>
<ul><li>Drupal 8:<br>
	- MySQL 5.5.3/MariaDB 5.5.20/Percona Server 5.5.8 or higher with PDO and an InnoDB-compatible primary storage engine,<br>
	- PostgreSQL 9.1.2 or higher with PDO,<br>
	- SQLite 3.6.8 or higher</li>
<li>Drupal 7:<br>
	- MySQL 5.0.15/MariaDB 5.1.44/Percona Server 5.1.70 or higher with PDO,<br>
	- PostgreSQL 8.3 or higher with PDO</li>
<li>Больше информации о требованиях к базе данных на английском&nbsp;<a href="https://www.drupal.org/requirements/database">тут</a></li>
</ul></div>

</div>
