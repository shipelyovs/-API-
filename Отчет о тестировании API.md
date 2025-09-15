# **Отчет о результатах тестирования API**

### *Общая информация:*
Тестируемый функционал: API эндпоинты GET /posts и POST /posts.

### *Цель тестирования:*
Проверка корректности работы API эндпоинтов GET /posts и POST /posts, включая валидацию параметров, обработку ошибок и структуру ответов.

### *Методология тестирования:*
- Тестирование методом черного ящика с фокусом на проверку входных и выходных данных
- Комбинация позитивных и негативных сценариев для всесторонней проверки функционала
- Проверка идемпотентности операций для обеспечения корректной работы API

### *Основные направления тестирования:*
**1. Структурное тестирование**
- Проверка структуры ответов
- Валидация типов данных
- Анализ заголовков ответа
- Проверка кодов состояния HTTP

**2. Функциональное тестирование**
- Проверка основных эндпоинтов (GET/POST)
- Тестирование параметров запросов
- Валидация фильтрации данных
- Проверка пагинации

### *Результаты тестирования:*
Был создан ран из 26 кейсов. В результате проверки пройдено было 7, остальные 19 были провалены. 

### *Обнаруженные дефекты:*
По результатам прохождения рана было оформлено 5 баг-репортов. 3 с Severity "Критичный" и 2 с Severity "Высокий"

### *Рекомендации:*
1. Исправить обработку параметров _limit, _userId и _page 
2. Реализовать корректную обработку идемпотентности для POST запросов

### *Заключение:*
Тестирование выявило критические проблемы с обработкой параметров и идемпотентностью. Рекомендуется провести исправление обнаруженных дефектов перед релизом API в production среду. Общая оценка качества API — удовлетворительная, требуется доработка.

## ВОПРОС: Как получить первые 5 постов пользователя с userId=7? Составить полный URL и описать ожидаемый результат.

## ОТВЕТ: 
1. URL запрос: https://jsonplaceholder.typicode.com/posts?userId=7&_limit=5
2. ER: 	
- код и статус ответа 200 OK
- в боди ответа присутсвует:
```[
    {
        "userId": 7,
        "id": 61,
        "title": "voluptatem doloribus consectetur est ut ducimus",
        "body": "ab nemo optio odio\ndelectus tenetur corporis similique nobis repellendus rerum omnis facilis\nvero blanditiis debitis in nesciunt doloribus dicta dolores\nmagnam minus velit"
    },
    {
        "userId": 7,
        "id": 62,
        "title": "beatae enim quia vel",
        "body": "enim aspernatur illo distinctio quae praesentium\nbeatae alias amet delectus qui voluptate distinctio\nodit sint accusantium autem omnis\nquo molestiae omnis ea eveniet optio"
    },
    {
        "userId": 7,
        "id": 63,
        "title": "voluptas blanditiis repellendus animi ducimus error sapiente et suscipit",
        "body": "enim adipisci aspernatur nemo\nnumquam omnis facere dolorem dolor ex quis temporibus incidunt\nab delectus culpa quo reprehenderit blanditiis asperiores\naccusantium ut quam in voluptatibus voluptas ipsam dicta"
    },
    {
        "userId": 7,
        "id": 64,
        "title": "et fugit quas eum in in aperiam quod",
        "body": "id velit blanditiis\neum ea voluptatem\nmolestiae sint occaecati est eos perspiciatis\nincidunt a error provident eaque aut aut qui"
    },
    {
        "userId": 7,
        "id": 65,
        "title": "consequatur id enim sunt et et",
        "body": "voluptatibus ex esse\nsint explicabo est aliquid cumque adipisci fuga repellat labore\nmolestiae corrupti ex saepe at asperiores et perferendis\nnatus id esse incidunt pariatur"
    }
]```