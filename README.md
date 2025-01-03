# Лабораторная работа 6. Семантическая сегментация

Для данной работы необходимо скачать архив с датасетом по ссылке: https://disk.yandex.ru/d/-Rvv2UQlHVL04w

Выполнение работы дает 15 баллов независимо от итогового mIoU на тестовой выборке, но mIoU более 0.6 дает дополнительно еще 5 баллов

Возможные вопросы от преподавателя на защите:
1. Что такое семантическая сегментация?
2. Каковы особенности архитектуры нейронных сетей для семантической сегментации?
3. Как работает свертка?
4. Можно ли использовать трансформерные архитектуры для семантической сегментации и в чем будут состоять ограничения для их использования?
5. Какая метрика используется для оценки качества таких моделей и как она вычисляется?

Ответы на вопросы:
Что такое семантическая сегментация?
Семантическая сегментация — это задача в области компьютерного зрения, которая предполагает классификацию каждого пикселя изображения в соответствии с определенным классом. Результатом является карта сегментов, где все пиксели одного класса объединены в единую область. Это используется, например, для анализа дорожных сцен, медицинских изображений и картографии.

Каковы особенности архитектуры нейронных сетей для семантической сегментации?
Архитектуры обычно состоят из энкодера и декодера. Энкодер извлекает пространственные и контекстные признаки, уменьшая размерность данных (например, через свертки и пулинг). Декодер восстанавливает пространственное разрешение до исходного изображения, используя транспонированные свертки или операции upsampling. Для сохранения мелких деталей популярны архитектуры с пропусками (skip-connections), как в U-Net. Современные подходы также могут использовать модуль внимания (attention) для учета глобального контекста.

Как работает свертка?
Свертка — это базовая операция в сверточных нейронных сетях. Ядро (фильтр) скользит по входному изображению, и на каждом шаге вычисляется сумма произведений значений пикселей и элементов фильтра. Это позволяет выделять локальные признаки, такие как края, текстуры или формы. Свертки эффективно уменьшают размерность данных, сохраняя важные признаки.

Можно ли использовать трансформерные архитектуры для семантической сегментации и в чем будут состоять ограничения для их использования?
Да, трансформеры, такие как Vision Transformers (ViT) и их адаптации (например, SegFormer), активно используются. Они хорошо работают за счет учета глобального контекста, поскольку основаны на механизме внимания, который учитывает взаимосвязи между всеми элементами изображения. Однако их основные ограничения — высокая вычислительная сложность, особенно на больших изображениях, и потребность в большом количестве данных для эффективного обучения. Без адаптации они могут хуже справляться с мелкими деталями.

Какая метрика используется для оценки качества таких моделей и как она вычисляется?
Наиболее популярная метрика — IoU (Intersection over Union). Она измеряет пересечение предсказанной и истинной областей для каждого класса, деля его на их объединение. Итоговый показатель может быть усреднен по всем классам (mIoU). Это наглядно показывает, насколько точно модель сегментирует области, и помогает выявлять, где она ошибается.
