# Лабораторна робота 10. "Механізм виключень"

## Цілі лабораторної роботи

- зрозуміти механізм помилок на етапі компіляції та на етапі роботи додатку
- вивчити механізм виключень в Java

## Хід роботи

### Завдання 1

Реалізуйте клас `TimeSpan` із лабораторної роботи №4.

Створіть власні класи виключень, які походять від базового класу `RuntimeException` для наступних подій у класі:

- `NegativeTimeSpanException` - виключення викидається, коли значення поточного `TimeSpan` стає від'ємним;
- `IllegalInputTimeSpanException` - виключення викидається, коли значення вхідного інтервалу часу є некоректним (від'ємна кількість годин та\або хвилин, кількість хвилин понад 59 при двох вхідних аргументах);
- `IllegalScaleFactorException` - виключення викидається, коли значення вхідного множника у методі `scale` є некоректним.

Додайте до вихідного коду механізм обробки виключних ситуацій за допомогою власних класів виключень.

Ви можете додати власні класи виключень для інших виключних ситуацій, які пов'язані з даним класом та сутністю "інтервал часу".

### Завдання 2

В проєкт лабораторної роботи присутній частково розроблений клієнт консольного додатка для управління банківськими рахунками. Додаток дозволяє виконувати наступні дії:

- створювати новий рахунок;
- видаляти рахунок;
- вносити кошти на рахунок;
- знімати кошти з рахунку;
- видруковувати інформацію щодо рахунку.

Ваше завдання полягає в наступному:

**Пункт 1**

Для моделювання банківського рахунку в додатку повинен бути реалізований базовий клас `BankAccount` та похідний клас `CheckingAccount`, який моделює рахунок з денним лімітом на зняття коштів.

Заголовки класів наведені в додатку в пакеті `model`. Якщо потрібно, змініть заголовки та додайте потрібні поля та методи згідно з UML діаграмою, наведеною нижче.

<p align="center" style="margin:auto">
  <img src="https://i.imgur.com/7EngVp3.png" />
</p>

Поле `dailyWithdrawalLimit` повинно мати значення `300` за замовченням. Потрібно передбачити гетер та сетер для даного поля.

**Пункт 2**

Реалізуйте додаток з дотриманням умов та обмежень, які будуть описані нижче. Додаток повинен бути працездатним, методи класів `BankAccount` та `CheckingAccount` повинні бути реалізовані та працювати коректно.

**Пункт 3**

При реалізації додатку ви повинні передбачити власні класи виключень (базовим класом для власних підкласів може виступати клас `RuntimeException`).

Додаток має такі умови та обмеження.

Обмеження банківського рахунку:

- поле `userId` повинно бути унікальним для банківського рахунку, не може бути двох банківських рахунків з однаковим `userId`;
- пароль повинен бути довжиною щонайменше `8` символів та містити щонайменше одну цифру;
- баланс рахунку не може бути від'ємним - баланс може бути `0` чи більше.

При створенні акаунту:

- переконайтеся, що новий рахунок має унікальний `userId` та коректний пароль;
- пароль та підтвердження паролю повинні збігатися;
- новий акаунт повинен бути об'єктом типу `CheckingAccount`.

При видаленні акаунту:

- користувач повинен ввести `userId` та пароль рахунку;
- користувач не може видалити рахунок з ненульовим балансом.

При внесенні коштів:

- користувач повинен ввести `userId` та пароль рахунку;
- значення внеску повинно бути більше `0`.

При знятті коштів:

- користувач повинен ввести `userId` та пароль рахунку;
- сума повинна бути більше `0`, але не може перевищувати денний ліміт для зняття коштів.

При друку інформації щодо рахунку:
- користувач повинен ввести `userId` та пароль рахунку.

**Пункт 4**

Ви повинні обробляти виняткові ситуації, які виникають при порушенні умов та обмежень додатку (наприклад, користувач ввів некоректний пароль чи хоче зняти кошти більше денного ліміту тощо) за допомогою власних класів виключень.

Класи виключень повинні бути створені в пакеті `exceptions`.

Ви можете організувати ієрархію виключень за допомогою механізму успадкування (наприклад, створити клас `AccountException`, який буде базовим класом для виняткових ситуацій, пов'язаних з банківським акаунтом).

При виникненні виняткової ситуації, додаток повинен вивести повідомлення щодо помилки (повідомлення можна вивести в потік помилок за допомогою методу `System.err.println()`), після чого повернутися в головне меню.

При успішному виконанні операції, додаток повинен повідомити користувача про успішне виконання операції та повернутися до головного меню.

**Пункт 5**

Для обробки виняткових ситуацій ви можете використовувати всі можливості механізму виключень: `try-catch`, `throw`, `throws` тощо.
