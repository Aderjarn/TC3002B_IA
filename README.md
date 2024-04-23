# TC3002B_IA
Proyecto del Módulo 2, en este se realizará un modelo el cual se entrenará con imágenes del lenguaje de señas americano para que, el modelo pueda identificar que letra o gesto es.

### Preprocesamiento de dataset
Los datos utilizados para este proyecto son el dataset de [American  Sign Language](https://www.kaggle.com/datasets/kapillondhe/american-sign-language?select=ASL_Dataset), encontrado en kaggle, con licencia GPL 2.

Este dataset esta dividido en Train y en Test, la sección de Train cuenta con aprox **5600 imagenes** por clase y esta compuesto de **28 clases**, las cuales contienen 26 de letras, una de espacio y una donde no se encuentra ningun gesto. En el caso de la sección Test son **4 imagenes por clase**.

Para el funcionamiento adecuado del modelo a implementar, se seleccionaron **1000 imagenes por clase** para training y **250 por clase** para testing. Esto significa que la distribución del Dataset es de **80% a 20%**
El dataset ya modificado para su uso en este proyecto se encuentra en el siguiente [Google Drive](https://drive.google.com/drive/folders/12T7WFUGrXnJnKvZKeLaGCPVRHsZfRWJj?usp=sharing), en el mismo se pueden encontrar tecnicas de escalamiento aplicadas.

### Implementación de modelo
El modelo a implementar se baso en el articulo: ["Enhancing Arabic Sign Language Interpretation: Leveraging Convolutional Neural Networks and Transfer Learning"](https://www.mdpi.com/2227-7390/12/6/823#B21-mathematics-12-00823). En este articulo se detallan diferentes maneras de realizar modelos o algoritmos de aprendizaje para identificar las letras del lenguaje de señas arabe. Para este caso en particular se tomo como inspiración el preprocesamiento que se encuentra en el articulo y de manera más especifica para el modelo se utilizan tecnicas como dropout layer, en la red neuronal. Además se implemento una función early stopping al entrenamiento del modelo para asegurar que en caso de que este se empezara a desviar o no estuviera aprendiendo despues de cierto numero de epocas, el modelo se iba a parar, esto para así llegar a condiciones optimas del modelo y evitar overfitting principalmente.

Una vez entrenado el modelo se utilizaron métricas como accuracy, loss, una matriz de confusión.

Seleccionar métricas adecuadas respaldadas por un paper del estado del arte.
Reportar resultados obtenidos e interpretarlos

### Links de interés 
https://www.kaggle.com/datasets/kapillondhe/american-sign-language?select=ASL_Dataset
https://www.mdpi.com/2227-7390/12/6/823#B21-mathematics-12-00823
https://machinelearningmastery.com/early-stopping-to-avoid-overtraining-neural-network-models/
