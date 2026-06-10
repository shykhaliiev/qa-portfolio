# C-1: Валідація порожніх обовʼязкових полів форми «Заявка на консультацію»

**Section**  
Контактна форма «Заявка на консультацію» (class="Form_form__QZ5t9")

**Type**  
Functionality

**Priority**  
1 (must test)

**Estimate**  
3 хвилини

**Milestone**

**References**

**Preconditions**  
1. Відкрити https://banklviv.ua/private-persons/deposits/depozyt-znayomstvo;
2. Перейти до форми «Заявка на консультацію». Форма доступна:
    * в статичному вигляді на сторінці; 
    * в модальному вікні через кнопку «Замовити дзвінок» в footer.

**Steps**  
1. Залишити поля «Імʼя» та «Номер телефону» порожніми;
2. Встановити чекбокс згоди на обробку персональних даних;
3. Натиснути кнопку «Надіслати».

**Expected results**  
1. Поля залишаються порожніми;
2. Чекбокс успішно встановлюється;
3. Кнопка «Надіслати» залишається заблокованою, відправка форми – неможлива.

# C-2 — Серверна валідація запиту без обов'язкових параметрів форми «Депозитна консультація»

**Section**  
Контактна форма «Депозитна консультація» (/catalog/htmx/send_feedback/41)

**Type**  
Functionality

**Priority**  
1 (must test)

**Estimate**  
5 хвилин

**Milestone**

**References**

**Preconditions**  
1. Створити новий запит у Postman;
2. Обрати HTTP-метод: POST;
3. Вказати ендпоінт: /catalog/htmx/send_feedback/41;
4. У вкладці Headers додати:
    * Content-Type: application/x-www-form-urlencoded;
    * X-CSRFToken: *валідний CSRF-токен*.

**Steps**  
1. Перейти у вкладку Body й обрати тип x-www-form-urlencoded;
2. Заповнити технічні поля форми, залишити поля name й phone_number порожніми:
    * csrfmiddlewaretoken = *валідний CSRF-токен*
    * name = *порожнє поле*
    * phone_number = *порожнє поле*
    * agreement = on
    * sub_product_id = 41
    * utm_source = Зовнішній сайт (Депозитний калькулятор)
3. Надіслати запит.

**Expected results**  
1.  
2.  
3. Сервер відхиляє запит через відсутність обов'язкових параметрів (name та phone_number);  
Код статусу відповіді: 400 Bad Request;   
Тіло відповіді: повідомлення про те, що поля «ПІБ» та «Номер телефону» є обов'язковими для заповнення.
