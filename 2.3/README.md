# Домашнее задание к занятию «Конфигурация приложений» - Шульгатый Станислав

### Цель задания

В тестовой среде Kubernetes необходимо создать конфигурацию и продемонстрировать работу приложения.

------

### Чеклист готовности к домашнему заданию

1. Установленное K8s-решение (например, MicroK8s).
2. Установленный локальный kubectl.
3. Редактор YAML-файлов с подключённым GitHub-репозиторием.

------

### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

1. [Описание](https://kubernetes.io/docs/concepts/configuration/secret/) Secret.
2. [Описание](https://kubernetes.io/docs/concepts/configuration/configmap/) ConfigMap.
3. [Описание](https://github.com/wbitt/Network-MultiTool) Multitool.

------

### Задание 1. Создать Deployment приложения и решить возникшую проблему с помощью ConfigMap. Добавить веб-страницу

1. Создать Deployment приложения, состоящего из контейнеров nginx и multitool.
2. Решить возникшую проблему с помощью ConfigMap.
3. Продемонстрировать, что pod стартовал и оба конейнера работают.
4. Сделать простую веб-страницу и подключить её к Nginx с помощью ConfigMap. Подключить Service и показать вывод curl или в браузере.
5. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

---

### Ответ

1. Скриншот, демонстрирующий, что pod стартовал и оба конейнера работают:

![Screen1](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/img/task2_3_1.png)

2. Создана простая веб-страница и подключена к Nginx с помощью ConfigMap, запущен Service:

![Screen2](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/img/task2_3_2.png)

3. Ссылка на итоговый Deployment с ConfigMap и Service внутри: [Deployment](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/src/task1/Deployment.yaml)

------

### Задание 2. Создать приложение с вашей веб-страницей, доступной по HTTPS 

1. Создать Deployment приложения, состоящего из Nginx.
2. Создать собственную веб-страницу и подключить её как ConfigMap к приложению.
3. Выпустить самоподписной сертификат SSL. Создать Secret для использования сертификата.
4. Создать Ingress и необходимый Service, подключить к нему SSL в вид. Продемонстировать доступ к приложению по HTTPS. 
4. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

---
### Ответ

1. Ссылка на Deployment приложения, состоящего из Nginx: [Deployment](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/src/task2/Deployment.yaml)

2. Ссылка на ConfigMap, содержащего веб-страницу: [ConfigMap](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/src/task2/configmap.yaml)

3. Скриншот, демонстрирующий получение самоподписном сертификате SSL: 

![Screen3](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/img/task2_3_3.png)

4. Ссылка на Secret, содержащий данные о самоподписном сертификате SSL, закодированные Base64: [Secret](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/src/task2/secret.yaml)

5. Ссылка на Ingress, принимающий данные о самоподписном сертификате SSL: [Ingress](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/src/task2/ingress.yaml)

6. Ссылка на Service: [Service](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/src/task2/service.yaml)

7. Скриншот, демонстрирующий доступность к сайту по HTTPS посредством curl: 

![Screen4](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/img/task2_3_4.png)

7. Скриншот, демонстрирующий доступность к сайту "извне" по HTTPS посредством браузера: 

![Screen5](https://github.com/megasts/kuber-homeworks/blob/task_2.3/2.3/img/task2_3_5.png)




------

### Правила приёма работы

1. Домашняя работа оформляется в своём GitHub-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl`, а также скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.

------
