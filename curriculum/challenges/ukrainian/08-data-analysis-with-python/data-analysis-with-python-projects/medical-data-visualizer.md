---
id: 5e46f7f8ac417301a38fb92a
title: Візуалізатор медичних даних
challengeType: 10
forumTopicId: 462368
dashedName: medical-data-visualizer
---

# --description--

Ви будете <a href="https://gitpod.io/?autostart=true#https://github.com/freeCodeCamp/boilerplate-medical-data-visualizer/" target="_blank" rel="noopener noreferrer nofollow">працювати над цим проєктом з нашим стартовим кодом Gitpod</a>.

Ми досі розробляємо інтерактивну частину навчальної програми з Python. Наразі є декілька відео на ютуб-каналі freeCodeCamp.org, які навчать всього необхідного для виконання цього проєкту:

- <a href="https://www.freecodecamp.org/news/python-for-everybody/" target="_blank" rel="noopener noreferrer nofollow">Python for Everybody Video Course</a> (14 годин)

- <a href="https://www.freecodecamp.org/news/how-to-analyze-data-with-python-pandas/" target="_blank" rel="noopener noreferrer nofollow">How to Analyze Data with Python Pandas</a> (10 годин)

# --instructions--

In this project, you will visualize and make calculations from medical examination data using `matplotlib`, `seaborn`, and `pandas`. Значення набору даних були зібрані під час медичних оглядів.

## Опис даних

Рядки в наборі даних представляють пацієнтів, а стовпці інформацію, як-от вимірювання тіла, результати різних аналізів крові та вибір способу життя. Ви будете використовувати набір даних, щоб дослідити зв’язок між серцевими захворюваннями, розмірами тіла, маркерами крові та вибором способу життя.

Назва файлу: medical_examination.csv

|                      Особливість                      |       Тип змінної       |    Змінна     |                   Тип значення                    |
|:-----------------------------------------------------:|:-----------------------:|:-------------:|:-------------------------------------------------:|
|                          Вік                          | Об’єктивна особливість  |     `age`     |                 ціле число (дні)                  |
|                         Зріст                         | Об’єктивна особливість  |   `height`    |                  ціле число (см)                  |
|                         Вага                          | Об’єктивна особливість  |   `weight`    |                плаваюче число (кг)                |
|                         Стать                         | Об’єктивна особливість  |   `gender`    |                 категоричний код                  |
|              Систолічний кров’яний тиск               | Особливість обстеження  |    `ap_hi`    |                    ціле число                     |
|              Діастолічний кров’яний тиск              | Особливість обстеження  |    `ap_lo`    |                    ціле число                     |
|                      Холестерин                       | Особливість обстеження  | `cholesterol` | 1: нормально, 2: вище норми, 3: значно вище норми |
|                        Глюкоза                        | Особливість обстеження  |    `gluc`     | 1: нормально, 2: вище норми, 3: значно вище норми |
|                        Куріння                        | Суб’єктивна особливість |    `smoke`    |                     двійкове                      |
|                   Вживання алкоголю                   | Суб’єктивна особливість |    `alco`     |                     двійкове                      |
|                  Фізична активність                   | Суб’єктивна особливість |   `active`    |                     двійкове                      |
| Наявність чи відсутність серцево-судинних захворювань |     Цільова змінна      |   `cardio`    |                     двійкове                      |

## Завдання

Create a chart similar to `examples/Figure_1.png`, where we show the counts of good and bad outcomes for the `cholesterol`, `gluc`, `alco`, `active`, and `smoke` variables for patients with `cardio=1` and `cardio=0` in different panels.

Використайте дані для виконання наступних завдань у `medical_data_visualizer.py`:

