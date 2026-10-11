Sistema de Transporte de Tunja — Aprendizaje Supervisado 🚌📈

Actividad 3 — Métodos de aprendizaje supervisado Curso de Inteligencia Artificial

Introducción

En la actividad anterior se construyó un sistema de transporte urbano de Tunja basado en reglas fijas programadas a mano. En esta actividad se cambia el enfoque: en vez de decirle al sistema cómo decidir, se entrena un modelo de aprendizaje supervisado para que aprenda, a partir de datos de ejemplo, la relación entre las características de un viaje en bus y el tiempo que ese viaje toma.

No existe un dataset público con el nivel de detalle necesario (tiempo real de viaje por trayecto, clima, hora pico) para el transporte urbano de Tunja, así que el proyecto construye su propio dataset sintético de 350 viajes, generado dentro del mismo código, reutilizando como base de conocimiento los lugares y rutas reales del sistema. Sobre esos datos se entrena un modelo de regresión lineal (scikit-learn) que predice el tiempo de viaje en minutos.

Contenido del repositorio
├── sistema_aprendizaje_supervisado_tunja.py   # Código fuente: genera los datos y entrena el modelo
├── Descripcion_de_los_Datos_Actividad3.docx   # Documento: fuentes y descripción de los datos
├── Pruebas_Realizadas_Actividad3.docx         # Documento: metodología, métricas y resultados
├── grafica_regresion_real_vs_predicho.png     # Gráfica generada por el script
└── README.md
Cómo funciona el programa
Base de conocimiento: lista de lugares (LUGARES) y diccionario de rutas (RUTAS) del sistema de transporte de Tunja, con sus tiempos base.
Generación de datos: la función simular_viaje() calcula, para cada par de lugares, el número de paradas y la distancia del trayecto, y simula condiciones externas (hora pico, lluvia) que afectan el tiempo real del viaje. Con esto se generan 350 registros, almacenados en memoria como un arreglo de NumPy — no se usa ningún archivo CSV externo.
Entrenamiento: los datos se dividen en 80% entrenamiento / 20% prueba (train_test_split) y se entrena un modelo LinearRegression.
Evaluación: se calculan las métricas RMSE y R² sobre el conjunto de prueba.
Predicción e inferencia: se predicen tiempos para viajes nuevos no vistos por el modelo.
Visualización: se genera una gráfica de tiempo real vs. tiempo predicho.
Variables del modelo
Variable	Tipo	Descripción
num_paradas	Entero	Paradas recorridas en el trayecto
distancia_km	Decimal	Distancia aproximada del trayecto
hora_pico	Binaria (0/1)	Si el viaje ocurre en hora pico
lluvia	Binaria (0/1)	Si el viaje ocurre bajo lluvia
transbordo	Binaria (0/1)	Si el viaje requirió transbordo
tiempo_viaje_min	Decimal	Variable objetivo a predecir
Resultados obtenidos
Métrica	Valor
RMSE (error promedio)	3.82 minutos
R² (ajuste del modelo)	0.892

El modelo explica cerca del 89% de la variación del tiempo de viaje, con un error promedio de menos de 4 minutos sobre datos que no vio durante el entrenamiento.

Cómo ejecutarlo
bash
pip install numpy scikit-learn matplotlib
python sistema_aprendizaje_supervisado_tunja.py

El script imprime en consola los datos generados, los coeficientes del modelo, las métricas de evaluación y las predicciones para viajes nuevos, y abre una ventana con la gráfica de resultados.

Documentos incluidos
Descripcion_de_los_Datos_Actividad3.docx: por qué no existe una fuente de datos abierta para Tunja, cómo se construyó el dataset sintético paso a paso, y la descripción de cada variable.
Pruebas_Realizadas_Actividad3.docx: metodología de evaluación, métricas obtenidas, coeficientes del modelo y su interpretación.
Conclusiones
El modelo de regresión lineal logró un buen ajuste (R² = 0.892) porque los datos son sintéticos y siguen reglas conocidas; con datos reales del sistema de transporte, la relación sería más compleja y convendría explorar modelos no lineales (árboles de decisión, random forest).
Construir el dataset reutilizando la base de conocimiento de rutas y lugares permitió generar datos realistas y reproducibles sin depender de fuentes externas inexistentes.
Autores

