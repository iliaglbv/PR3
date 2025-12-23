# 1 Проверка состояния сервера
    curl -i http://localhost:8080/health
# 2 Получить список задач
    curl -i http://localhost:8080/tasks
# 3 Создать задачу
    curl -i -X POST http://localhost:8080/tasks
    -H "Content-Type: application/json"
    -d '{"title":"buy milk"}'
# 4 Фильтр задач по ключевому слову
    curl -i "http://localhost:8080/tasks?q=milk"
# 5 Получить задачу по ID (например, ID=1)
    curl -i http://localhost:8080/tasks/1
# 6 Ошибки (проверка обработки) неыерный id
    curl -ihttp://localhost:8080/tasks/9999
