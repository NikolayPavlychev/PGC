Проект ProductGroupPrediction
------------------------------

Проект ProductGroupPrediction направлен на решение задач классификации товарных карточек по их текстовому описанию.
Он реализован для работы сайта компании по продаже автозапчастей и внедрен в бизнес-процесс.

Целевая метрика accuracy по всем классам(n~1000) = 87% на тестовой выборке.

Модель развернута на сервере заказчика и взаимодействие ведется по CLI.


CLI
------------------------------

1. Препроцессинг
------------------------------

<путь до интерпретатора> preprocessing.py <путь до .csv файла> <режим>

<путь до .csv файла> файл должен иметь атрибуты ['artical', 'brend_code', 'desc', 'guid', 'group_code']

<режим>:
train - переобучение модели на данных из .csv файла
inference - инференс модели на данных из .csv файла
inference_production - инференс предобученной модели на данных из .csv файла

2. Обучение, инференс и оценка модели
------------------------------

<путь до интерпретатора> training_inference.py <путь до .csv файла> <режим>

<путь до .csv файла> файл должен иметь атрибуты ['artical', 'brend_code', 'desc', 'guid', 'group_code']

<режим>:
train - переобучение модели на данных из .csv файла
inference - инференс модели на данных из .csv файла
inference_production - инференс предобученной модели на данных из .csv файла

Артефакт с предсказаниями продуктовых групп:
Атрибуты: ['artical','group_code','group_code_predict']
<имя .csv файла>_predictions'+'_inference.csv',sep=';',index=False)
	
Пример запуска:
	
/home/nikolaypavlychev/ProductGroupClassification/prod_2/prod_2/prod/pgc/bin/python preprocessing.py dataset_groups_before_analyse_sub.csv inference_production
/home/nikolaypavlychev/ProductGroupClassification/prod_2/prod_2/prod/pgc/bin/python training_inference.py dataset_groups_before_analyse_sub.csv inference_production

3. Cлучайная выборка 
------------------------------

<путь до интерпретатора> random_samples.py 

Формируется dataset_groups_before_analyse_sub.csv, содержащий случаные 100000 записей из dataset_groups_before_analyse.csv
