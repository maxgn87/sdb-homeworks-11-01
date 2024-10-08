# Домашнее задание к занятию «Базы данных, их типы - Гнедин Максим»

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

---

### Задание 1. СУБД

### Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать 
правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для
каждой предметной области. 

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему? 
 
1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков.
СУБД должна гарантировать целостность и чёткую структуру данных.

1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы? 

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к 
маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? 
СУБД должны быть гибкими и быстрыми.

1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу 
и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это 
реализовать?

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов 
по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать
со связями.

1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД 
логистов?

1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

*Приведите ответ в свободной форме.*

---
### Решение :
1.1 Можно рассмотреть Реляционные СУБД (PostgreSQL, MySQL, SQL Server). Эти СУБД обеспечивают строгую структуру данных, хорошие средства аналитики данных и высокую производительность благодаря оптимизаторам запросов. 
1.2 Рассмотреть Документированную  СУБД (например, MongoDB). Она позволяет хранить данные в гибком формате JSON, легко адаптироваться к изменениям структуры данных и обеспечивает высокую производительность при чтении и записи. Для CRM можно использовать специализированные решения на базе этой СУБД.
1.3 Реляционная СУБД (например, MySQL). Для небольших объемов данных и простой структуры она будет оптимальным выбором.
1.4 Графовая СУБД (например, Neo4j). Она может подходит для представления сложных связей между объектами (маршруты, курьеры, материалы) и позволяет эффективно выполнять поиск по графу.


### Задание 2. Транзакции

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы 
транзакция завершилась успешно. Ориентируйтесь на шесть действий.

2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?

*Приведите ответ в свободной форме.*

---
### Решение :
1. Инициция транзакции. Пользователь выбирает способ пополнения (банковская карта, электронный кошелёк, терминало оплаты и.т.д). Пользователь вводит необходимую информацию: номер телефона, сумму пополнения.
2. Проверка данных. Проверка корректности введённых данных( правильность номера телефона, сумму и наличие стредств на счёте).
3. Аторизация платежа. Пользователю может потребоваться пройти дополнительную авторизацию (например, ввести одноразовый пароль, подтвердить платеж по SMS).  Система направляет запрос на авторизацию платежа в платежную систему или банк.
4.Обработка транзакции. Платежная система или банк обрабатывают запрос и подтверждают списание средств с платежного средства пользователя.Система оператора связи получает уведомление о поступлении платежа
5. Зачисление средств на счёт. Система оператора связи зачисляет указанную сумму на баланс телефона пользователя.Система формирует отчет о проведенной транзакции.
6. Подтверждение транзакции. Пользователь получает уведомление о успешном зачислении средств на счет телефона (SMS, push-уведомление, email).Система может предоставить чек или электронную квитанцию о проведенной операции.


### Задание 3. SQL vs NoSQL

3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL. 

3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.

*Приведите ответ в свободной форме.*

---

### Решение : 

1. Структура и целостность данных.
2. Сложные запросы: SQL предоставляет богатый набор операторов и функций для выполнения сложных запросов к данным, включая выборку,сортировку, группировку, агрегатные функции и соединения таблиц.
3. Транзакционность. Откат транзакций: В случае сбоя транзакция может быть откатана, что позволяет восстановить систему в исходное состояние
4. Масштабируемость. Вертикальная масштабируемость: SQL-системы хорошо масштабируются путем увеличения аппаратных ресурсов сервера, что позволяет обрабатывать большие объемы данных.
5. Зрелость и поддержка.Длительная история: SQL-системы существуют уже несколько десятилетий и имеют хорошо развитую экосистему инструментов и технологий.

### Задание 4. Кластеры

Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу 
выделено 1000 машин. 

На основе какого критерия будете выбирать тип СУБД и какая модель *распределённых вычислений* 
здесь справится лучше всего и почему?

*Приведите ответ в свободной форме.*

---
### Решение : 
Критерии выбора :
1. Масштабируемость: СУБД должна легко масштабироваться горизонтально, чтобы распределить нагрузку на множество машин.
2. Производительность: Важна высокая скорость выполнения запросов, особенно при работе с большими объемами данных.
3. Поддержка распределенных вычислений: СУБД должна эффективно работать в распределенной среде, поддерживая параллельное выполнение запросов.
4. Поддержка аналитических запросов: Если требуется проводить сложные аналитические расчеты, то СУБД должна предоставлять соответствующие инструменты.
5. Стоимость: Необходимо учитывать стоимость лицензирования и эксплуатации СУБД.
Для решения такой задачи наиболее подходящей моделью распределенных вычислений будет MapReduce. Эта модель позволяет разбить большую задачу на множество небольших, независимых задач, которые могут выполняться параллельно на разных машинах. Затем результаты этих задач объединяются для получения окончательного результата.


Задания,помеченные звёздочкой, — дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже разобраться в материале.
