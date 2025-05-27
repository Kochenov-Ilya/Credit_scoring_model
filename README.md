# Прогнозирование кредитного дефолта с использованием машинного обучения
## Описание
Проект направлен на прогнозирование риска дефолта клиентов (SeriousDlqin2yrs) на основе кредитной истории. Решение включает полный цикл:
- Анализ и предобработка данных
- Визуализация распределений признаков
- Балансировка классов (SMOTE)
- Обучение моделей (XGBoost, Logistic Regression)
- Оценка метрик (F1, ROC-AUC, Precision/Recall)
- Интерпретация модели с помощью SHAP

## Ключевые особенности
✅ Обработка пропусков и выбросов  
✅ Анализ корреляций признаков  
✅ Оптимизация гиперпараметров  
✅ Подробная интерпретация результатов

## Технологии
- Python 3.8+
- Библиотеки: Pandas, NumPy, Scikit-learn, XGBoost, SHAP, Matplotlib
## Основные признаки:
- age	Age of borrower in years
- NumberOfDependents	Number of dependents in family excluding themselves (spouse, children etc.)	integer
- NumberOfTime60-89DaysPastDueNotWorse	Number of times borrower has been 60-89 days past due but no worse in the last 2 years.
- NumberRealEstateLoansOrLines	Number of mortgage and real estate loans including home equity lines of credit
- NumberOfTimes90DaysLate	Number of times borrower has been 90 days or more past due.
- MonthlyIncome	Monthly income
- NumberOfOpenCreditLinesAndLoans	Number of Open loans (installment like car loan or mortgage) and Lines of credit (e.g. credit cards)
- DebtRatio	Monthly debt payments, alimony,living costs divided by monthy gross income	percentage
- NumberOfTime30-59DaysPastDueNotWorse	Number of times borrower has been 30-59 days past due but no worse in the last 2 years
- SeriousDlqin2yrs	Person experienced 90 days past due delinquency or worse '
- RevolvingUtilizationOfUnsecuredLines	Total balance on credit cards and personal lines of credit except real estate and no installment debt like car loans divided by the sum of credit limits	percentage
## Результаты:
Я остановился на модели XGB.Модель отлично справляется с задачей прогназирования дефолта заёмщика.Алгоритм выявляет 94% рискованных заёмщиков с точность 88% ,что критично для минимизации убытков. Интерпретируемость влияния ключевых факторов:доход , долговая нагрузка , колличество активных кредитов, возраст заёмщика ,соответствует доменным знаниям.
Метрики модели :
Recall:94%
Precision:88%
ROC-AUC:92%
F1-score:91%
Ограничения модели:
Модель не учитывает социально-экономический контекст
Улучшения:
Возрастное смещение приводит к недостаточной репрезентативности для молодых заёмщиков,стоит провести сбор дополнительных данных с меньшим средним возрастом
NumberOfTimes90DaysLate,NumberOfTime60-89DaysPastDueNotWorse,NumberOfDependents - слишком разреженные и практически не влияют на прогноз модели, необходимо провести сбор дополнительных данных для того чтобы обучить модель эффективно использовать эти фичи
Проверка модели на данных из других регионов/временных периодов.
Примеры
Если у заёмщика увеличится колличество активных кредитов , то прогноз модели увеличится(вероятность дефолта станет выше)
При увеличении месячного дохода прогноз модели уменьшится(вероятность дефолта станет ниже)
Коэффициент использования кредита - чем выше тем выше вероятность дефолта

