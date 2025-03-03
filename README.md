# Прикладные задачи машинного обучения

## Домашнее задание #1:

### Описание
- Найти датасет для классификации на kaggle.com
- Выполнить разведочный анализ и визуализацию данных: построить распределения переменных, найти выбросы
- Применить все описанные методы классификации, сравнить их точность (метрика accuracy)
- Применить все описанные методы регрессии, сравнить их точность (метрика rmse)
- Сделать выводы
- Полезная библиотека: https://scikit-learn.org/

### Датасет
- [https://www.kaggle.com/datasets/nikhil7280/weather-type-classification/data](https://www.kaggle.com/datasets/nikhil7280/weather-type-classification/data)

### Решение
- **hw1.ipynb**

### Выводы

1. **Классификация (прогнозирование типа погоды)**
- Лучшая модель: дерево решений (точность 90,95%), за ней следуют SVM (90,68%) и KNN (89,17%)
- Наихудшая модель: LDA (83,52%) и SGD (83,83%)
- Наблюдения:
    - Общая высокая точность предполагает, что набор данных имеет хорошо разделенные классы.
    - Это верно, поскольку набор данных был синтетически сгенерирован для имитации данных о погоде для задач классификации.
2. **Регрессия (прогнозирование процента осадков)**
- Лучшая модель: SVM (RMSE = 16,86), за ней следует KNN (RMSE = 17,27)
- Наихудшая модель: линейная регрессия (RMSE = 23,06)
- Наблюдения:
    - SVM имела самую низкую RMSE, что означает, что она была наиболее точной в прогнозировании процентов осадков.
    - KNN показала хорошие результаты, предполагая, что модели осадков могут иметь локальное сходство.
    - Дерево решений показало худшие результаты (RMSE = 20,46), вероятно, из-за переобучения.
    - Линейная регрессия имела самую высокую RMSE, что указывает на то, что модели осадков могут не иметь простой линейной связи с другими переменными.

---

## Домашнее задание #2:

### Описание
- Добавить в решение ДЗ#1 метрики классификации и регрессии (чтобы суммарно их было не меньше 8)
- Использовать grid search + cross-валидацию для оценки качества
- Добиться хорошего качества классификации и регрессии на всех моделях

### Решение
- **hw2.ipynb**

### Выводы

Всего собрано 11 моделей, 7 классификационных и 4 регрессионных.

В каждой из моделей для этого домашнего задания было добавлено 2 дополнительных итерации.

Считая итерацию из домашнего задания 1 как итерацию 1, в итерации 2 было сделано начальное введение grid search и cross-validation с меньшим набором гиперпараметров.

В итерации 3 были введены расширенные гиперпараметры для улучшения результатов моделей.

Ниже перечислены числовые значения метрик для каждой итерации.

Лучшие результаты отмечены [*].

1. **Классификация (прогнозирование типа погоды)**
- Итерация 1 (hw1)
```
Decision Tree Accuracy: 0.9076
KNN Accuracy: 0.8917
[*] SVM Accuracy: 0.9068
[*] Logistic Regression Accuracy: 0.8485
[*] Naive Bayes Accuracy: 0.8629
[*] LDA Accuracy: 0.8352
SGD Accuracy: 0.8394
```
- Итерация 2 (hw2)
```
[*] Decision Tree Best Params: {'max_depth': 10}, Accuracy: 0.9106
KNN Best Params: {'n_neighbors': 5}, Accuracy: 0.8917
SVM Best Params: {'C': 10}, Accuracy: 0.9049
[*] Logistic Regression Best Params: {'C': 1}, Accuracy: 0.8485
[*] Naive Bayes Best Params: {}, Accuracy: 0.8629
[*] LDA Best Params: {}, Accuracy: 0.8352
SGD Best Params: {'alpha': 0.01}, Accuracy: 0.8413
```
- Итерация 3 (hw2)
```
Decision Tree Best Params: {'max_depth': 10, 'min_samples_split': 2}, Accuracy: 0.9102
[*] KNN Best Params: {'n_neighbors': 5, 'weights': 'distance'}, Accuracy: 0.8932
SVM Best Params: {'C': 10, 'kernel': 'rbf'}, Accuracy: 0.9049
[*] Logistic Regression Best Params: {'C': 10, 'solver': 'lbfgs'}, Accuracy: 0.8485
[*] Naive Bayes Best Params: {}, Accuracy: 0.8629
[*] LDA Best Params: {'solver': 'svd'}, Accuracy: 0.8352
[*] SGD Best Params: {'alpha': 0.001, 'loss': 'hinge'}, Accuracy: 0.8417
```

2. **Регрессия (прогнозирование процента осадков)**
- Итерация 1 (hw1)
```
Decision Tree RMSE: 20.2848
KNN RMSE: 17.2668
SVM RMSE: 16.8632
[*] Linear Regression RMSE: 23.0580
```
- Итерация 2 (hw2)
```
Decision Tree Best Params: {'max_depth': 5}, RMSE: 15.8409
KNN Best Params: {'n_neighbors': 7}, RMSE: 17.0721
[*] SVM Best Params: {'C': 10}, RMSE: 16.0255
[*] Linear Regression Best Params: {}, RMSE: 23.0580
```
- Итерация 3 (hw2)
```
[*] Decision Tree Best Params: {'max_depth': 10, 'min_samples_split': 10}, RMSE: 15.4908
[*] KNN Best Params: {'n_neighbors': 10, 'weights': 'distance'}, RMSE: 16.9667
[*] SVM Best Params: {'C': 10, 'kernel': 'rbf'}, RMSE: 16.0255
[*] Linear Regression Best Params: {}, RMSE: 23.0580
```