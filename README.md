# TC3002B_IA
Proyecto del Módulo 2, en este se realizará un modelo el cual se entrenará con imágenes del lenguaje de señas americano para que, el modelo pueda identificar que letra o gesto es.

## Señección de dataset
Los datos utilizados para este proyecto son el dataset de [American  Sign Language](https://www.kaggle.com/datasets/kapillondhe/american-sign-language?select=ASL_Dataset), encontrado en kaggle, con licencia GPL 2. Este dataset esta dividido en Train y en Test, la sección de Train cuenta con aprox **5600 imagenes** por clase y esta compuesto de **28 clases**, las cuales contienen 26 de letras, una de espacio y una donde no se encuentra ningun gesto. En el caso de la sección Test son **4 imagenes por clase**.
Para el funcionamiento adecuado del modelo a implementar, se seleccionaron **1000 imagenes por clase** para training y **250 por clase** para testing. Esto significa que la distribución del Dataset es de **80% a 20%**. El dataset ya modificado para su uso en este proyecto se encuentra en el siguiente [Google Drive](https://drive.google.com/drive/folders/12T7WFUGrXnJnKvZKeLaGCPVRHsZfRWJj?usp=sharing), en el mismo se pueden encontrar tecnicas de escalamiento aplicadas.

## Preprocesamiento de dataset
Antes de empezar a implementar y entrenar un modelo al dataset se le aplicaron varias aumentaciones, para así facilitar el trabajo raelizado en la implementación del modelo en si. Dicho preprocesamiento tomo como base el propuesto en el siguiente articulo: ["Enhancing Arabic Sign Language Interpretation: Leveraging Convolutional Neural Networks and Transfer Learning"](https://www.mdpi.com/2710280). El preprocesado o aumentos aplicados a las imagenes a utilizar para Train son los siguientes: 
- rescale=1./255 
- rotation_range=30                                     
- width_shift_range=0.1
- height_shift_range=0.1
- shear_range=0.1
- zoom_range=0.1
- horizontal_flip=True
- preprocessing_function=tf.image.rgb_to_grayscale
- validation_split=0.2
  
Cómo se puede observar en el ultimo punto, se hizo una división de 80% - 20% en las imagenes en Train para así contar con una validación previa a Test. Ademas para tener una aprendizaje mas controlado se aplicaron los siguiente puntes a Train y Validation.
- target_size = (64, 64)
- batch_size = 64
- class_mode='sparse'
- subset='training'
- classes=class_names
- shuffle=True
- seed=42

En esto observamos que se aplico un cambio en el tamaño de las imagenes, el loss del modelo que en esta caso sera utilizando sparce_categorical_crossentropy, un shuffle para prevenir que el modelo aprenda con algun tipo de bias y finalmente un seed para asegurar que el modelo reproduzca resultados de similares de una manera constante. 

## Implementación de modelo
El modelo a implementar se baso en el articulo: ["Enhancing Arabic Sign Language Interpretation: Leveraging Convolutional Neural Networks and Transfer Learning"](https://www.mdpi.com/2710280). En este articulo se detallan diferentes maneras de realizar modelos o algoritmos de aprendizaje para identificar las letras del lenguaje de señas arabe. Para este caso en particular se tomaron tecnicas como dropout layer, en la red neuronal. Además se implemento una función early stopping al entrenamiento del modelo para asegurar que en caso de que este se empezara a desviar o no estuviera aprendiendo despues de cierto numero de epocas, el modelo se iba a parar, esto para así llegar a condiciones optimas del modelo y evitar overfitting principalmente.

Una vez entrenado el modelo se utilizaron métricas como accuracy, loss, matriz de confusión. dichas se pueden ver a continuación: 
![Training and Validation Accuracy](https://github.com/Aderjarn/TC3002B_IA/assets/55771964/8669ef1d-a976-4479-8e46-8127e939669f)


## Bibliografía 
Kaggle American  Sign Language: https://www.kaggle.com/datasets/kapillondhe/american-sign-language?select=ASL_Dataset
Enhancing Arabic Sign Language Interpretation: Leveraging Convolutional Neural Networks and Transfer Learning: https://www.mdpi.com/2710280
Sparse Categorical Cross-Entropy vs Categorical Cross-Entropy: https://fmorenovr.medium.com/sparse-categorical-cross-entropy-vs-categorical-cross-entropy-ea01d0392d28
How is the data shuffled in the preprocessing step and why is it important?: https://eitca.org/artificial-intelligence/eitc-ai-dltf-deep-learning-with-tensorflow/tensorflow/preprocessing-conitnued/examination-review-preprocessing-conitnued/how-is-the-data-shuffled-in-the-preprocessing-step-and-why-is-it-important/#:~:text=Shuffling%20the%20data%20in%20the,and%20addresses%20class%20imbalance%20issues.
How to Use Random Seeds Effectively: https://towardsdatascience.com/how-to-use-random-seeds-effectively-54a4cd855a79#:~:text=A%20random%20seed%20is%20used,data%20science%20and%20other%20fields.
A Gentle Introduction to Early Stopping to Avoid Overtraining Neural Networks: https://machinelearningmastery.com/early-stopping-to-avoid-overtraining-neural-network-models/


