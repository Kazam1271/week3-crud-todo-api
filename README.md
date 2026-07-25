# week3-crud-todo-api

Week 3 assignment for **BeTechFied** — Level Up Your Todo API.

Forked from [`skenpo2/week3-crud-todo-api`](https://github.com/skenpo2/week3-crud-todo-api)
and extended with the full set of CRUD routes plus the assignment tasks.

## Endpoints

| Method | Route              | Description                                    |
|--------|--------------------|------------------------------------------------|
| GET    | `/todos`           | Read all todos                                 |
| GET    | `/todos/:id`       | **Single read** by id (404 if not found)       |
| GET    | `/todos/active`    | **Array bonus:** only todos where `!completed` |
| GET    | `/todos/completed` | Only completed todos                           |
| POST   | `/todos`           | Create a todo — **requires `task` field**      |
| PATCH  | `/todos/:id`       | Partial update (e.g. `{ "completed": true }`)  |
| DELETE | `/todos/:id`       | Delete a todo (204 on success)                 |

### Validation
`POST /todos` returns **400** if the `task` field is missing or empty.

## Setup

```bash
npm install
npm run dev   # nodemon, or: npm start
```

Server runs on `http://localhost:3002` (override with `PORT` env var).

## Testing with curl

```bash
# Read all
curl http://localhost:3002/todos

# Single read
curl http://localhost:3002/todos/1

# Active (not completed)
curl http://localhost:3002/todos/active

# Create (valid)
curl -X POST http://localhost:3002/todos \
  -H "Content-Type: application/json" \
  -d '{"task":"Write tests"}'

# Create (missing task -> 400)
curl -X POST http://localhost:3002/todos \
  -H "Content-Type: application/json" \
  -d '{}'

# Update
curl -X PATCH http://localhost:3002/todos/1 \
  -H "Content-Type: application/json" \
  -d '{"completed":true}'

# Delete
curl -X DELETE http://localhost:3002/todos/2
```
