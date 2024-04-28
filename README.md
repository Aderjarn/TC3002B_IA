# TC3002B_IA
Proyecto del Módulo 2, en este se realizará un modelo el cual se entrenará con imágenes del lenguaje de señas americano para que, el modelo pueda identificar que letra o gesto es.

## Selección de dataset
Los datos utilizados para este proyecto son el dataset de [American  Sign Language](https://www.kaggle.com/datasets/kapillondhe/american-sign-language?select=ASL_Dataset), encontrado en kaggle, con licencia GPL 2. Este dataset está dividido en Train y en Test, la sección de Train cuenta con aprox 5600 imágenes por clase y está compuesto de 28 clases, las cuales contienen 26 de letras, una de espacio y una donde no se encuentra ningún gesto. En el caso de la sección Test son 4 imágenes por clase. Para el funcionamiento adecuado del modelo a implementar, se seleccionaron 1000 imágenes por clase para training y 250 por clase para testing. Esto significa que la distribución del Dataset es de 80% a 20%. El dataset ya modificado para su uso en este proyecto se encuentra en el siguiente [Google Drive](https://drive.google.com/drive/folders/12T7WFUGrXnJnKvZKeLaGCPVRHsZfRWJj?usp=sharing), en el mismo se pueden encontrar técnicas de escalamiento aplicadas.

## Preprocesamiento de dataset
Antes de empezar a implementar y entrenar un modelo al dataset se le aplicaron varias aumentaciones, para así facilitar el trabajo realizado en la implementación del modelo en sí. Dicho preprocesamiento tomó como base el propuesto en el siguiente artículo: ["Enhancing Arabic Sign Language Interpretation: Leveraging Convolutional Neural Networks and Transfer Learning"](https://www.mdpi.com/2710280). El preprocesado o aumentos aplicados a las imágenes a utilizar para Train son los siguientes:

rescale=1./255
rotation_range=30
width_shift_range=0.1
height_shift_range=0.1
shear_range=0.1
zoom_range=0.1
horizontal_flip=True
preprocessing_function=tf.image.rgb_to_grayscale
validation_split=0.2
Cómo se puede observar en el último punto, se hizo una división de 80% - 20% en las imágenes en Train para así contar con una validación previa a Test. Además para tener una aprendizaje más controlado se aplicaron los siguiente puntes a Train y Validation.

target_size = (64, 64)
batch_size = 64
class_mode='sparse'
subset='training'
classes=class_names
shuffle=True
seed=42
En esto observamos que se aplicó un cambio en el tamaño de las imágenes, el loss del modelo que en esta caso será utilizando sparce_categorical_crossentropy, un shuffle para prevenir que el modelo aprenda con algún tipo de bias y finalmente un seed para asegurar que el modelo reproduzca resultados de similares de una manera constante.

## Implementación de modelo
El trabajo realizado en este apartado se encuentra en la carpeta BaseASLModel. El modelo a implementar se basó en el artículo:["Enhancing Arabic Sign Language Interpretation: Leveraging Convolutional Neural Networks and Transfer Learning"](https://www.mdpi.com/2710280). En este artículo se detallan diferentes maneras de realizar modelos o algoritmos de aprendizaje para identificar las letras del lenguaje de señas arabe. Para este caso en particular se tomaron técnicas como cnn, max pooling, dropout layer, en la red neuronal. Además se implementó una función early stopping al entrenamiento del modelo para asegurar que en caso de que este se empezará a desviar o no estuviera aprendiendo después de cierto número de épocas, el modelo se iba a parar, esto para así llegar a condiciones óptimas del modelo y evitar overfitting principalmente.

Una vez entrenado el modelo se utilizaron métricas como accuracy y loss, para evaluar su desempeño Train y Validation y así conocer si el modelo se encontraba en un estado de Underfitting u Overfitting. Dichas métricas se pueden ver graficadas a continuación:
 
![Accuracy and Validation Acurracy and Loss](https://github.com/Aderjarn/TC3002B_IA/assets/55771964/f1e2c88d-a32a-46c5-9878-c87f085e7df6)

Posteriormente se guardo el modelo, para utilizarlo en un archivo separado con los datos dentro de Test. En dicha fase se obtuvo la siguiente matriz de confusión con las predicciones que se hicieron basandose en el modelo y una tabla con una predicción por clase. En esta parte el modelo obtuvo un accuracy del 96%.
![Confusion Matrix](https://github.com/Aderjarn/TC3002B_IA/assets/55771964/9ece29d1-995a-45ce-b7fb-ebcd6289b2e9)

![Predictions per class](https://github.com/Aderjarn/TC3002B_IA/assets/55771964/b18d5c2a-7921-4273-b806-df889dda5ab4)


## Bibliografía 
Kaggle American  Sign Language: https://www.kaggle.com/datasets/kapillondhe/american-sign-language?select=ASL_Dataset
Enhancing Arabic Sign Language Interpretation: Leveraging Convolutional Neural Networks and Transfer Learning: https://www.mdpi.com/2710280
Sparse Categorical Cross-Entropy vs Categorical Cross-Entropy: https://fmorenovr.medium.com/sparse-categorical-cross-entropy-vs-categorical-cross-entropy-ea01d0392d28
How is the data shuffled in the preprocessing step and why is it important?: https://eitca.org/artificial-intelligence/eitc-ai-dltf-deep-learning-with-tensorflow/tensorflow/preprocessing-conitnued/examination-review-preprocessing-conitnued/how-is-the-data-shuffled-in-the-preprocessing-step-and-why-is-it-important/#:~:text=Shuffling%20the%20data%20in%20the,and%20addresses%20class%20imbalance%20issues.
How to Use Random Seeds Effectively: https://towardsdatascience.com/how-to-use-random-seeds-effectively-54a4cd855a79#:~:text=A%20random%20seed%20is%20used,data%20science%20and%20other%20fields.
A Gentle Introduction to Early Stopping to Avoid Overtraining Neural Networks: https://machinelearningmastery.com/early-stopping-to-avoid-overtraining-neural-network-models/


