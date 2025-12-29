# Первоначальная настройка Git.
Добавляем пользователя

<img width="591" height="110" alt="image" src="https://github.com/user-attachments/assets/2779af97-f2df-43d4-b9d0-9bc56e3b2195" />

# Инициализация Git-репозитория

Создаем папку и переходим в нее

<img width="243" height="107" alt="image" src="https://github.com/user-attachments/assets/4f63d636-94a4-4f21-aff1-d60445c4a328" />


Создаем репозиторий с название PR2 на github

<img width="1838" height="872" alt="image" src="https://github.com/user-attachments/assets/600ebc1d-31d1-43ef-9566-a921c69eaccf" />


Инициализируем локальный репозиторий и подключи к GitHub

```bash
git init
git remote add origin https://github.com/Yaroslavka102741703/PR2.git
```

<img width="689" height="113" alt="image" src="https://github.com/user-attachments/assets/9f978982-23a8-4359-8b09-21ce36e631dd" />


# Создадим начальный коммит в ветку master:


```bash
echo "# PR2" > README.md
git add README.md
git commit -m "Initial commit"
git push -u origin master
```

<img width="819" height="517" alt="image" src="https://github.com/user-attachments/assets/cc7571cd-af81-4a9d-bdef-ac5366f8e0b8" />


# Создаем ветку feature/TASK-123 от master

```bash
git checkout -b feature/TASK-123
```

Создай файл с ФИО и группой 

```bash
echo "Имя: Швыркова Яна" > info.txt
echo "Группа: ПИ-430Б" >> info.txt
```

# Делаем коммит

git add info.txt
git commit -m "Add student info"


# Еще 2 коммита


```bash
echo "Дополнительная строка 1" >> info.txt
git add info.txt
git commit -m "Update info: add line 1"

echo "Дополнительная строка 2" >> info.txt
git add info.txt
git commit -m "Update info: add line 2"
```



<img width="982" height="791" alt="image" src="https://github.com/user-attachments/assets/c2b05c3e-1d63-477c-ba55-7e44563dc9d4" />


# Создаем ветк bugfix/TASK-3321 от master

```bash
git checkout master
git checkout -b bugfix/TASK-3321
```


Теперь изменяем тот же файл info.txt, но в другие строки

```bash
echo "Группа: ПИ-430" > info.txt
echo "Имя: Яна Швыркова" >> info.txt
echo "Email: Yaroslavka102741703@mail.ru" >> info.txt
```


<img width="546" height="206" alt="image" src="https://github.com/user-attachments/assets/fbf93f22-84ae-43dc-8753-0502ed0f9931" />


---

Коммитим

``bash
git add info.txt
git commit -m "Add email to student info"
```

И еще 2 коммита

```bash
echo "Телефон: +123456789" >> info.txt
git add info.txt
git commit -m "Add phone number"

echo "GitHub: @Yaana" >> info.txt
git add info.txt
git commit -m "Add GitHub handle"
```

Вносим временные изменения


```bash
echo "ВРЕМЕННЫЕ ИЗМЕНЕНИЯ" >> info.txt
git stash
```

<img width="956" height="142" alt="image" src="https://github.com/user-attachments/assets/87ec9028-5c30-47b9-bba9-def7bf619932" />


Переключаемся на feature/TASK-123, смотрим файлы:

<img width="482" height="194" alt="image" src="https://github.com/user-attachments/assets/6d0d41f4-157c-4156-a201-2c5d60bffaac" />



Возвращаемся обратно в bugfix/TASK-3321 и восстановливаем изменения:

```bash
git checkout bugfix/TASK-3321
git stash pop
```

Убеждаемся, что строка "ВРЕМЕННЫЕ ИЗМЕНЕНИЯ" вернулась:

```bash
cat info.txt
```

<img width="698" height="450" alt="image" src="https://github.com/user-attachments/assets/4165c2cd-c691-42e8-a0e8-91cabb11f235" />


Теперь можно закоммитить эти изменения

```bash
git add info.txt
git commit -m "Add temporary note (restored from stash)"
```


# Пушим ветки

```bash
git push -u origin feature/TASK-123
git push -u origin bugfix/TASK-3321
```

<img width="827" height="643" alt="image" src="https://github.com/user-attachments/assets/6b418450-834d-4437-8d39-bc214b5561df" />


# Сливаем в мастер

```bash
git checkout master
git merge feature/TASK-123
```

<img width="511" height="227" alt="image" src="https://github.com/user-attachments/assets/80bd0c32-a621-41b6-98b7-32bbebeaca23" />

```bash
git merge bugfix/TASK-3321
```

<img width="641" height="110" alt="image" src="https://github.com/user-attachments/assets/c29aa4c9-5b13-41ad-a4c3-1c3789713849" />


Решаем конфликт

```bash
nano info.txt
```


<img width="432" height="372" alt="image" src="https://github.com/user-attachments/assets/c4c7c1a6-440f-4659-abea-d46b1d0c5f2b" />


В ручную удаляем конфликтующие строки

<img width="347" height="184" alt="image" src="https://github.com/user-attachments/assets/380794a8-8029-48b4-bd0e-1ae1ab8ceebd" />


```bash
git add info.txt
git commit -m "Merge bugfix/TASK-3321 into main with conflict resolution"
git push origin main
```







