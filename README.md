# Проект з використанням MS SQL Server у Docker

##  Опис
Цей проєкт реалізує базу даних з використанням MS SQL Server, що запускається в контейнері Docker.  
У цьому файлі наведено інструкції щодо створення контейнера, запуску та підключення до бази даних.  

---

##  Структура проекту
project_root/
├── manual/ # Директорія з документацією
├── k8s/ # Директорія з HelmChart
├── VIEW.SQL # SQL файл з представленнями (VIEW)
├── README.MD # Інструкція по запуску контейнера

---

##  Передумови
Для запуску MS SQL Server у контейнері вам знадобиться:
- **Docker Desktop** або Docker Engine встановлений на системі.
- Інтернет-з’єднання для завантаження образу MS SQL Server.  

---

## Запуск MS SQL Server у контейнері

### 1. Створіть Docker Volume для зберігання даних:
```bash
docker volume create mssql-data
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=YourStrong@Passw0rd" -p 1433:1433 \
  --name sqlserver --mount source=mssql-data,target=/var/opt/mssql \
  -d mcr.microsoft.com/mssql/server:2022-latest
docker ps -a
