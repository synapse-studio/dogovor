## Русскими словами
* **Операционная система:** любая
  - мы используем Linux Debian/Ubuntu
* **Веб сервер:** Apache или Nginx или Microsoft IIS - любая современная версия
  - мы используем Nginx
* **Язык: PHP 8+** - современная версия (php 8.3+ на май 2023)
  - Актуальную версию PHP можно увидеть тут: https://www.php.net/supported-versions.php
* **База данных:** MySQL/PostgreSQL/SQLite и множество других
  - MySQL 5.7.8+ для Drupal10 / у нас Mariadb 10.6+
  - SQLite 3.26+ для сайтов визиток / у нас SQLite 3.38+
* **План хостинга:** память 128+мб, место на диске 100+мб
  - оперативная память min 32Mb. Для комфортной работы желательно 500Mb+
  - место на диске 100Mb+. Для комфортной работы 500Mb+
### Итого:
Для работы сайта на друпале подойдёт любой современный хостинг.
## Для технарей

* Web-севрер Apache 2.x или Nginx
  - Nginx - наша конфигурация : https://github.com/politsin/docker-proxy/tree/master/includes
  - Для Apache: mod_rewrite, .htaccess + "AllowOverride All", iconv, mbstring
  - Подробное описание: https://www.drupal.org/docs/system-requirements/web-server-requirements
* PHP 8.0+
  - PHP 8.0+ достаточно для всех версий
  - предыдущие версии PHP нет смысла обсуждать, т.к. они находятся в статусе EOL https://www.php.net/supported-versions.php
  - Необходимые пакеты:  mysql/mysqli with PDO, xml, gd/ImageMagick, OpenSSL, JSON, cURL, Mbstring, Opcache
  - Мы используем также пакеты https://github.com/politsin/docker-php/blob/master/Dockerfile#L15
  - Подробное описание: https://www.drupal.org/docs/system-requirements/php-requirements
  - Конфигурация:
    * register_globals off
    * safe_mode off
    * session.save_handler user
    * session.cache_limiter nocache
    * error_reporting E_ALL
    * php_memory_limit не менее 100мб (у нас 500Mb)
* База данных
  - MySQL 5.7.8+ для Drupal10 / у нас Mariadb 10.6+
  - SQLite 3.26+ для сайтов визиток / у нас SQLite 3.38+
  - у нас Mariadb 10.6+ (~= MySQL 5.7) с такой конфигурацией https://github.com/politsin/docker-starter/blob/master/etc/dev/mysql/my.cnf 
  - Подробное описание https://www.drupal.org/docs/system-requirements/database-server-requirements
* Для комфортной работы программиста
  - ssh/sftp
  - composer & memory 500Mb+
  - drush 12+
  - drupal-console
  - node-js
  - gulp-cli, gulp#4.0 --save-dev, gulp-sass, gulp-watch, gulp-touch, gulp-touch-cmd, gulp-plumber
  - git
  - среда для работы программиста: https://github.com/politsin/docker-php/blob/master/Dockerfile
