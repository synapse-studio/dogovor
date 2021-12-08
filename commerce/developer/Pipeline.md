# Процесс (Pipeline) обмена.

### В этом документе описаны 2 TODO:
* `$this->query('progress')` - такое ощущение что в этом месте могли что-то забыть
* `new` + `Importing` - значит какая-то предыдущая миграция повисла в статусе `Importing`, наверно стоит в таком случае запускать drush mrs для повисшей миграции?

### Pipeline
* За обмен файлами отвечает cmlexchange, 1С приходит на один из адресов:
  - /cmlexchange - инкрементальная выгрузка
  - /cmlexchange/full - полная выгрузка 
* Открытие роута запускает `\Drupal::service('cmlexchange.protocol')->init();`
  - Проверяется авторизация
  - Передаются файлы
  - Запускается `import_pipeline`
* `import_pipeline` проверяет необходимость unZip `\Drupal::service('cmlexchange.import_pipeline')->process();`
  - проверяем необходимость unZip
  - проверяем наличие модуля `cmlmigrations` и конфиг-галочки `cmlexchange.settings.cmlmigrations`
  - запускаем `mlmigrations.pipeline`
  - или завершаем процесс если не требуется импорт данных: отвечаем `success` и ставим `success`-статус у `$cml`
* `mlmigrations.pipeline` отвечает за миграции `\Drupal::service('mlmigrations.pipeline')->init();`
  - проверяем наличие незавершённых предыдущий миграций (со статусом `progress`) и делаем их текущими.
  - ***TODO:*** (такое ощущение что в этом месте  `$this->query('progress')` могли что-то забыть)
  - сохраняем текущий cml-id в `cmlmigrations.settings.runing_cml`
  - получаем информацию о миграциях `$migrations` ($migrations[list] список, $migrations[status] - все миграции в Idle?)
  - переходим в $this->import($cml, $migrations)
* Переключатель статусов:
  - Статус `new`
    - миграции `Idle`? = Ставим статус `progress` и запускаем 
    - миграции `Importing` ?
       - 1C слишком быстра пришла за ответом? отвечеам `progress`
       - 1С пришла вовремя - ставим статус 'busy' и завершаем миграцию с ошибкой *значит какая-то предыдущая миграция повисла в статусе Importing*, ***TODO:*** - наверно стоит в таком случае запускать drush mrs для повисшей миграции?
  - Статус `progress`
      - миграции `Idle`? = Значит миграции уже завершились, ставим `success`
      - миграции `Importing` ? `$timeout_min = 60 * $config->get('cmlmigrations.settings.timeout');`
        - Таймаут ОК: отвечаем `progress`
        - Таймаут прошёл: миграции работают слишком долго, ставим статус `failure` 
  - Статус `какой-то другой` - так не должно быть, ставим `failure`
