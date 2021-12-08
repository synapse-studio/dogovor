# Alpha-to-betta-changes.

* Drupal 8.6+ (из-за изменения таксономии)
  - убран костыль, который правит парента 
  - добавлена поддержка статуса термина
  - место изменений `Drupal\cmlmigrations\Plugin\migrate\source\TaxonomyCatalog`
* Сервис получения последнего обмена
  - удлалён `Drupal\cmlapi\Controller\GetCml`
  - удлалён `Drupal\cmlapi\Controller\GetLastCml`
  - теперь `\Drupal::service('cmlapi.getcml')->`
* XML-парсер 
  - теперь сервис
* Используемые бандлы (типы) в соответствии с https://www.drupal.org/project/cmlstarter
  - товар: стало `product` было `default`
  - товар: стало `variation` было `default`
* Добавилось поле `full` - нужно запустить `entity-updates`