Proyecto desarrollado en equipo de dos integrantes para el curso de Inteligencia Artificial — Actividad 3.Sistema de Transporte de Tunja — Aprendizaje Supervisado 🚌📈

Actividad 3 — Métodos de aprendizaje supervisado Curso de Inteligencia Artificial

Introducción

En la actividad anterior se construyó un sistema de transporte urbano de Tunja basado en reglas fijas programadas a mano. En esta actividad se cambia el enfoque: en vez de decirle al sistema cómo decidir, se entrena un modelo de aprendizaje supervisado para que aprenda, a partir de datos de ejemplo, la relación entre las características de un viaje en bus y el tiempo que ese viaje toma.

No existe un dataset público con el nivel de detalle necesario (tiempo real de viaje por trayecto, clima, hora pico) para el transporte urbano de Tunja, así que el proyecto construye su propio dataset sintético de 350 viajes, generado dentro del mismo código, reutilizando como base de conocimiento los lugares y rutas reales del sistema. Sobre esos datos se entrena un modelo de regresión lineal (scikit-learn) que predice el tiempo de viaje en minutos.

Contenido del repositorio
├── sistema_aprendizaje_supervisado_tunja.py   # Código fuente: genera los datos y entrena el modelo
├── Descripcion_de_los_Datos_Actividad3.docx   # Documento: fuentes y descripción de los datos
├── Pruebas_Realizadas_Actividad3.docx         # Documento: metodología, métricas y resultados
├── grafica_regresion_real_vs_predicho.png     # Gráfica generada por el script
└── README.md
Cómo funciona el programa
Base de conocimiento: lista de lugares (LUGARES) y diccionario de rutas (RUTAS) del sistema de transporte de Tunja, con sus tiempos base.
Generación de datos: la función simular_viaje() calcula, para cada par de lugares, el número de paradas y la distancia del trayecto, y simula condiciones externas (hora pico, lluvia) que afectan el tiempo real del viaje. Con esto se generan 350 registros, almacenados en memoria como un arreglo de NumPy — no se usa ningún archivo CSV externo.
Entrenamiento: los datos se dividen en 80% entrenamiento / 20% prueba (train_test_split) y se entrena un modelo LinearRegression.
Evaluación: se calculan las métricas RMSE y R² sobre el conjunto de prueba.
Predicción e inferencia: se predicen tiempos para viajes nuevos no vistos por el modelo.
Visualización: se genera una gráfica de tiempo real vs. tiempo predicho.
Variables del modelo
Variable	Tipo	Descripción
num_paradas	Entero	Paradas recorridas en el trayecto
distancia_km	Decimal	Distancia aproximada del trayecto
hora_pico	Binaria (0/1)	Si el viaje ocurre en hora pico
lluvia	Binaria (0/1)	Si el viaje ocurre bajo lluvia
transbordo	Binaria (0/1)	Si el viaje requirió transbordo
tiempo_viaje_min	Decimal	Variable objetivo a predecir
Resultados obtenidos
Métrica	Valor
RMSE (error promedio)	3.82 minutos
R² (ajuste del modelo)	0.892

El modelo explica cerca del 89% de la variación del tiempo de viaje, con un error promedio de menos de 4 minutos sobre datos que no vio durante el entrenamiento.

Cómo ejecutarlo
bash
pip install numpy scikit-learn matplotlib
python sistema_aprendizaje_supervisado_tunja.py

El script imprime en consola los datos generados, los coeficientes del modelo, las métricas de evaluación y las predicciones para viajes nuevos, y abre una ventana con la gráfica de resultados.

Documentos incluidos
Descripcion_de_los_Datos_Actividad3.docx: por qué no existe una fuente de datos abierta para Tunja, cómo se construyó el dataset sintético paso a paso, y la descripción de cada variable.
Pruebas_Realizadas_Actividad3.docx: metodología de evaluación, métricas obtenidas, coeficientes del modelo y su interpretación.
Conclusiones
El modelo de regresión lineal logró un buen ajuste (R² = 0.892) porque los datos son sintéticos y siguen reglas conocidas; con datos reales del sistema de transporte, la relación sería más compleja y convendría explorar modelos no lineales (árboles de decisión, random forest).
Construir el dataset reutilizando la base de conocimiento de rutas y lugares permitió generar datos realistas y reproducibles sin depender de fuentes externas inexistentes.
Autores
Natalia Espinosa y Eduard Gonzalez
