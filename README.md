# analysis_of_240_profiles_in_mamba

Спарсила 240К анкет на mamba.ru, парсила только то, что видно всем, а точнее: 
- возраст
- рост
- вес
- образование
- о себе
- с кем живу
- дети
- цель на сайте
- пол
- в каком поле заинтересован
- язык
- возраст партнера

Сделала так, чтобы мужчин и женщин было одинаково (сначала мужчин было намного больше, пришлось парсить еще только женщин, иначе результаты статистических тестов были какие-то скошенные). 
<img width="116" alt="genders_count" src="https://user-images.githubusercontent.com/84775580/199487357-b60e9c62-e89a-49ef-a014-e27e59ca6c19.png">

Посмотрела на графики возрастов и убрала "выбросы", хвосты, оставив только 18-45 лет включительно. Получилось вполне похожее на нормальное распределение. 
![ages_men](https://user-images.githubusercontent.com/84775580/199490138-4bc71d03-850b-498f-a6d9-8b298121129d.png)

![ages_women](https://user-images.githubusercontent.com/84775580/199490158-c24379f0-5362-4c0e-89c4-30ee047c509e.png)

Добавила дополнительные столбцы:
- диапазон возраста партнера (есть и такие, но их мало, кто искал в диапазоне до 60 лет)
- начальные возраст партнера
- упростила (сгруппировала) разнообразие целей на 6 групп: флирт, отношения, семья, друзья, неуверенные (очень много целей, от 5), не указали цель. 
- столбец процента, иначе, сколько процентов от общего числа мужчин или женщин составляет один мужчина или одна женщина соответственно. 

Постепенно в ходе анализа заметила, что работал закон больших чисел - поэтому каким-то базовым статистикам можно доверять смело. А точнее - по возрасту, весу, росту. Получилась некоторая демографическая сводка. 
<br> Возраст - 31 
<br> Вес - 70
<br> Рост - 172 
<img width="313" alt="basic statistics" src="https://user-images.githubusercontent.com/84775580/199488242-1c1e3f78-2888-4c6c-a604-87eb3d87cdaa.png">

Посмотрела, чтобы удостовериться, есть ли корреляция в возрастах между теми, кто ищет, и теми, кого ищут. Закономерно, корреляция практически прямая: более старшие ищут более старших. 
<img width="193" alt="searxhfor" src="https://user-images.githubusercontent.com/84775580/199489919-d0a04959-6748-4fe1-8541-e22da40d3dfa.png">

Анализ целей. 
Распределение целей на графике вполне соответствует генеральной совокупности, проверила с помощью хи-квадрата. 

![newplot](https://user-images.githubusercontent.com/84775580/199490573-f1c2421a-1cb5-4c89-baa1-e908392ce354.png)

Отличаются ли цели на сайте по возрастам у мужчин и женщин?

![aim_age_gender_dist](https://user-images.githubusercontent.com/84775580/199491056-10d24f38-8e06-414d-be3e-321b9c3e0b30.png)


Средние возраста по целям:
* флиртовать, встречаться: м 31, ж 29
* быть в отношениях: м 31, ж 32
* дружить: м, ж ~ 30
* хочу все подряд: м 32, ж 31
* не указали цель: м 31, ж 30
* семья: м, ж ~ 34,5

📣 Очевидный вывод - средний возраст колеблется от 29 до 32 с маленькими различиями. Самый большой разрыв в 2 года в цели флирт: мужчины хотят в 31, а женщины - в 29.

В целом, в около 30 все хотят "гулять" и люди ищут партнера (романтического, сексуального, дружеского), к семье приходят к 35, и мало кто сидит на сайте с целью семьи (всего ~0,9%) ❤

п.с. Данные проверены на t-test, в возрастах нет выбросов (возраст от 18 до 45 лет), но, в целом, данных настолько много, что начинает действовать закон больших чисел - и, в теории, уже можно (было бы достаточно) использовать центральную предельную теорему.
