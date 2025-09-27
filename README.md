# Домашнее задание к занятию 11 «Teamcity»

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

## Основная часть

1. Создайте новый проект в teamcity на основе fork.

<img width="1159" height="394" alt="image" src="https://github.com/user-attachments/assets/20036ab0-6495-4fb9-b823-66601ed31a00" />

2. Сделайте autodetect конфигурации.
3. Сохраните необходимые шаги, запустите первую сборку master.

<img width="1173" height="647" alt="image" src="https://github.com/user-attachments/assets/37cba2ed-c6f3-4bb6-9fd7-59702e6458aa" />

4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.

<img width="1153" height="434" alt="image" src="https://github.com/user-attachments/assets/7a915ab5-3675-4a1f-bafe-dc8147570519" />

5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.

<img width="896" height="535" alt="image" src="https://github.com/user-attachments/assets/28499155-6d71-4196-8b1b-18bfeb5f9c47" />

8. Мигрируйте `build configuration` в репозиторий.

<img width="754" height="1151" alt="image" src="https://github.com/user-attachments/assets/f877815e-0728-423f-a6e3-50c55dffdeb7" />

9. Создайте отдельную ветку `feature/add_reply` в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.

<img width="778" height="546" alt="image" src="https://github.com/user-attachments/assets/bdf48425-f2e3-4330-bc8e-2f030cf762c2" />

11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.

<img width="731" height="793" alt="image" src="https://github.com/user-attachments/assets/a7a103b6-6655-4447-abd7-f9d0b4af6142" />

12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.

<img width="1165" height="114" alt="image" src="https://github.com/user-attachments/assets/d0742cad-9358-4b73-ac88-1b8dd0c61db3" />

14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.

<img width="912" height="145" alt="image" src="https://github.com/user-attachments/assets/7b52b46c-6343-4ff3-b992-c0e14fbc8a06" />

15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.

<img width="1072" height="384" alt="image" src="https://github.com/user-attachments/assets/26dab3aa-b4c3-49ba-b233-b68ce8243acd" />

18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.

<img width="1242" height="611" alt="image" src="https://github.com/user-attachments/assets/ff774c85-59cd-4432-ad2f-b2ecbd6dea3a" />

19. В ответе пришлите ссылку на репозиторий.

https://github.com/Nightnek/example-teamcity

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
