# Практическая работа 3
Голубев Илья ЭФМО-02-25
# Описание проекта
Простой HTTP-сервер для управления задачами To-Do list
Цели:	
- Освоить базовую работу со стандартной библиотекой net/http без сторонних фреймворков.
- Научиться поднимать HTTP-сервер, настраивать маршрутизацию через http.ServeMux.
- Научиться обрабатывать параметры запроса (query, path), тело запроса (JSON/form-data) и формировать корректные ответы (код статуса, заголовки, JSON).
- Научиться базовому логированию запросов и обработке ошибок.

# Требования
Go версии 1.21 и выше
# Установка и запуск
Клонировать репозиторий:
```
git clone https://github.com/iliaglbv/PR3
cd PR3
```
Команда запуска сервера:
```
go run ./cmd/server
```
# Структура проекта
```plaintext
PR3/                     
├── cmd/                  
│   └── server/             
│       └── main.go       
├── internal/              
│   └── api/               
│   │   └── handlers.go     
│   │   └── middleware.go
│   │   └── responses.go
│   └── storage/
│       └── memory.go       
├── go.mod                
└── requests.md 
```
# Основные эндпоинты
Прлверка состояния сервера

    curl http://localhost:8080/health
<img width="490" height="157" alt="healthnew_1" src="https://github.com/user-attachments/assets/762f7406-1c96-4ad4-a067-a4ce29b96285" />

Создать задачу (title":"ваша задача")

    curl -Method POST http://localhost:8080/tasks `
    -Headers @{"Content-Type"="application/json"} `
    -Body '{"title":"buy milk"}'
<img width="813" height="331" alt="task201_1" src="https://github.com/user-attachments/assets/24dee3d0-ee0f-4ba5-a5da-a6e5b5680839" />

Список задач

    curl http://localhost:8080/tasks
<img width="768" height="189" alt="tasks_1" src="https://github.com/user-attachments/assets/18d28a84-bafe-4584-ae1f-52933809d651" />

Список задач с фильтром

    curl "http://localhost:8080/tasks?q=milk"
<img width="463" height="186" alt="taskq_1" src="https://github.com/user-attachments/assets/5cba5d41-1239-4d34-b9e7-35d9451f048e" />

Получить задачу по ID

    curl http://localhost:8080/tasks/1
<img width="429" height="191" alt="taskid1" src="https://github.com/user-attachments/assets/111dd5f7-aead-4f3c-8891-1d1ad05be7dd" />

