# Диаграммы

## Диаграмма последовательности
```mermaid
sequenceDiagram
    actor User as Пользователь
    participant App as Приложение
    participant DB as База данных
    participant Model as ML-модель рекомендаций

    User->>App: Открыть раздел рекомендаций
    App->>DB: Запросить предпочтения пользователя
    DB-->>App: Вернуть выбранные жанры
    App->>Model: Передать предпочтения
    Model->>DB: Запросить данные о фильмах
    DB-->>Model: Вернуть список фильмов
    Model->>Model: Рассчитать рекомендации
    Model-->>App: Вернуть подборку фильмов
    App-->>User: Показать рекомендации
    User->>App: Выбрать фильм
    App-->>User: Показать описание и рейтинг
```
## Диаграмма классов
```mermaid
classDiagram
    class User {
        +int id
        +string name
    }

    class Movie {
        +int id
        +string title
        +string genre
        +float rating
    }

    class UserPreference {
        +int id
        +string preferredGenres
    }

    class Recommendation {
        +int id
        +int userId
        +int movieId
        +float score
    }

    User "1" --> "1" UserPreference : has
    User "1" --> "*" Recommendation : receives
    Movie "1" --> "*" Recommendation : recommended in
```
- User — хранит информацию о пользователе системы.
- Movie — содержит данные о фильме: название, жанр и рейтинг.
- UserPreference — хранит предпочтения пользователя по жанрам.
- Recommendation — связывает пользователя с рекомендованным фильмом и содержит оценку его соответствия предпочтениям.