- Додайте стовпчик `overweight` до даних. Щоб визначити, чи має людина зайву вагу, спочатку обчисліть її ІМТ, поділивши вагу (кг) на зріст (м) у квадраті. Якщо це значення > 25, то людина має зайву вагу. Use the value `0` for NOT overweight and the value `1` for overweight.
- Normalize the data by making `0` always good and `1` always bad. If the value of `cholesterol` or `gluc` is `1`, make the value `0`. If the value is more than `1`, make the value `1`.
- Convert the data into long format and create a chart that shows the value counts of the categorical features using `seaborn`'s `catplot()`. The dataset should be split by `Cardio` so there is one chart for each `cardio` value. Діаграма повинна виглядати так: `examples/Figure_1.png`.
- Очистіть дані. Відфільтруйте наступні сегменти пацієнтів, які представляють неправильні дані:
  - діастолічний тиск вищий за систолічний (збережіть правильні дані за допомогою `(df['ap_lo'] <= df['ap_hi'])`)
  - зріст менший за 2,5-ий процентиль (збережіть правильні дані за допомогою `(df['height'] >= df['height'].quantile(0.025))`)
  - зріст більший за 97,5-ий процентиль
  - вага менша за 2,5-ий процентиль
  - вага більша ніж 97,5-ий процентиль
- Створіть кореляційну матрицю, використовуючи набір даних. Plot the correlation matrix using `seaborn`'s `heatmap()`. Замаскуйте верхній трикутник. Діаграма повинна виглядати так: `examples/Figure_2.png`.

Кожного разу, коли для змінної встановлено значення `None`, переконайтеся, що для неї встановлено правильний код.

Unit tests are written for you under `test_module.py`.

## Instructions
By each number in the `medical_data_visualizer.py` file, add the code from the associated instruction number below.

1. Import the data from `medical_examination.csv` and assign it to the `df` variable
2. Create the `overweight` column in the `df` variable
3. Normalize data by making `0` always good and `1` always bad. If the value of `cholesterol` or `gluc` is 1, set the value to `0`. If the value is more than `1`, set the value to `1`.
4. Draw the Categorical Plot in the `draw_cat_plot` function
5. Create a DataFrame for the cat plot using `pd.melt` with values from `cholesterol`, `gluc`, `smoke`, `alco`, `active`, and `overweight` in the `df_cat` variable.
6. Group and reformat the data in `df_cat` to split it by `cardio`. Show the counts of each feature. You will have to rename one of the columns for the `catplot` to work correctly.
7. Convert the data into `long` format and create a chart that shows the value counts of the categorical features using the following method provided by the seaborn library import : `sns.catplot()`
8. Get the figure for the output and store it in the `fig` variable
9. Do not modify the next two lines
10. Draw the Heat Map in the `draw_heat_map` function
11. Clean the data in the `df_heat` variable by filtering out the following patient segments that represent incorrect data:
    - height is less than the 2.5th percentile (Keep the correct data with `(df['height'] >= df['height'].quantile(0.025))`)
    - height is more than the 97.5th percentile
    - weight is less than the 2.5th percentile
    - weight is more than the 97.5th percentile
12. Calculate the correlation matrix and store it in the `corr` variable
13. Generate a mask for the upper triangle and store it in the `mask` variable
14. Set up the `matplotlib` figure
15. Plot the correlation matrix using the method provided by the `seaborn` library import: `sns.heatmap()`
16. Do not modify the next two lines

## Розробка

Напишіть свій код в `medical_data_visualizer.py`. Для розробки ви можете використати `main.py`, щоб протестувати свій код.

## Тестування

Модульні тести для цього проєкту знаходяться в `test_module.py`. Ми імпортували тести з `test_module.py` до `main.py` для вашої зручності.

## Надсилання

Скопіюйте URL-адресу свого проєкту та відправте її до freeCodeCamp.

# --hints--

Проєкт повинен пройти усі тести Python.

```js

```

# --solutions--

```py
  # Python challenges don't need solutions,
  # because they would need to be tested against a full working project.
  # Please check our contributing guidelines to learn more.
```
