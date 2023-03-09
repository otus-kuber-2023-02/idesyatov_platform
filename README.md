# idesyatov_platform
idesyatov Platform repository

# kubernetes-prepare
<details>
<summary>Подробнее ...</summary>

## Выполнено ДЗ № 1

* Организована структура

```sh
.github
├── PULL_REQUEST_TEMPLATE.md
├── auto_assign.yml
├── labeler.yml
└── workflows
 ├── auto-assign.yml
 ├── labeler.yml
 └── run-tests.yml
```
* Настройка локального окружения:
    + установка minikube
    + подключение k9s-cli
</details>

# kubernetes-intro
<details>
<summary>Подробнее ...</summary>

## Выполнено ДЗ № 2

 - [X] Основное ДЗ
 - [X] Задание со *

## В процессе сделано:

- Создан Dockerfile для nginx, который показывает статические файлы из директорий /app внутри контейнера
- Создан web-pod.yaml манифест для образа подготовленного в предыдущем пункте с дополнительным контейнером инициализации
- Создан frontend-pod.yaml который при запуске падает с логом что не найдены переменные окружения для приложения
- Создан frontend-pod-healthy.yaml манифест, который запускает frontend образ. В манифесте установлены значения переменных окружения (деректива env)

## Как запустить проект:

- Скачиваем репозиторий выполнив команду
```sh
mkdir -p ~/Dev/otus-kuber-2023-02/ && cd $_ && \
git clone git@github.com:otus-kuber-2023-02/idesyatov_platform.git && \
git checkout -b kubernetes-intro
```

- Запускаем pod выполнив команду
```sh
kubectl apply -f ./kubernetes-intro/web-pod.yaml
```

- Запускаем pod Выполнив команду
```sh
kubectl apply -f ./kubernetes-intro/frontend-pod-healthy.yaml
```

## Как проверить работоспособность:

### проверка web-pod.yaml
- Проверить что нужный pod web запустился
```sh
kubectl get pod web
```

- Выполнить проброс порта
```sh
kubectl port-forward --address 0.0.0.0 pod/web 8000:8000
```

- Перейти по ссылке http://localhost:8000/index.html

### проверка frontend-pod-healthy.yaml
- Проверить что нужный pod web запустился
```sh
kubectl get pod frontend
```
- Выполнить проброс порта
```sh
kubectl port-forward --address 0.0.0.0 pod/frontend 8080:8080
```

- Перейти по ссылке http://localhost:8080

## PR checklist:
- [X] Выставлен label с темой домашнего задания
</details>

# kubernetes-next
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ № 3

- [ ] Основное ДЗ
- [ ] Задание со *

## В процессе сделано:
- Пункт 1
- Пункт 2

## Как запустить проект:
- Например, запустить команду X в директории Y

## Как проверить работоспособность:
- Например, перейти по ссылке http://localhost:8080

## PR checklist:
- [ ] Выставлен label с темой домашнего задания

</details>