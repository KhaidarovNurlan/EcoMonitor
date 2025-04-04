# EcoMonitor

## 💾 pgAdmin

Чтобы настроить базу данных PostgreSQL, создайте базу данных eco_monitor, создайте таблицы:

```sql
CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE devices (
    device_id SERIAL PRIMARY KEY,
    device_fingerprint VARCHAR(255) NOT NULL,
    last_user_id INTEGER REFERENCES users(user_id),
    last_login TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE(device_fingerprint)
);

CREATE TABLE measurements (
    measurement_id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(user_id),
    city_name VARCHAR(100) NOT NULL,
    aqi INTEGER NOT NULL,
    temperature DECIMAL(5,2) NOT NULL,
    humidity INTEGER NOT NULL,
    pm25 DECIMAL(5,2) NOT NULL,
    pm10 DECIMAL(5,2) NOT NULL,
    measured_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## 📚 VS Code

- Создайте папку my-node-proj;
- Выполните следующие команды:

```bash
npm init -y
npm i express express-validator cors jsonwebtoken dotenv bcryptjs cookie-parser pg
npx create-react-app my-frontend
cd my-frontend
npm i react-router-dom axios bootstrap fingerprintjs2 lucide-react
```

- В папке my-frontend удалите public и src и закиньте файлы из моего my-frontend, остальные мои файлы загрузите просто в my-node-proj.

## Запуск

```bash
node server.js
cd my-frontend
npm start
```
