# DO10 — Basic Kubernetes

## Part 1.

### 1. Запуск Kubernetes-окружения
Сделал: запустил локальный кластер Kubernetes с помощью Minikube.


![kubectlt](<screen/Screenshot from 2026-01-20 13-07-07.png>)
---

### 2. Применение примерных манифестов
Сделал: применил манифесты из директории `/src/example` командой `kubectl apply`.

![alt text](<screen/Screenshot from 2026-01-20 13-18-47.png>)

---

### 3. Запуск Kubernetes Dashboard
Сделал: запустил стандартную панель управления Kubernetes с помощью команды `minikube dashboard`.

![alt text](<screen/Screenshot from 2026-01-20 13-21-09.png>)

---

### 4. Проброс портов к сервисам
Сделал: прокинул туннели для доступа к сервисам внутри кластера с помощью `kubectl service`.

![alt text](<screen/Screenshot from 2026-01-20 13-24-57.png>)

---

### 5. Проверка работы приложения
Сделал: проверил доступность веб-приложения через браузер.

![alt text](<screen/Screenshot from 2026-01-20 13-25-49.png>)

---

## Part 2.

### 1. Создание манифестов приложения
Сделал: написал собственные YAML-манифесты для приложения из первого проекта.


### 1.1 ConfigMap
Сделал: создал ConfigMap со значениями хостов и портов базы данных и сервисов.

![alt text](<screen/Screenshot from 2026-01-20 13-37-46.png>)

---

### 1.2 Secret
Сделал: создал Secret с логином и паролем к базе данных и ключами межсервисной авторизации.

![alt text](<screen/Screenshot from 2026-01-20 13-41-36.png>)

---

### 1.3 Deployment и Service
Сделал: создал Deployment и Service для postgres, rabbitmq и 7 сервисов приложения.
Для всех сервисов используется одна реплика.
Приложение запущено последовательным применением манифестов `kubectl apply -f`.

![alt text](<screen/Screenshot from 2026-01-21 12-21-28.png>)

---

### 2. Проверка состояния объектов
Сделал: проверил состояние созданных ресурсов с помощью `kubectl get` и `kubectl describe`.

![kubectl get](screen/2.2.png)
![kubectl describe](screen/2.3.png)
![kubectl get pods](screen/2.4.png)

---

### 3. Проверка значений Secret
Сделал: проверил корректность значений секретов с декодированием из Base64.

![Secret decode](screen/2.5.png)

---

### 4. Проверка логов приложения
Сделал: проверил логи сервисов с помощью команды `kubectl logs`.

![Logs](screen/2.6.png)

---

### 5. Проброс портов к gateway и session
Сделал: прокинул туннели для доступа к `gateway-service` и `session-service`.

![Session port-forward](screen/2.7.png)
![Gateway port-forward](screen/gateway.png)
![alt text](<screen/результаты curl.png>)

---

### 6. Функциональные тесты Postman
Сделал: запустил функциональные тесты Postman / Newman для проверки работы API.

![alt text](<screen/Pasted image.png>)

---

### 7. Kubernetes Dashboard — мониторинг
Сделал: в Kubernetes Dashboard проверил состояние нод, список Pod, загрузку CPU и памяти,
конфигурации, секреты и логи Pod.

![Nodes](screen/2.8.png)
![Pods](screen/2.9.png)
![Metrics](screen/2.9.9.png)
![Configs and Secrets](screen/2.10.png)

---

### 8. Обновление приложения и стратегии развертывания
Сделал: обновил приложение, добавив новую зависимость в `pom.xml`, и пересобрал образы.

#### Recreate
Развертывание с полной остановкой старых Pod.

![Recreate](screen/2.11.png)

#### Rolling Update
Последовательное обновление Pod без остановки сервиса.

![Rolling](screen/2.12.png)
