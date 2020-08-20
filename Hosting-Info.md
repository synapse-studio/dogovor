## Русскими словами
* <b>Операционная система:</b> любая
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
1. Web-севрер Apache 2.x или Nginx
  - mod_rewrite
  - .htaccess (Apache Virtualhost должна содержать директиву "AllowOverride All" для использования файлов .htaccess в Drupal.)
  - mbstring
  - iconv
  - Больше информации о требованиям к веб-серверу на английском <a href="https://www.drupal.org/requirements/webserver">тут</a>
1. PHP 7+
  - Drupal 8: PHP 7+ or higher
  - Settings:
	- register_globals off
	- safe_mode off
	- session.save_handler user
	- session.cache_limiter nocache
	- error_reporting E_ALL
	- php_memory_limit не менее 100мб
	- The standard PHP extensions (enabled by default) Hash and JSON are required by Drupal 7
	- PDO support (extension=pdo.so and extension=pdo_mysql.so)
	- The PECL version of PDO is not compatible with Drupal 7 and cannot be use
  - Больше информации о требованиям к PHP на английском&nbsp;<a href="https://www.drupal.org/requirements/php">тут</a>
1. MySQL 5.6 or higher with PDO
  - MySQL 5.5.3/MariaDB 5.5.20/Percona Server 5.5.8 or higher with PDO and an InnoDB-compatible primary storage engine
  - PostgreSQL 9.1.2 or higher with PDO,
  - SQLite 3.6.8 or higher
  - Больше информации о требованиях к базе данных на английском&nbsp;<a href="https://www.drupal.org/requirements/database">тут</a>
