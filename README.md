# TC3002B_IA
Proyecto del Módulo 2, en este se realizará un modelo el cual se entrenará con imágenes del lenguaje de señas americano para que, el modelo pueda identificar que letra o gesto es.

### Preprocesamiento de dataset
Los datos utilizados para este proyecto son el dataset de [American  Sign Language](https://www.kaggle.com/datasets/kapillondhe/american-sign-language?select=ASL_Dataset), encontrado en kaggle, con licencia GPL 2.

Este dataset esta dividido en Train y en Test, la sección de Train cuenta con aprox 5600 imagenes por clase y esta compuesto de 28 clases, las cuales contienen 26 de letras, una de espacio y una donde no se encuentra ningun gesto. En el caso de la sección Test son 4 imagenes para cada clase.

Para el funcionamiento adecuado del modelo a implementar, se seleccionaron 1000 imagenes por clase para training y 150 por clase para testing.
El dataset ya modificado para su uso en este proyecto se encuentra en el siguiente [Google Drive](https://drive.google.com/drive/folders/12T7WFUGrXnJnKvZKeLaGCPVRHsZfRWJj?usp=sharing), en el mismo se pueden encontrar tecnicas de escalamiento aplicadas.
