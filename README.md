# **taski-docker**

![githab](https://raw.githubusercontent.com/Zolibot/Interview_of_a_real_fighter/main/fat-cat-laser-eyes.gif)


![](https://img.shields.io/badge/license-MIT-green)
![](https://img.shields.io/badge/Powered%20by-Python3.9-green)

---

## **Оглавление**

- [**taski-docker**](#taski-docker)
  - [**Оглавление**](#оглавление)
    - [**Описание**](#описание)
    - [**Технологии:**](#технологии)
    - [**Запуск проекта через Docker compose**](#запуск-проекта-через-docker-compose)
      - [**Настройка файла окружения .env**](#настройка-файла-окружения-env)
      - [***Установка  Docker***](#установка--docker)
      - [**Запуск**](#запуск)
    - [**Настройка CI/CD используя GitHab Action**](#настройка-cicd-используя-githab-action)
  - [**Авторы**](#авторы)

---

### **Описание**

Данный проект представляет собой сервис для составления списка задач, который позволяет пользователям создавать новые задачи и отмечать их выполненными после завершения. Backend часть проекта разработана на Django, а frontend часть на React.

Для удобства развертывания и запуска проекта используется Docker Compose. Это позволяет быстро и легко установить все необходимые зависимости и запустить приложение на любой операционной системе.

В списке задач отображается название задачи, ее описание, дата создания и статус выполнения. Пользователь может добавлять новые задачи, редактировать существующие и отмечать их как выполненные.

В целом, проект представляет собой удобный инструмент для организации личных задач и контроля их выполнения. Он может быть использован как для личных нужд, так и для командной работы в рамках проектов.

### **Технологии:**

- ![](https://img.shields.io/badge/Python-3.9-brightgreen)
- ![](https://img.shields.io/badge/Django-3.2-brightgreen)
- ![](https://img.shields.io/badge/Nginx-1.18.0-brightgreen)
- ![](https://img.shields.io/badge/NodeJs-v18.16.0-brightgreen)
- ![](https://img.shields.io/badge/Gunicorn-20.1.0-brightgreen)
- ![](https://img.shields.io/badge/Docker-24.0.2-brightgreen)

---

### **Запуск проекта через Docker compose**

- клонировать репозиторий или скачать архив

```bash
git clone git@github.com:Zolibot/taski-docker.git
```
---

#### **Настройка файла окружения .env**

- В корневом каталоге создать файл **.env**

```bash
touch .env
```
- Добавить переменные среды для базы данных и backend

```bash
# Файл .env
POSTGRES_USER=django_user
POSTGRES_PASSWORD=mysecretpassword
POSTGRES_DB=django
# Добавляем переменные для Django-проекта:
DB_HOST=db
DB_PORT=5432
```

---

####  ***[Установка  Docker](https://docs.docker.com/desktop/uninstall/)***

---

 **Установка  Docker на Linux**

- В терминале вести команды

```bash
sudo apt update
sudo apt install curl
curl -fSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo apt-get install docker-compose-plugin
```

- Проверка установки Docker

```bash
sudo docker -v
```

- Вывод

```bash
Docker version 23.0.1, build e92dd87
```

- Проверка установки Docker Compose

```bash
sudo docker compose version
```
- Вывод

```bash
Docker Compose version 2.16.0
```

---

#### **Запуск**

- На локальном сервере

```bash
sudo docker compose -f docker-compose.yml up
```

- На удаленном сервере в режиме демона

```bash
sudo docker compose -f docker-compose.production.yml up -d
```

---

### **Настройка CI/CD используя GitHab Action**

- Для корректной работы GitHub Actions необходимо задать переменные для работы с контейнерами, удаленным сервером и телеграм-ботом.

**Список переменных:**

```bash
# доступ к DockerHab обновления образов
DOCKER_USERNAME=yous_dockerhab_login
DOCKER_PASSWORD=yous_dockerhab_password
# настройки базы данных
POSTGRES_DB=django
POSTGRES_PASSWORD=django_password
POSTGRES_USER=django
DB_HOST=db
DB_PORT=5432
# ip адрес удаленной машины
HOST=xxx.xxx.xxx.xxx
# доступ к удаленному серверу
# закрытый ключ ssh
SSH_KEY=-----BEGIN OPENSSH PRIVATE KEY-----xxxx-----END OPENSSH PRIVATE KEY-----
# фраза для закрытого ключа
SSH_PASSPHRASE=passphrase
# отправка сообщения об успешной сборки
# id кому отправить
TELEGRAM_TO=128xxxxxxx
# токен Telegram бота
TELEGRAM_TOKEN=123456:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

- В случае успешного выполнения программы, Telegram-бот отправит сообщение об успешной сборке и развертывании на удаленном сервере, а также обновятся образы на DockerHub.

---

## **Авторы**

*[Александр Андреевич](https://github.com/Zolibot)*

![GitHub followers](https://img.shields.io/github/followers/Zolibot?style=social)