# mcd_deep_learning
# Generador de Cuentos Infantiles con LSTM

Presentación del proyecto final de la materia de principios de aprendizaje profundo de la maestría en ciencia de datos de la Universidad Panamericana

## Descripción del proyecto

Este proyecto implementa un modelo de **Red Neuronal Recurrente** (RNN) utilizando **LSTM** para la generación de cuentos infantiles. El modelo está entrenado en un corpus de cuentos infantiles de dominio público, y puede generar nuevas historias basadas en una secuencia inicial proporcionada por el usuario. El proyecto se divide en tres etapas: preprocesamiento del texto, entrenamiento del modelo, y generación de texto.

## Archivos del Repositorio

Este repositorio contiene los siguientes archivos y carpetas:

### 1. **Notebooks**
   - [**`CharsParaCuentos_AdrianaMartinez.ipynb`**](mcd_deep_learning/CharsParaCuentos_AdrianaMartinez.ipynb): Notebook que contiene el código para el preprocesamiento del texto. Convierte el corpus de cuentos infantiles en un conjunto de caracteres únicos y genera los diccionarios necesarios para codificar el texto.
   - **`Entrenamiento_GeneradordeCuentos_AdrianaMartinez.ipynb`**: Notebook para el entrenamiento del modelo LSTM. Entrena el modelo en el corpus procesado y genera versiones del modelo entrenado con diferentes números de épocas.
   - **`GeneradorDeCuentos_AdrianaMartinez.ipynb`**: Notebook para generar nuevos cuentos. Carga los modelos entrenados y permite generar secuencias de texto a partir de una secuencia inicial.

### 2. **Cuentos de Entrenamiento**
   - **`cleaned_merged_fairy_tales_without_eos.txt`**: Archivo que contiene el corpus de cuentos infantiles utilizados para entrenar el modelo. Estos cuentos son de dominio público y fueron limpiados previamente para ser adecuados para el entrenamiento.

### 3. **Carpeta `chars/`**: Contiene los archivos generados durante el preprocesamiento del texto:
   - **`chars60.pkl`**: Archivo que contiene el conjunto de caracteres únicos extraídos del texto.
   - **`char2int60.pkl`**: Diccionario que mapea cada carácter a un número entero.
   - **`int2char60.pkl`**: Diccionario que mapea números enteros a caracteres.
   - **`encoded60.pkl`**: Archivo omitido debido a su tamaño, que contiene el texto codificado como una secuencia de enteros.

### 4. **Carpeta `models/`**: Contiene los modelos LSTM entrenados exportados en formato `.pth` para diferentes números de épocas:
   - **`lstm_cuentos_infantiles_1epoch.pth`**: Modelo entrenado durante 1 época.
   - **`lstm_cuentos_infantiles_60epoch.pth`**: Modelo entrenado durante 60 épocas.
   - **`lstm_cuentos_infantiles_150epoch.pth`**: Modelo entrenado durante 150 épocas.

### 5. **`requirements.txt`**: Archivo que contiene las dependencias necesarias para ejecutar los notebooks. Incluye librerías como PyTorch, NumPy y Matplotlib.

## Dataset: Cuentos Infantiles

El dataset utilizado para entrenar el modelo está compuesto por cuentos infantiles extraídos del **Proyecto Gutenberg**. El archivo **`cleaned_merged_fairy_tales_without_eos.txt`** contiene estos cuentos, los cuales han sido preprocesados para eliminar información no deseada como metadatos y caracteres ofensivos.

### Características del dataset:
- **Formato**: Texto plano.
- **Limpieza del texto**: El texto ha sido limpiado para remover ilustraciones, metadatos y cualquier otro contenido no adecuado para el modelo.
- **Idioma**: Inglés.
- **Uso del dataset**: El conjunto de cuentos es utilizado para preprocesar el texto, transformando cada carácter en un índice entero para que el modelo LSTM pueda aprender a predecir la siguiente secuencia de caracteres.

## Descripción del Proyecto

### 1. **Preprocesamiento del Texto**
   El archivo **`CharsParaCuentos_AdrianaMartinez.ipynb`** contiene el código para el preprocesamiento del texto. Este paso incluye:
   - Extraer los caracteres únicos del corpus de cuentos.
   - Crear los diccionarios que mapean caracteres a índices enteros y viceversa.
   - Codificar el texto completo como una secuencia de enteros para que el modelo LSTM pueda procesarlo.

### 2. **Entrenamiento del Modelo**
   El archivo **`Entrenamiento_GeneradordeCuentos_AdrianaMartinez.ipynb`** contiene el código para entrenar el modelo LSTM. El modelo es entrenado utilizando diferentes cantidades de épocas (1, 10, 60, 150 y 180), y los resultados se guardan en la carpeta `models/`. El entrenamiento incluye:
   - Definición de un modelo LSTM con dos capas ocultas y 512 unidades en cada capa.
   - Uso del optimizador **Adam** y la función de pérdida **CrossEntropyLoss**.
   - Generación de modelos entrenados en diferentes etapas del entrenamiento, los cuales pueden ser utilizados para generar texto posteriormente.

### 3. **Generación de Texto**
   El archivo **`GeneradorDeCuentos_AdrianaMartinez.ipynb`** permite al usuario cargar cualquiera de los modelos entrenados y generar nuevas secuencias de texto basadas en una secuencia inicial proporcionada. El modelo predice el siguiente carácter en la secuencia y continúa generando hasta la longitud deseada.

## Requisitos

Para ejecutar los notebooks de este proyecto, necesitas instalar las siguientes dependencias. Puedes instalarlas utilizando el archivo `requirements.txt`:

```bash
pip install -r requirements.txt
```

### Principales dependencias:
- **PyTorch**: Para construir, entrenar y evaluar el modelo LSTM.
- **NumPy**: Para la manipulación de arrays.
- **Matplotlib**: Para graficar el valor de pérdida durante el entrenamiento.
- **Pickle**: Para cargar y guardar los archivos procesados.

## Cómo Usar Este Proyecto

1. **Preprocesamiento del Texto**:
   - Ejecuta el notebook **`CharsParaCuentos_AdrianaMartinez.ipynb`** para preprocesar el texto y generar los diccionarios de mapeo. Los archivos generados se guardarán en la carpeta `chars/`.

2. **Entrenamiento del Modelo**:
   - Ejecuta el notebook **`Entrenamiento_GeneradordeCuentos_AdrianaMartinez.ipynb`** para entrenar el modelo. Puedes ajustar el número de épocas y otros parámetros según sea necesario. Los modelos entrenados se guardarán en la carpeta `models/`.

3. **Generación de Texto**:
   - Usa el notebook **`GeneradorDeCuentos_AdrianaMartinez.ipynb`** para cargar cualquiera de los modelos entrenados y generar nuevas secuencias de texto. También se puede correr exclusivamente	este notebook para hacer pruebas sobre los modelos generados sin la necesidad de correr los dos anteriores

## Contribuciones

Si deseas contribuir a este proyecto, eres bienvenido/a. Puedes realizar un fork del repositorio y enviar tus propuestas a través de **pull requests**.

## Licencia

Este proyecto se distribuye bajo la licencia MIT. Para más detalles, consulta el archivo `LICENSE`.
