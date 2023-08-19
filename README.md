# Emotionet
Desde los comienzos de la humanidad, las expresiones emocionales han emergido en los individuos para indicar funciones fisiológicas y comunicar comportamientos no verbales, con evidencia de que podrían ser de un carácter universal\cite{TRACY201525}. Su propósito es enviar mensajes como acercarse o evitar al que expresa, o algo en el entorno, la personalidad del que expresa, su rol social o los juicios de dominio. La ira, el asco, el miedo, la alegría, la tristeza y la sorpresa reservan un estatus especial en todo el espectro de las emociones humanas porque han sido estudiadas ampliamente a lo largo de la historia y la literatura científica. Por esto, proponemos ajustar finamente YOLO, con un conjunto de imágenes y sus emociones asociadas proporcionado por TRHEAD y sus herramientas descentralizadas con el fin de detectar emociones de manera justa para los usuarios. 

Descargamos las imágenes vía un directorio público en IPFS el cual nos proporciona el CID y la etiqueta asociada a cada imagen. Después de una exploración de datos en Python como se indica en la figura [1] y un preprocesamiento con Pandas (eliminar imagenes con ruido sustancial, redimensionar las imágenes a 640 y codificación entera) quedando 159 instancias (etiquetadas con triste 0, sorprendido 1, feliz 2 y enojado 3). Después de cumplir las especificaciones de Yolo8 proporcionado por ultralytics, ajustamos YOLO con nuestro dataset con el fin de detectar emociones en el rostro de la persona en la imagen. Para el entrenamiento usamos 100 épocas, con 5 k-folds con 80% para entrenamiento y 20% para validación.

![Figura 1: Distribución](https://github.com/sanchezcarlosjr/emotionnet/assets/24639141/b856765f-8771-413b-8bb3-1a14901f03ef)

Los resultados del modelo han sido altamente prometedores, logrando un F1-Score, una métrica que combina precisión y recuperación, de 90.0% [f1-score]. La curva Precision-Recall (usada por el imbalance en las clases), fue utilizada para evaluar la capacidad de clasificación del modelo en diferentes umbrales, mostró un área bajo la curva (AUC-PR) de 96.6% [precision-recall-curve], lo que subraya la robustez del modelo en la clasificación de las categorías. Estas métricas, en conjunto, demuestran la eficacia del modelo en la tarea para la que fue diseñado, aunque se observó una ligera tendencia al sobreajuste en las últimas épocas, lo que podría ser objeto de futuras investigaciones. Además podemos observar en la figura [matriz de confusión] la matriz de confusión normalizada. Puede encontrar el modelo en https://github.com/sanchezcarlosjr/emotionnet.

![f1-score](https://github.com/sanchezcarlosjr/emotionnet/assets/24639141/8320dd84-e1c7-44f4-b2d7-4441e3de0bfd)

![precision-recall-curve](https://github.com/sanchezcarlosjr/emotionnet/assets/24639141/3d262a47-369c-436d-8f0c-9b9f899f0804)

![matriz de confusión](https://github.com/sanchezcarlosjr/emotionnet/assets/24639141/4662c78d-41e5-4817-953a-84efdbb22fdb)

