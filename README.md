# BakeCakeBot

Этот проект представляет собой телеграм-бота для оформления заказов тортов. Бот позволяет пользователю выбрать параметры торта (форма, уровни, топпинг, ягоды, декор), добавить комментарий и подтвердить заказ. Администраторы получают уведомления о новых заказах.
## Технологии
 - Python 3.x
 - Django для работы с базой данных.
 - aiogram для взаимодействия с Telegram API.
 - SQLite3 для хранения данных.



## Функции
  - Выбор формы, уровней, топпинга, ягод и декора для торта.
  - Ввод текста на торт.
  - Уведомление пользователей о подтверждении заказа.
  - Уведомления администраторов о новых заказах.
  - Хранение данных в базе данных.


## Установка
 1. Клонируем репозиторий `https://github.com/AnnaKuryletz/BakeCakeBot.git`
 2. Создайте и активируйте виртуальное окружение:
    ```
    python3 -m venv venv
    source venv/bin/activate  # Для Linux/MacOS
    venv\Scripts\activate     # Для Windows
    ```
 3. Установка зависимостей: `pip install -r requirements.txt`
 4. Настройте Telegram бота:
   - Получите токен для вашего бота в `BotFather`.
   - Убедитесь, что бот имеет права администратора в нужной группе, если вы хотите отправлять уведомления администратору.
 5. Настройте базу данных:
   - Примените миграции для базы данных: `python manage.py migrate`

## Запуск

Для запуска блога у вас уже должен быть установлен Python 3.
- Запустите сервер командой `python manage.py runserver`

После этого переходите по ссылке [127.0.0.1:8000](http://127.0.0.1:8000/admin), вы увидите страницу администратора.

## Конфигурации
1. Переменные окружения: В проекте используются следующие переменные:

  - `TELEGRAM_BOT_TOKEN`: Токен для вашего Telegram-бота.
  - `ADMIN_CHAT_ID`: ID группы или канала, куда будут отправляться уведомления об оформленных заказах.

2. Модели данных:

  - `CustomCake`: Модель для кастомных тортов.
  - `StandardCake`: Модель для стандартных тортов.
  - `CakeOrder`: Модель для заказа торта (содержит информацию о выбранном торте, адресе доставки, комментариях).
3. Состояния: В проекте используется конечный автомат для отслеживания состояний пользователя:

  - `DeliveryState.waiting_for_address`: Ожидание ввода адреса доставки.
  - `DeliveryState.waiting_for_comment`: Ожидание ввода комментария или пожеланий.
  - `OrderCake.confirming`: Подтверждение заказа и его сохранение.


## Как использовать
 - Запуск бота: После настройки и запуска сервера, ваш бот будет доступен для общения с пользователями в Telegram.

 - Процесс заказа:
    * Пользователь вводит необходимые данные для заказа: форму, уровни, топпинг и другие параметры.
    * Бот отправляет пользователю подробное сообщение с выбором и запросом на подтверждение.
    * После подтверждения, бот сохраняет заказ в базе данных и уведомляет администраторов.
 - Уведомления администраторов: После оформления заказа администраторы получают уведомления о новом заказе с деталями, включая адрес доставки и пожелания клиента.