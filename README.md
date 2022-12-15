# DL_LAB_2022
For labs 
В данной работе реализован оптимизатор AdaSmooth и архитектура нейроннай сети Inception_v3 с использованием pytourch. Также были реализованны некоторые операции сверток на библиотеке numpy. Было проведено сравнение реализованного оптимизатора AdaSmooth с оптимизатором Adam. 
#Архитектура Inception_v3
Чтобы разобрать особенности 3 версии данной архитектуры необходимо также разобрать предыдущие версии архитектуры. 
Основная идея Inception_v1 содержится в паралельных свертках в пределах 1 блока (рис. 1). 
![image](https://user-images.githubusercontent.com/58116790/207856380-8f6698f1-eb82-403d-9870-454fc56f43fa.png)
Это позволяет лучше подбрать необходимые фильтры и операнды для достижения максимального качества. Затем этот блок оптимизировали добавив свертки 1x1 что позволяет уменьшить размеры сети параметров. 
![image](https://user-images.githubusercontent.com/58116790/207857342-75f25e90-a011-48f9-ab77-98edc1756639.png)
Дальнейшая эволюция Inception двигалась в сторону оптимизации работы модели. Для этого вместо сверток с большим ядром использовались множество малных (например заменялась свертка 5x5 на 2 3x3). 
![image](https://user-images.githubusercontent.com/58116790/207858097-be25dbfd-3fff-46a4-b6de-b9e59faba08a.png)
Затем стали применять ассимитричные свертки (3x3 заменяют на 1x3 и 3x1). 
![image](https://user-images.githubusercontent.com/58116790/207858326-2aea19e5-ad17-4af3-be0d-483c397aa918.png)
Кроме того стали использоваться вспомогательные классификаторы. Они представляют собой дополнительные более рание "выходы" которые позволяют бороться с проблемой угасающего градиента. 
Отличием 2 и 3 версия является использование нормализации в финальных линейных слоях. В целом итоговая архитектура выглядит так:
![image](https://user-images.githubusercontent.com/58116790/207860818-f725d5cc-8387-4c05-b66d-740e843c7617.png)
#Оптимизаторы
Adam — один из самых эффективных алгоритмов оптимизации в обучении нейронных сетей. Он сочетает в себе идеи RMSProp и оптимизатора импульса. Вместо того чтобы адаптировать скорость обучения параметров на основе среднего первого момента (среднего значения), как в RMSProp, Adam также использует среднее значение вторых моментов градиентов.
https://habrastorage.org/webt/7p/jc/io/7pjcio1qukwjemezhhmznme7zre.gif
AdaSmooth - это новый оптмизатор который как утверждают авторы нечуствительный к гиперпараметрам что снимает необходимость их подбора. Он основан на AdaGrad однако авторы поставили себе цель удалить 2 его недостатка: убрать необходимость выбора гипер параметров и учитывания только обсолютного значения градиентов. В результате у авторов получилось создать более точный и быстрый оптимизтор. 
![image](https://user-images.githubusercontent.com/58116790/207866415-67e1dd84-3cf8-435c-8e3a-3e6776f1bc0c.png)

#Результаты 
На следующих графиках показано сравнение результов функции ошибки от эпохи
AdaSmooth:

![Chart](https://user-images.githubusercontent.com/58116790/207869149-6c8ebd57-ac36-4591-a939-eb4b632f8c5d.png)

Adam:

![Chart](https://user-images.githubusercontent.com/58116790/207871291-334ebb6e-2618-458e-901a-e3c03b4f7186.jpg)

На следующих графиков показано сравнение точности от номера эпохи:
AdaSmooth:

![Chart (1)](https://user-images.githubusercontent.com/58116790/207871354-fd4cdca8-32b3-4ca0-a937-51358007bb28.jpg)

Adam:

![Chart (2)](https://user-images.githubusercontent.com/58116790/207871407-11eb8ac6-a5e2-426e-aac6-94d7baaf1e29.jpg)




