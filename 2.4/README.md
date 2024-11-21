# Домашнее задание к занятию «Управление доступом»

### Цель задания

В тестовой среде Kubernetes нужно предоставить ограниченный доступ пользователю.

------

### Чеклист готовности к домашнему заданию

1. Установлено k8s-решение, например MicroK8S.
2. Установленный локальный kubectl.
3. Редактор YAML-файлов с подключённым github-репозиторием.

------

### Инструменты / дополнительные материалы, которые пригодятся для выполнения задания

1. [Описание](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) RBAC.
2. [Пользователи и авторизация RBAC в Kubernetes](https://habr.com/ru/company/flant/blog/470503/).
3. [RBAC with Kubernetes in Minikube](https://medium.com/@HoussemDellai/rbac-with-kubernetes-in-minikube-4deed658ea7b).

------

### Задание 1. Создайте конфигурацию для подключения пользователя

1. Создайте и подпишите SSL-сертификат для подключения к кластеру.
2. Настройте конфигурационный файл kubectl для подключения.
3. Создайте роли и все необходимые настройки для пользователя.
4. Предусмотрите права пользователя. Пользователь может просматривать логи подов и их конфигурацию (`kubectl logs pod <pod_id>`, `kubectl describe pod <pod_id>`).
5. Предоставьте манифесты и скриншоты и/или вывод необходимых команд.

---
### Ответ

1. Создал, подпишите SSL-сертификат для подключения к кластеру, настроил конфигурационный файл kubectl для подключения: 

![Screen1](https://github.com/megasts/kuber-homeworks/blob/task_2.4/2.4/img/task2_4_1.png)

2. Переключился на созданный контекст:

![Screen2](https://github.com/megasts/kuber-homeworks/blob/task_2.4/2.4/img/task2_4_2.png)

3. При потытке выполнить команду:

``` bash
$ kubectl get pods
```

ошибок не возникло:

![Screen3](https://github.com/megasts/kuber-homeworks/blob/task_2.4/2.4/img/task2_4_3.png)

Это произошло от того, что на Node не включен RBAC.

4. Включаем RBAC:

![Screen4](https://github.com/megasts/kuber-homeworks/blob/task_2.4/2.4/img/task2_4_4.png)

после этого при выполении команды 

``` bash
$ kubectl get pods
```

получаем ошибку доступа к подам пользователю "megi" (необходимо настроить роли):

![Screen5](https://github.com/megasts/kuber-homeworks/blob/task_2.4/2.4/img/task2_4_5.png)

5. Создаем [role:](https://github.com/megasts/kuber-homeworks/blob/task_2.4/2.4/src/role.yaml)

![Screen6](https://github.com/megasts/kuber-homeworks/blob/task_2.4/2.4/img/task2_4_6.png)

6. Создаем [RoleBinding](https://github.com/megasts/kuber-homeworks/blob/task_2.4/2.4/src/rolebinding.yaml) и переключаемся на контекст пользователя "megi"; после этого видно, что пользователь может просматривать Pods, но не может другие ресурсы:

![Screen7](https://github.com/megasts/kuber-homeworks/blob/task_2.4/2.4/img/task2_4_7.png)

------

### Правила приёма работы

1. Домашняя работа оформляется в своём Git-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl`, скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.

------

