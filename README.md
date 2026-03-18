# Detección de Fraude Financiero con Machine Learning

Sistema de detección de transacciones fraudulentas utilizando aprendizaje automático sobre un dataset de 6.3 millones de registros.

---

## Contexto

Las transacciones financieras digitales han crecido exponencialmente, y con ellas el riesgo de fraude. Los sistemas tradicionales de detección basados en reglas fijas son lentos, inflexibles y fácilmente evadibles por patrones de fraude modernos.

Este proyecto aplica técnicas de Machine Learning para identificar automáticamente transacciones fraudulentas en una plataforma de dinero móvil, analizando millones de registros con alta precisión.

---

## Problema

El dataset contiene registros de transacciones financieras donde **algunos fueron marcados incorrectamente como fraude** por algoritmos existentes, generando falsos positivos que afectan la experiencia del usuario y la confianza en el sistema.

Los principales desafíos son:

- **Desbalance de clases**: las transacciones fraudulentas representan una fracción mínima del total.
- **Falsos positivos** generados por el algoritmo anterior que deben ser corregidos.
- **Volumen masivo de datos**: 6.3 millones de registros requieren un pipeline eficiente.
- **Patrones complejos** que no son detectables con reglas simples.

### Tipos de transacciones

| Tipo | Descripción |
|------|-------------|
| `CASH-IN` | Depósito de efectivo a través de un comerciante. Aumenta el saldo. |
| `CASH-OUT` | Retiro de efectivo a través de un comerciante. Disminuye el saldo. |
| `DEBIT` | Transferencia desde el servicio móvil a una cuenta bancaria. |
| `PAYMENT` | Pago de bienes o servicios. Disminuye el saldo del comprador. |
| `TRANSFER` | Envío de dinero a otro usuario dentro de la plataforma. |

---

## Solución

Pipeline completo de ciencia de datos que incluye preprocesamiento, ingeniería de características, selección y evaluación de modelos para detectar transacciones fraudulentas.

### Flujo del proyecto

```
Datos crudos → Preprocesamiento → Feature Engineering → Entrenamiento → Evaluación → Predicción
```

### Preprocesamiento
- Limpieza y tratamiento de valores nulos.
- Codificación de variables categóricas (tipo de transacción).
- Normalización de variables numéricas.
- Manejo del desbalance de clases.

### Feature Engineering
- Diferencia entre saldo antes y después de la transacción.
- Detección de inconsistencias en saldos (posibles indicadores de fraude).
- Identificación de patrones por tipo de transacción.

### Modelos evaluados y resultados

| Modelo | Accuracy | Precision |
|--------|----------|-----------|
| Logistic Regression | 1.00 | 0.6633 |
| Random Forest Classifier | 1.00 | 0.9837 |

### Métricas de evaluación

| Métrica | Descripción |
|---------|-------------|
| Accuracy | Proporción total de predicciones correctas |
| Precision | Transacciones marcadas como fraude que realmente lo son |
| Recall | Fraudes reales correctamente detectados |
| F1-Score | Balance entre precisión y recall |
| AUC-ROC | Capacidad discriminativa del modelo |

> El **Recall** es la métrica crítica: un fraude no detectado (falso negativo) genera pérdidas directas.

### Resultado
Ambos modelos alcanzaron un **100% de accuracy**. Sin embargo, la Precision del **Random Forest (98.4%)** supera ampliamente a la de Regresión Logística **(66.3%)**, lo que lo convierte en el modelo más confiable para este problema dado el fuerte desbalance de clases.

---

## Tecnologías

| Categoría | Herramienta |
|-----------|-------------|
| Lenguaje | Python 3.10+ |
| Manipulación de datos | Pandas, NumPy |
| Machine Learning | Scikit-learn |
| Visualización | Matplotlib, Seaborn |
| Entorno | VS Code |
