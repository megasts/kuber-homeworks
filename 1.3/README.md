# Домашнее задание к занятию «Запуск приложений в K8S»

### Цель задания

В тестовой среде для работы с Kubernetes, установленной в предыдущем ДЗ, необходимо развернуть Deployment с приложением, состоящим из нескольких контейнеров, и масштабировать его.

------

### Чеклист готовности к домашнему заданию

1. Установленное k8s-решение (например, MicroK8S).
2. Установленный локальный kubectl.
3. Редактор YAML-файлов с подключённым git-репозиторием.

------

### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

1. [Описание](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) Deployment и примеры манифестов.
2. [Описание](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/) Init-контейнеров.
3. [Описание](https://github.com/wbitt/Network-MultiTool) Multitool.

------

### Задание 1. Создать Deployment и обеспечить доступ к репликам приложения из другого Pod

1. Создать Deployment приложения, состоящего из двух контейнеров — nginx и multitool. Решить возникшую ошибку.
2. После запуска увеличить количество реплик работающего приложения до 2.
3. Продемонстрировать количество подов до и после масштабирования.
4. Создать Service, который обеспечит доступ до реплик приложений из п.1.
5. Создать отдельный Pod с приложением multitool и убедиться с помощью `curl`, что из пода есть доступ до приложений из п.1.

---
### Ответ

1. Ссылка на Deployment: [приложение, состоящего из двух контейнеров — nginx и multitool](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/src/deployment_1_replic.yaml)

2. Ссылка на Deployment с двумя репликами: [приложение, состоящего из двух контейнеров — nginx и multitool](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/src/deployment_2_replic.yaml)

3.  - Скриншот количество подов до масштабирования: ![Скриншот1](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/IMG/task1_3_1.png)

    - Скриншот количество подов после масштабирования: ![Скриншот2](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/IMG/task1_3_2.png)

4. Ссылка на Service: [доступ до реплик приложений из п.1](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/src/netology-svc.yaml)

5.  - Ссылка на Pod: [отдельный Pod с приложением multitool](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/src/pod_multitool.yaml)

    - Скриншот подтверждения наличия доступа из пода до приложений из п.1 ![Скриншот3](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/IMG/task1_3_3.png)

---

### Задание 2. Создать Deployment и обеспечить старт основного контейнера при выполнении условий

1. Создать Deployment приложения nginx и обеспечить старт контейнера только после того, как будет запущен сервис этого приложения.
2. Убедиться, что nginx не стартует. В качестве Init-контейнера взять busybox.
3. Создать и запустить Service. Убедиться, что Init запустился.
4. Продемонстрировать состояние пода до и после запуска сервиса.

---
### Ответ

 - Ссылка на Deployment: [приложениe nginx с Init-контейнером](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/src/deployment_nginx.yaml)

 - Ссылка на Service: [svc-nginx](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/src/deployment_nginx.yaml)

 - Скриншоты, подтверждающие, что контейнер nginx стартует только после запуска Service c наименованием svc-nginx:
 
  ![Скриншот4](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/IMG/task1_3_4.png)

  ![Скриншот5](https://github.com/megasts/kuber-homeworks/blob/Task_1.3/1.3/IMG/task1_3_5.png)
---

### Правила приема работы

1. Домашняя работа оформляется в своем Git-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl` и скриншоты результатов.
3. Репозиторий должен содержать файлы манифестов и ссылки на них в файле README.md.

------
