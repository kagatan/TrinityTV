# Класс для взаимодействия с сервисом TrinityTV через API

Ссылка на сервис: https://trinity-tv.net/

## Подготовка
 
У менеджера необходимо получить:
  - PARTNER ID
  - SALT
  - Список тарифов с их ID
    
## Использование:


```php
<?php 

require dirname(__FILE__).'/TrinityTvApi.php';

$partnerID = '';
$salt = '';

// Данные для примера
$localid = 1234;  // Идентификатор пользователя в системе партнера
$subscrid = 1448; // Идентификатор тарифного плана (выдается менеджером)


$api = new TrinityTvApi($partnerID, $salt);

// Создание пользователя и подключение услуги (подписки)
$res = $api->createUser($localid, $subscrid);

// Изменение Данных пользователя.
$res = $api->updateUser($localid, 'Surname','First name','Second name','Address');

// Получение списка всех пользователей и их статусов.
$res = $api->listUsers();

// Получение списка авторизованных MAC/UUID устройств
$res = $api->listDevices($localid);

// Получение списка подписок пользователя.
$res = $api->subscriptionInfo($localid);

// Приостановление и восстановление услуги (подписки).
//      suspend - отключение подписки
//      resume - продолжение отключенной подписки
$res = $api->subscription($localid, 'suspend');

// Авторизация MAC/UUID устройства
$res = $api->addMacDevice($localid, 'AA-00-BB-AA-FF-11-22');

//Авторизация MAC/UUID устройства по коду
$res = $api->addCodeMacDevice($localid, '9999');

// Деавторизация  MAC/UUID устройства
$res = $api->deleteMacDevice($localid, 'AA-00-BB-AA-FF-11-22');


```


