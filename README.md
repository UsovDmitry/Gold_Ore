<a name= ""> </a>
## **Предсказание коэффициента восстановления золота из золотосодержащей руды**
___
### Содержание
___
1.  [Предсказание коэффициента восстановления золота из золотосодержащей руды](#0)    
	1.1 [Описание проекта](#1)  
	1.2 [Описание данных](#2)  
	1.3 [Условия задачи](#3)    
2. [Вывод](#4)    

___
<a name= "1"> </a>
### Описание проекта
Подготовьте прототип модели машинного обучения для «Цифры». Компания разрабатывает решения для эффективной работы промышленных предприятий.  
Модель должна предсказать коэффициент восстановления золота из золотосодержащей руды. В вашем распоряжении данные с параметрами добычи и очистки.  
Модель поможет оптимизировать производство, чтобы не запускать предприятие с убыточными характеристиками.
___
<a name= "2"> </a>
### Описание данных

Данные находятся в трёх файлах:

    Данные в первом файле предстаявляют собой обучающую выборку;
    Второй файл — тестовая выборка;
    Третий файл — исходные данные.

Данные индексируются датой и временем получения информации (признак date). Соседние по времени параметры часто похожи.
Некоторые параметры недоступны, потому что замеряются и/или рассчитываются значительно позже. Из-за этого в тестовой выборке отсутствуют некоторые признаки, которые могут быть в обучающей. Также в тестовом наборе нет целевых признаков.
Исходный датасет содержит обучающую и тестовую выборки со всеми признаками.
В вашем распоряжении сырые данные: их просто выгрузили из хранилища. Прежде чем приступить к построению модели, проверьте по нашей инструкции их на корректность.

___
<a name= "3"> </a>
### Условия задачи

1. Необходимо проверить, что эффективность обогащения рассчитана правильно. Вычислить её на обучающей выборке для признака rougher.output.recovery. Найти MAE между расчётами и значением признака. Описать выводы.  
2. Проанализировать признаки, недоступные в тестовой выборке. Что это за параметры? К какому типу относятся?  
3. Провести предобработку данных.  
4. Проанализируйте данные  
	4.1 Посмотрите, как меняется концентрация металлов (Au, Ag, Pb) на различных этапах очистки. Опишите выводы.  
	4.2 Сравните распределения размеров гранул сырья на обучающей и тестовой выборках. Если распределения сильно отличаются друг от друга, оценка модели будет неправильной.  
	4.3. Исследуйте суммарную концентрацию всех веществ на разных стадиях: в сырье, в черновом и финальном концентратах.
5. Постройте модель  
6. Напишите функцию для вычисления итоговой sMAPE.  
7. Обучите разные модели и оцените их качество кросс-валидацией. Выберите лучшую модель и проверьте её на тестовой выборке. Опишите выводы
___
<a name= "4"> </a>
### Вывод
Очистив данные и подготовив/оптимизировав признаки для обучающей и тестовой выборки, мы можем сделать следующие заключения:

    1. Выборка содержит столбец с корректными данными по коэффициенту обогащения. Проверка проводилась с помощью формулы обогащения. Это важный показатель, который учитывает содержания металла на различных технологических процессах.
    2. Распределения размеров гранул на обучающей и тестовой выборках практически совпадает, это говорит о том, что выборки сформированы корректно.
    3. В тестовой выборке отсутвовали ряд важных признаков(rougher.output.recovery,final.output.recovery), которые мы в добавили.
    4. Было проведено исследование суммарных концентрации металлов на различных стадиях тез.процесса. Был обнаружен аномальный выброс данных в "нулевых" значениях, который был в последствии удален.
    5. В процессе исследования моделей обучения, была выбрана модель RandomForestRegressor() на основе которой метрика качества sMAPE(симметричное среднее абсолютное процентное отклонение) показала наименьшие значения по дефолту (9.09), в процессе оптимизации гиперпараметров, значение sMAPE удалось снизить до 8.87.
    6. Проверка данной модели на тестовой базе, показало прекрасный показатель метрики качества sMAPE равным 7.15


___
