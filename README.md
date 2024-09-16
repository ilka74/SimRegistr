Задача проекта - "Имитация регистрации пользователей на интернет-платформе".

На основе фреймворка Django создан проект "UrbanDjango" с приложением "task".
В папке "templates" проекта находится шаблон "registration_page.html". Он содержит форму с полями для ввода и кнопку для её отправки.
Поля для ввода и подписи:
* для логина - поле "username" с ограничением длины в 30 символов. Подпись: "Введите логин";
* для пароля - поле "password" с ограничением длины не менее 8 символов. Подпись: "Введите пароль";
* для повтора пароля - "repeat_password" с ограничением длины не менее 8 символов. Подпись: "Повторите пароль";
* для возраста - поле "age" с ограничением длины в 3 символа. Подпись: "Введите свой возраст".

В файле "forms" папки с приложением "task" разработана и сохранена форма "UserRegister", наследованная от Django формы с аналогичными параметрами, как и в шаблоне. 

В файле "views" папки с приложением написаны два представления "sign_up_by_django" и "sign_up_by_html".
Оба представления обладают следующим функционалом:
* псевдо-список users уже существующих пользователей; 
* пустой словарь info, который передается в context функции render. В случае формы в этом словаре также находится и сама форма;
* получение данных из POST запроса;
* обработка данных из POST запроса.
-----------------------------------------------
Если при вводе пароль и повторный пароль совпадают + возраст не менее 18 лет + пользователя ещё нет в users, то возвращаем ответ 
"Приветствуем, <логин пользователя>!": 
![image](https://github.com/user-attachments/assets/f1f07009-af78-4ac2-99d4-e596bdbb2d3e)
![image](https://github.com/user-attachments/assets/f7432567-99e9-48b2-9589-900e74332323)

В следующих случаях в словарь info добавляются следующие значения под ключом 'error':
1. "Пароли не совпадают" - если не совпали введённые пароли.
2. 'Вы должны быть старше 18', если возраст меньше 18.
3. 'Пользователь уже существует', если username есть в users.

Соответственно выводится значение переменной "error" в шаблоне:
![image](https://github.com/user-attachments/assets/45ae5b5a-fb01-48b3-8beb-05abda32ed79)
![image](https://github.com/user-attachments/assets/371f632a-a1ac-411d-8d64-b5f9dbf769ec)
![image](https://github.com/user-attachments/assets/a0c03886-27b9-4471-8e88-c23f44ee900c)

-----------------------------------------------
Представления запускаются по маршрутам, описанным в файле "urls.py" папки с настройками проекта Django:
path('', sign_up_by_html),
path('django_sign_up/', sign_up_by_django)
