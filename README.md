# TC3002B_IA
Proyecto del Módulo 2, en este se realizará un modelo el cual se entrenará con imágenes del lenguaje de señas americano para que, el modelo pueda identificar que letra o gesto es.

### Preprocesamiento de datos
Los datos utilizados para este proyecto son el dataset de American  Sign Language, encontrado en kaggle. Dicho dataset se encuentra en la siguiente liga: https://www.kaggle.com/datasets/kapillondhe/american-sign-language?select=ASL_Dataset, con licencia GPL 2.

Este dataset esta dividido en Train y en Test, la sección de Train cuenta con aprox 5600 imagenes por clase y esta compuesto de 28 clases, las cuales contienen 26 de letras, una de espacio y una donde no se encuentra ningun gesto. En el caso de la sección Test son 4 imagenes para cada clase.
De dicho dataset se utilizaran 1000 imagenes para el Train que se realizara y se aumentara la cantidad de imagenes de la sección Test a 150 para cada clase. 
El dataset ya modificado para su uso en este proyecto se encuentra en el siguiente Google drive, en el mismo se pueden encontrar tecnicas de escalamiento aplicadas: https://drive.google.com/drive/folders/12T7WFUGrXnJnKvZKeLaGCPVRHsZfRWJj?usp=sharing
