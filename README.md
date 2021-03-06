# CheckScan iOS
Описание тестового задания на должность iOS разработчика в CheckScan

### Техническое задание:

Необходимо реализовать приложение с корневыми экранами ЧекСкана
* Скетч файл: https://github.com/MatveyMalatsion/checkscantest/blob/master/CheckScan.sketch
* Спецификация API: http://212.47.248.32:8080/api/v2.1/swagger-ui.html


##### БАЗОВЫЕ ТРЕБОВАНИЯ
_______________________________________
- Главный экран содержит две вкладки : Лента чеков и Поиск
- Все сетевые запросы можно найти в прикрепленном swagger
- В NavigationBar кнопка, по нажатию на которую появляется стандартный UIAlertController с вариантами
    -  Если пользователь авторизован, то опция «Выйти» и «Отмена»
    -  Иначе - «Войти» и «Отмена».
###### Авторизация и сессии
- В Чек Скан есть два вида учетных записей - анонимная и авторизованная. При старте приложения необходимо понимать, залогинен ли пользователь в сервис и если да - анонимной учеткой или авторизованной. Механизм сессий реализован через Куки. Без валидной Куки сетевые запросы будут падать с кодом 401
- Если кука «умерла», то необходимо предлагать пользователю выбор - залогиниться заново либо начать пользоваться чек сканом анонимно. 
- При нажатие на опцию войти появляется UIAlertController с двумя текстовыми полями для логина, пароля и кнопки отправить.

###### Лента чеков:
- Лента чеков отображает чеки пользователя. Чеки грузятся не все сразу, а по 50. Когда доходим до конца ленты - грузим еще чеки - пока они есть. Нужно понимать, есть ли они
- Чеки размещать в отдельных секциях по месяцам в порядке от последнего до первого
- Сохранять чеки в CoreData и показывать чеки из кеша в случае, если на устройстве нет интернета
###### Экран поиска
- На экране поиска есть поле для ввода запроса. 
- Лента так же грузит элементы постранично - по 50 элементов за раз
- Если в поле поиска ничего не написано - отображать ближайшие от текущей геопозиции места - если геопозиция отключена, то отображать вместо ленты UIButton «Разрешите геолокацию» которая ведет в Настройки геолокации iOS
- Если в поле поиска что-то введено - показывать результаты запроса.

##### ADVANCED (берем без вопросов)
_________________________________________
Реализовать на выбор:

- Поддержка iPad - лента чеков не один в ряд, а в несколько (2,3,4) в зависимости от параметров экрана. Реализовать обработку поворота экрана
- Скопировать функционал Статистика из Android версии
- Cкопировать функционал сканирования и добавления чека по QR коду из Android версии (использовать GoogleMaps API)
