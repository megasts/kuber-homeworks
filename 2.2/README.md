# Домашнее задание к занятию «Хранение в K8s. Часть 2»

### Цель задания

В тестовой среде Kubernetes нужно создать PV и продемострировать запись и хранение файлов.

------

### Чеклист готовности к домашнему заданию

1. Установленное K8s-решение (например, MicroK8S).
2. Установленный локальный kubectl.
3. Редактор YAML-файлов с подключенным GitHub-репозиторием.

------

### Дополнительные материалы для выполнения задания

1. [Инструкция по установке NFS в MicroK8S](https://microk8s.io/docs/nfs). 
2. [Описание Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/). 
3. [Описание динамического провижининга](https://kubernetes.io/docs/concepts/storage/dynamic-provisioning/). 
4. [Описание Multitool](https://github.com/wbitt/Network-MultiTool).

------

### Задание 1

**Что нужно сделать**

Создать Deployment приложения, использующего локальный PV, созданный вручную.

1. Создать Deployment приложения, состоящего из контейнеров busybox и multitool.
2. Создать PV и PVC для подключения папки на локальной ноде, которая будет использована в поде.
3. Продемонстрировать, что multitool может читать файл, в который busybox пишет каждые пять секунд в общей директории. 
4. Удалить Deployment и PVC. Продемонстрировать, что после этого произошло с PV. Пояснить, почему.
5. Продемонстрировать, что файл сохранился на локальном диске ноды. Удалить PV.  Продемонстрировать что произошло с файлом после удаления PV. Пояснить, почему.
5. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

---

### Ответ

1. Ссылки на манифесты:

[Deployment](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/src/Deployment.yaml)

[PVC](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/src/PVC.yaml)

[PV](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/src/PV.yaml)

2. Скриншот, демонстрирующий, что multitool может читать файл, в который busybox пишет каждые пять секунд в общей директории: 

![Screen1](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/img/task2_2_1.png)

3. Скриншот после удаления Deployment и PVC:

![Screen2](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/img/task2_2_2.png)

Статус PV сменился с Bound на Released. PV свободен и может быть использован в дальнейшем.

4. Скриншот, демонстрирующий, что файл сохранился на локальном диске ноды:

![Screen3](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/img/task2_2_3.png)

5. Скриншот, демонстрирующий, что после удаления PV файл сохранился:

![Screen4](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/img/task2_2_4.png)

Файл после удаления PV файл сохранился потому, что при создании PV была применена настройка ReclaimPolicy=Retain (после удаления PV ресурсы из внешних провайдеров автоматически не удаляются).

------

### Задание 2

**Что нужно сделать**

Создать Deployment приложения, которое может хранить файлы на NFS с динамическим созданием PV.

1. Включить и настроить NFS-сервер на MicroK8S.
2. Создать Deployment приложения состоящего из multitool, и подключить к нему PV, созданный автоматически на сервере NFS.
3. Продемонстрировать возможность чтения и записи файла изнутри пода. 
4. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

---

### Ответ

1. Ссылки на манифест для создания PODa и PVC: [Deployment_nfs](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/src/Deployment_nfs.yaml)

2. Скриншот подключения NFS-сервер на MicroK8S:

![Screen5](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/img/task2_2_5.png)

3. Скриншот, демонстрирующий возможность чтения и записи файла изнутри пода:

![Screen6](https://github.com/megasts/kuber-homeworks/blob/task_2.2/2.2/img/task2_2_6.png)

------

### Правила приёма работы

1. Домашняя работа оформляется в своём Git-репозитории в файле README.md. Выполненное задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl`, а также скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.
