# Изучение влияние параметра “темп обучения” на процесс обучения нейронной сети на примере решения задачи классификации Oregon Wildlife с использованием техники обучения Transfer Learning
# 1) С использованием [1] и техники обучения Transfer Learning обучить нейронную сеть EfficientNet-B0 (предварительно обученную на базе изображений imagenet) для решения задачи классификации изображений Oregon WildLife с использованием фиксированных темпов обучения 0.1, 0.01, 0.001, 0.0001
- Графики обучения: Только валидация

- Для метрики качества

 ![alt text](metrika2.jpg)
   
   График метрики качества
  ![SVG example](./metrika2.svg)
  
  - Для функции потерь
  
  ![alt text](loss2.jpg)
  
  График функции потерь
  ![SVG example](./loss2.svg)
  
  - При использовании шага обучения 0.001 достигается наилучшее качество на валидации равное 89,53%;


# 2) Реализовать и применить в обучении следующие политики изменения темпаобучения [2], а также определить оптимальные параметры для каждой политики: a. Пошаговое затухание (Step Decay) b. Экспоненциальное затухание (Exponential Decay)

# a. Step Decay
Графики обучения: Только валидация

- Для метрики качества

 ![alt text](exp_metrika.jpg)
   
   График метрики качества
  ![SVG example](./exp_metrika.svg)
  
  - Для функции потерь
  
  ![alt text](exp_loss.jpg)
  
  График функции потерь
  ![SVG example](./exp_loss.svg)

 - Лучшие параметры: начальное значение темпа обучения - 0.01 со снижением в 0.3 раза каждые 10 эпох. Эти параметр приводят к наивысшему значению метрики качества (89,17%), но это на 0,0036% меньше чем у алгоритма с оптимальным фиксированным темпом.
 
# b. Exponential Decay
Графики обучения: Только валидация

- Для метрики качества

 ![alt text](exp_metrika2.jpg)
   
   График метрики качества
  ![SVG example](./exp_metrika2.svg)
  
  -Для функции потерь
  
  ![alt text](exp_loss2.jpg)
  
  График функции потерь
  ![SVG example](./exp_loss2.svg)

 - Лучшие параметры: начальное значение темпа обучения - 0.01 с фактором наклона экспоненциальной кривой 0.3. Эти параметр приводят к наивысшему значению метрики качества (89,74%), и алгоритм превосходит алгоритм с оптимальным  фиксированным шагом  на 0,21%. Так же алгоритм быстрее сходится и значение функции потерь меньше на 0,0447.

# Финальные графики: Только валидация

- Для метрики качества

 ![alt text](final1.jpg)
   
   График метрики качества
  ![SVG example](./final1.svg)
  
  - Для функции потерь
  
  ![alt text](final2.jpg)
  
  График функции потерь
  ![SVG example](./final2.svg)

# Анализ результатов
- Оптимальные параметры для фиксированного темпа обучения = 0.001, метрика качества при таких параметрах равна 89,53%, функция потерь - 0.2766;
- Оптимальные параметры для  Step Decay: начальное значение темпа обучения - 0.01 со снижением в 0.3 раза каждые 10 эпох, метрика качества при таких параметрах равна 89,17%, что на 0,0036% меньше чем у алгоритма с оптимальным фиксированным темпом. Функция потерь равна 0.446, что на 0.1694 больше чем у алгоритма с оптимальным фиксированным темпом.
- Оптимальные параметры для Exponential Decay: начальное значение темпа обучения - 0.01 с фактором наклона экспоненциальной кривой 0.3,метрика качества при таких параметрах равна 89,74% , что на 0,21% больше чем у алгоритма с оптимальным фиксированным темпом.  Функция потерь равна 0.2319, что на 0.0447 меньше чем у алгоритма с оптимальным фиксированным темпом.
- Алгоритм Exponential Decay достиг предела сходимости уже на 20 эпохе.
- Можно сделать вывод, что из всех опробованных алгоритмов и параметров лучшим оказался алгоритм Exponential Decay, с параметрами:начальное значение темпа обучения - 0.01 с фактором наклона экспоненциальной кривой 0.3. C помощью него мы добились наилучшей метрики качества (89,74%, что на 0,21% больше чем у алгоритма с оптимальным фиксированным темпом ), наилучшей функции потерь (0.2319,что на 0.0447 меньше чем у алгоритма с оптимальным фиксированным темпом), а также быстрейшей сходимости(20 эпох).
