# БОТ "Fortune cookie"
Телеграм бот. Запустить по ссылке -> https://t.me/YourFortuneCookieBot

### Основной функционал:
Основной функционал бота заключается в выдаче предсказания при отправке боту пользователем определенного текста.

Предсказания хранятся в mongodb и накладываются на шаблонное изображения распределяясь по изображению с учетом длины текста ./bot/workers/AddTextOnImage.js . Далее пользователь получает предсказание с инлайн кнопками.

### Дополнительный функционал:
- "лайки и дизлайки" предсказаний (каждому предсказанию можно установить поставить оценку)
- "поделиться" предсказанием (отправить шаблонное сообщение другому пользователю)
- "узнать баланс" - выводит пользователю его баланс по печенькам и лотерейным билетам
- "лотерейный билет" - раз в неделю пользователь получает 1 лотерейный билет где может выиграть N количество печенек

### Автономный функционал
Один из самых интересно и скрытых

- "Рассыльщик" - класс, который проверяет необходимо ли отправить сообщение пользователю и отправляет его
    * Рассылка автоматических регулярных сообщений:
        1) При начислении бесплатной печеньки и лотерейного билет
        2) При отсутствии пользователя несколько дней
    * Рассылка запланированных сообщений. Для использования необходимо:
        1) 
           ```   
            {
                "text": String, // текст сообщения
                "buttons": {
                    "buttonType": String, // тип кнопок
                    "collectionName": String // наименование коллекции с кнопкаит
                },
                "addressee": Object, // фильтр адресатов
                "delivery_date": Number, // Дата рассыдки в секундах
                "status": Bool // статус рассылки
            } 
         ```
        2. Рассыльщик автоматически проверяет статус и время отправки
- Сервер для дополнительных нужд. Так же параллельно с ботом запускается сервер. Функционал:
    * Главное для чего он сейчас используется это для аналитики. Аналитика выгружается в гугл таблицу https://docs.google.com/spreadsheets/d/1lXexvEOgfF-6DOpAhCjYDET30dTzmhxVDA4KXg20JWE/edit#gid=771004730. 
    Чтобы обновить таблицу: Меню скриптов -> Обновить
    * Так же использую для создания различных хелперов
    
