```markdown```
# Асинхронный скрипт для извлечения и хранения данных из API

Этот скрипт используется для извлечения данных из API и сохранения их в базе данных SQLite. Он использует асинхронные методы для обработки запросов и сохранения данных, что позволяет эффективно использовать ресурсы и обрабатывать большое количество данных параллельно.

## Установка зависимостей

Для работы скрипта требуется установить следующие зависимости:

- `aiohttp`: для работы с HTTP запросами асинхронно
- `aiosqlite`: для работы с базой данных SQLite асинхронно

Установите зависимости с помощью следующей команды:

```
pip install aiohttp aiosqlite
```
или

```commandline
pip install -r requirements.txt
```

## Использование

Для запуска скрипта используйте команду:

```
python main.py --db <имя_файла_базы_данных> --request-limit <максимальное_ограничение_на_запросы>
```

### Аргументы командной строки

- `--db`: Имя файла базы данных SQLite, по умолчанию `product.db`
- `-rl`, `--request-limit`: Максимальное количество одновременных запросов, по умолчанию `10`


##### Примеры:

1. Запуск с использованием базы данных `mydatabase.db` и ограничением в 5 параллельных запросов:

```commandline
python main.py --db mydatabase.db -rl 5
```

2. Запуск с использованием базы данных `custom.db` и ограничением в 8 параллельных запросов:

```commandline
python main.py --db custom.db --request-limit 8
```
##### Рекомендуемые параметры:

```commandline
python main.py --db product.db -rl 10
```

## Структура базы данных

Скрипт создает следующую структуру таблиц в базе данных:

- `categories`: категории товаров
- `subcategories`: подкатегории товаров, связанные с категориями
- `products`: продукты, связанные с подкатегориями
- `offers`: предложения продуктов
- `shops`: магазины, где доступен товар
- `offer_shop_amount`: информация о количестве товара в магазинах

Каждая таблица имеет свою структуру и связи между ними для хранения данных.

![img.png](img.png)