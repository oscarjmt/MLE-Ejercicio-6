# Ejercicio 6: Machine Learning con GitHub Actions

## Descripción del Proyecto

Este repositorio contiene el Ejercicio 6, que se centra en la aplicación de prácticas de Machine Learning utilizando GitHub Actions. El objetivo principal es automatizar los procesos de entrenamiento, evaluación y producción de modelos de machine learning, continuando con el trabajo realizado en ejercicios anteriores.

## Objetivo

El propósito de este ejercicio es integrar nuestros conocimientos previos de machine learning con las capacidades de integración continua que ofrece GitHub Actions. Esto nos permite:

1. Automatizar el entrenamiento de modelos cuando se actualizan los datos de entrenamiento.
2. Automatizar la ejecución del modelo en producción cuando se actualizan los datos de prueba.
3. Mantener nuestros modelos y resultados siempre actualizados en el repositorio.
4. Facilitar la colaboración y el seguimiento de cambios en nuestros modelos y datos.

## Procesos

Este ejercicio implementa dos flujos de trabajo principales:

### 1. Flujo de Trabajo de Entrenamiento

Este flujo se activa cuando hay cambios en `data/train.csv`:

1. **Detección de Cambios**: GitHub Actions se activa automáticamente cuando se realiza un push que modifica el archivo `data/train.csv`.
2. **Preparación del Entorno**: Se configura un entorno Python con las dependencias necesarias.
3. **Entrenamiento del Modelo**: Se ejecuta el script `script_train.py`.
4. **Almacenamiento de Resultados**: Los modelos entrenados y los informes de clasificación se guardan en el repositorio.
5. **Actualización Automática**: GitHub Actions se encarga de commit y push de los cambios generados.

### 2. Flujo de Trabajo de Producción

Este flujo se activa cuando hay cambios en `data/test.csv`:

1. **Detección de Cambios**: GitHub Actions se activa cuando se modifica el archivo `data/test.csv`.
2. **Preparación del Entorno**: Similar al flujo de entrenamiento.
3. **Ejecución en Producción**: Se ejecuta el script `script_prod.py`.
4. **Actualización de Resultados**: Los resultados de la ejecución en producción se guardan y se hace commit al repositorio.

## Estructura del Repositorio

- `/data`: Contiene los datos de entrenamiento (`train.csv`) y prueba (`test.csv`).
- `/modelos`: Almacena los modelos entrenados.
- `/resultados`: Guarda los informes de clasificación y resultados de producción.
- `script_train.py`: Script principal para el entrenamiento del modelo.
- `script_prod.py`: Script para la ejecución del modelo en producción.
- `.github/workflows/`:
  - `train_script.yml`: Configuración del workflow de entrenamiento.
  - `prod_script.yml`: Configuración del workflow de producción.

## Cómo Utilizar

1. Clona este repositorio.
2. Para activar el flujo de entrenamiento:
   - Actualiza el archivo `data/train.csv` con nuevos datos si es necesario.
   - Realiza un push de los cambios a GitHub.
3. Para activar el flujo de producción:
   - Actualiza el archivo `data/test.csv` con nuevos datos de prueba.
   - Realiza un push de los cambios a GitHub.
4. GitHub Actions se encargará automáticamente de ejecutar los scripts correspondientes y actualizar los resultados.

## Nota Importante

Este proyecto utiliza un Personal Access Token (PAT) para autenticar las acciones de GitHub. Asegúrate de configurar correctamente el PAT en los secretos del repositorio con el nombre `GH_PAT` para que ambos workflows funcionen adecuadamente.

## Reflexión: Integración de CI/CD en Proyectos de Machine Learning

La integración de herramientas de Integración Continua y Entrega Continua (CI/CD) en proyectos de Machine Learning representa un avance significativo en la forma en que desarrollamos, desplegamos y mantenemos modelos de ML. Esta integración ofrece varios beneficios clave:

1. **Automatización del Flujo de Trabajo**: 
   - CI/CD permite automatizar tareas repetitivas como el entrenamiento de modelos, pruebas y despliegue, ahorrando tiempo y reduciendo errores humanos.
   - En nuestro proyecto, GitHub Actions automatiza el proceso de entrenamiento y producción, activándose con cambios en los datos.

2. **Reproducibilidad**:
   - Las herramientas de CI/CD ayudan a mantener un entorno consistente y documentado, crucial para la reproducibilidad en ML.
   - Nuestro uso de requirements.txt y entornos Python específicos en los workflows asegura esta consistencia.

3. **Versionado y Trazabilidad**:
   - CI/CD facilita el versionado no solo del código, sino también de los modelos y datos.
   - En nuestro caso, cada ejecución de GitHub Actions crea un nuevo commit, permitiendo rastrear cambios en modelos y resultados.

4. **Pruebas Continuas**:
   - Permite la ejecución automática de conjuntos de pruebas cada vez que se realizan cambios, asegurando la calidad del modelo.
   - Aunque no está implementado explícitamente en este ejercicio, podríamos fácilmente añadir pasos de prueba en nuestros workflows.

5. **Despliegue Continuo**:
   - Facilita el despliegue rápido y seguro de nuevos modelos en producción.
   - Nuestro workflow de producción es un ejemplo simplificado de cómo podría funcionar un despliegue automatizado.

6. **Colaboración Mejorada**:
   - CI/CD proporciona un flujo de trabajo estandarizado que mejora la colaboración entre científicos de datos, ingenieros de ML y otros miembros del equipo.
   - El uso de GitHub Actions en nuestro proyecto permite que todos los miembros del equipo puedan ver y entender el proceso de ML.

7. **Monitoreo y Feedback**:
   - Las herramientas de CI/CD pueden integrarse con sistemas de monitoreo para seguir el rendimiento del modelo en producción.
   - Aunque no está implementado en este ejercicio, podríamos extender nuestro workflow de producción para incluir pasos de monitoreo y alerta.

8. **Escalabilidad**:
   - CI/CD facilita la gestión de múltiples modelos y experimentos a medida que el proyecto crece.
   - Nuestra estructura actual podría fácilmente extenderse para manejar múltiples modelos o configuraciones.

La integración de CI/CD en proyectos de ML, como demostramos en este ejercicio, no solo mejora la eficiencia y la calidad del desarrollo de modelos, sino que también prepara el terreno para prácticas más avanzadas de MLOps (Operaciones de Machine Learning). Esta integración es un paso crucial hacia la industrialización del Machine Learning, permitiendo a las organizaciones desarrollar, desplegar y mantener modelos de ML de manera más efectiva y confiable.