
Документация https://smsworldhub.com/ru/info/api
Цена 30 коп за смс

Отправка сообщения

Для отправки SMS необходимо вызвать методом GET адрес:
http://api.smsworldhub.com/v1/send?login={login}&psw={psw}&phone={phone}&mes={mes}

Описание параметров, передаваемых Серверу:
Основные параметры token 	Ваш token из профиля.
phone 	Номер мобильного телефона в международном формате, на которое отправляется сообщение.
mes 	Текст отправляемого сообщения. Максимальный размер – 800 символов. Сообщение при необходимости будет разбито на несколько SMS, отправленных абоненту и оплаченных по отдельности. Размер одного SMS – 160 символов в латинице или 70 символов в кириллице.
Дополнительные параметры gatewayId 	Идентификатор шлюза. Если вы хотите рассылать через свой шлюз укажите id шлюза или all для автоматического выбора одного из вашего шлюза. View
lifeTime 	Срок жизни SMS 1 - 24 ч.
costUsd 	Максимальная цена $ за sms.
costRur 	Максимальная цена руб. за sms.
Мы устанавливаем максимальные цены для каждых стран чтоб предотвратить злоупотребление. Вы можете с ними ознакомиться.

В случае ошибки Сервер возвращает следующую строку :
{"error":"Wrong phone number","status":"ERROR","code":400}

Коды:
200 	Успешный запрос
400 	Ошибка валидации
401 	Мы не можем отправить sms на этот номер, страна не поддерживается или нет активного sms шлюза.
403 	Нет прав

В случае успешного запроса Сервер возвращает ответ в виде строки:
{"status":"OK","code":200,"data":{"id":"10","balance":{"rur":89.8,"usd":100}}}
Проверка статуса сообщения

Для проверки статуса SMS необходимо вызвать методом GET адрес:
http://api.smsworldhub.com/v1/status?token={token}&id={id}

Описание параметров, передаваемых Серверу:
token 	Ваш token из профиля.
id 	Идентификаторы sms сообщений разделенных запятыми

В случае успешного запроса Сервер возвращает ответ в виде строки:
{"status":"OK","code":200,"data":{"items":[{"id":"4","status":"On the queue"}]}}
Проверка баланса

Для проверки баланса необходимо вызвать методом GET адрес:
http://api.smsworldhub.com/v1/balance?token={token}

Описание параметров, передаваемых Серверу:
token 	Ваш token из профиля.

В случае успешного запроса Сервер возвращает ответ в виде строки:
{"status":"OK","code":200,"data":{"rur":90.4,"usd":100}} 
