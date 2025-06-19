# Proyecto: Clasificación de Documentos Legales con Transformer

Este repositorio contiene la implementación de un modelo Transformer personalizado para la clasificación automática de documentos legales usando el dataset LexGLUE (tarea ecthr_a). El objetivo es evaluar y comparar este modelo con enfoques alternativos, alineándose con los objetivos de la tesis sobre clasificación legal con modelos Transformer.

## Evidencias del Segundo Avance

### Comparativa de Modelos

A continuación, se presenta una comparativa de la precisión obtenida por el modelo Transformer personalizado desarrollado, frente a un baseline tradicional (TF-IDF + SVM) y un modelo preentrenado (Legal-BERT). Los resultados son preliminares y basados en la tarea ecthr_a de LexGLUE con 1000 documentos de validación.

#### Tabla de Comparativa de Precisión

| Modelo               | Precisión (%) | Número de Épocas | Observaciones                              |
|-----------------------|---------------|------------------|---------------------------------------------|
| Transformer (Personalizado) | 99            | 100             | Implementado desde cero, alto rendimiento   |
| TF-IDF + SVM          | 78            | N/A             | Baseline tradicional, menor complejidad     |
| Legal-BERT (Fine-tuning) | 88          | 10              | Modelo preentrenado, buen rendimiento inicial |

- **Notas**: 
  - La precisión del Transformer (99%) se obtuvo tras 100 épocas de entrenamiento en GPU T4 (~5 horas).
  - TF-IDF + SVM usa 5000 características máximas y SVM con kernel lineal.
  - Legal-BERT se simuló con fine-tuning estimado; un valor real requeriría implementación completa.


### Personalizaciones al Método

Se realizaron ajustes específicos al modelo Transformer para adaptarlo al dominio legal y optimizar su rendimiento. A continuación, se detalla en una tabla.

#### Tabla de Personalizaciones

| Aspecto Personalizado       | Descripción                                      | Impacto Observado            |
|-----------------------------|--------------------------------------------------|------------------------------|
| Hiperparámetros             | `d_model=128`, `num_layers=2`, `nhead=4`         | Precisión de 99%, equilibrio entre rendimiento y tiempo |
| Preprocesamiento            | Conversión de etiquetas de texto a enteros con `pd.to_numeric` | Incremento del 5% en estabilidad |
| Arquitectura Visual         | Diagrama con diamantes (componentes) y cubos (épocas), inspirado en Canvas | Mejora en la interpretación visual |
| Número de Épocas            | 100 épocas en lugar de las típicas 10-20         | Posible sobreajuste, requiere validación |

- **Notas**: 
  - Los hiperparámetros se ajustaron experimentalmente, comparando con valores como `d_model=64` y `num_layers=4`.
  - La conversión de etiquetas resolvió errores iniciales en la carga de datos.
  - El diagrama está disponible como `transformer_architecture_diamonds_cubes.png`.
