# idesyatov_platform
idesyatov Platform repository

## [kubernetes-prepare](.github)
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

## [kubernetes-intro](kubernetes-intro)
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

## [kubernetes-controllers](kubernetes-controllers)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ № 3

- [X] Основное ДЗ
- [X] Задание со *

## В процессе сделано:
- Изучены ReplicaSet, Deployment, DaemonSet
- Написаны и протестированы манифесты для работы с данными сущностями

## Как запустить проект:
- Задания для данного занятия описаны отдельными манифестами в директорий **./kubernetes-controllers** для запуска добавить имя манифеста:
```sh
kubectl apply -f ./kubernetes-controllers/[manifest_name.yaml]
```
- Пример запуска и проброса порта:
```sh
kubectl apply -f frontend-deployment.yaml

kubectl port-forward --address 0.0.0.0 deployment/frontend 8080:8080
```

## Как проверить работоспособность:
- Перейти по ссылке http://localhost:8080/

- Перейти по ссылке http://localhost:8080/_healthz

- Перейти по ссылке http://localhost:9100/metrics

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-networks](kubernetes-networks)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ № 4

- [X] Основное ДЗ
- [X] Задание со *

## В процессе сделано:
- добавлены probe к сервису web
- создан новый деплоймент для web
- испробованы разные стратегии обновления подов
- создание сервисов с clusterip, loadbalancer
(установка metallb из задания падает с failing to pull image, нужно менять регистри с docker.io на quay.io)
- сделал доступным coredns через metallb балансер
- запущен ingress-controller
## Как запустить проект:
- kubectl -f apply kubernetes-networks/web-deploy.yaml

## Как проверить работоспособность:
- Например, перейти по ссылке http://localhost:8080

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-volumes](kubernetes-volumes)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ № 5

- [X] Основное ДЗ
- [X] Задание со *

## В процессе сделано:
- создан statefulset
- создан pvc/pv
- создан secret используемый в pod

## Как запустить проект:
- kubectl apply -f ./kubernetes-volumes/

## Как проверить работоспособность:
- kubectl get statefulsets
- kubectl get pods
- kubectl get pvc
- kubectl get pv
- kubectl exec minio-0 env

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-security](kubernetes-security)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ № 6

- [X] Основное ДЗ
- [X] Задание со *

## В процессе сделано:
- написаны манифесты для создания service account
- написали манифесты для создания и назначения ролей RoleBinding / ClusterRole

## Как запустить проект:
- kubectl apply -f ./kubernetes-security/task01/
- kubectl apply -f ./kubernetes-security/task02/
- kubectl apply -f ./kubernetes-security/task03/

## Как проверить работоспособность:
- kubectl get serviceaccounts -n prometheus -o yaml
- kubectl get serviceaccounts -n dev -o yaml
- kubectl get rolebindings -n dev -o yaml


## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-templating](./kubernetes-templating)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ № 7

- [X] Основное ДЗ
- [ ] Задание со *

## В процессе сделано:
- установка helm
- установка из chart
- создание собственных chart

## Как запустить проект:
- ./kubernetes-templating/repo.sh
- kubectl apply -f ./kubernetes-templating/

## Как проверить работоспособность:
- Например, перейти по ссылке 
```bash
https://*.<IP>.nip.io
```

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-operators](./kubernetes-operators)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ № 8

- [X] Основное ДЗ
- [ ] Задание со *

## В процессе сделано:
- Созданы манифесты для crd

## Как запустить проект:
- kubectl apply -f ./kubernetes-operators

## Как проверить работоспособность:
- kubectl get jobs 

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-logging](./kubernetes-logging)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ № 9

- [X] Основное ДЗ
- [ ] Задание со *

## В процессе сделано:
- Созданы манифесты для crd

## Как запустить проект:
- kubectl apply -f ./kubernetes-logging

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-gitops](./kubernetes-gitops)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ № 10

- [X] Основное ДЗ
- [ ] Задание со *

## В процессе сделано:
- Создан кластер черезв в yandex cloud
- Создан проект gitlab.com для gitops практики
- Выполнены основные задания

## Как запустить проект:
- kubectl apply -f ./kubernetes-gitops

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-vault](./kubernetes-vault)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ №

- [X] Основное ДЗ
- [ ] Задание со *

## Как запустить проект:
- kubectl apply -f ./kubernetes-vault

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-monitoring](./kubernetes-monitoring)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ №

- [X] Основное ДЗ
- [ ] Задание со *

## В процессе сделано:
- Созданы манифесты для сервис мониторинга

## Как запустить проект:
- kubectl -f ./kubernetes-monitoring

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-storage](./kubernetes-storage)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ №

- [X] Основное ДЗ
- [ ] Задание со *

## В процессе сделано:
- Созданы манифесты для csi

## Как запустить проект:
- kubectl -f ./kubernetes-monitoring

## PR checklist:
- [X] Выставлен label с темой домашнего задания

</details>

## [kubernetes-next-lesson](./)
<details>
<summary>Подробнее ...</summary>

# Выполнено ДЗ №

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