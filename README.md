# Clase
Mejoras al modelo de corrección Barkjohn et al. (2021) para sensores PurpleAir PM2.5

# 🟣 Enhanced PurpleAir PM2.5 Correction Model
## Mejoras al Modelo de Corrección Barkjohn et al. (2021)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXX)

---

## 📋 Descripción

Este proyecto implementa mejoras metodológicas al modelo de corrección de **Barkjohn et al. (2021)** para datos de PM2.5 colectados con sensores **PurpleAir**. Las mejoras incluyen corrección de bias en el sensor de humedad, modelado no-lineal para alta humedad relativa, coeficientes adaptativos por región/temporada, y un enfoque de machine learning.

**Artículo completo:** [`article.md`](article.md) | [`article.pdf`](article.pdf)

---

## ✨ Mejoras Implementadas

| Mejora | Descripción | Impacto |
|--------|-------------|---------|
| 🔧 **Corrección de Bias en RH** | Compensa error sistemático del sensor BME280 (10-20% subestimación) | Reduce error ~15% |
| 📈 **Modelo No-Lineal** | Captura crecimiento higroscópico exponencial cuando RH > 50% | Reduce bias ~70% en alta humedad |
| 🌍 **Coeficientes Adaptativos** | Modelos específicos por región climática y temporada | Mejora consistencia regional |
| 🤖 **Machine Learning** | Gradient Boosting Regressor con features ingenierizadas | R² = 0.983, RMSE = 0.73 µg/m³ |

---

## 📊 Resultados Principales

### Comparación de Métodos de Corrección

| Método | R² | RMSE (µg/m³) | MAE (µg/m³) | Bias Medio (µg/m³) |
|--------|-----|--------------|-------------|-------------------|
| Sin corrección (raw) | -0.302 | 6.393 | 5.102 | 5.037 |
| Barkjohn Original (2021) | 0.601 | 3.540 | 3.286 | 3.266 |
| **No-Lineal + RH Corregida** | 0.834 | 2.286 | 1.674 | 0.811 |
| Adaptativo Regional | 0.810 | 2.439 | 2.085 | 1.788 |
| **Machine Learning (Propuesto)** | **0.983** | **0.729** | **0.569** | **0.013** |

### Mejora vs. Modelo Original
- **RMSE reducido en 79.5%** (de 3.54 a 0.73 µg/m³)
- **Bias eliminado** (de 3.27 a 0.01 µg/m³)
- **Varianza explicada**: 98% vs. 60%

---

## 🚀 Instalación

### Requisitos
```bash
Python >= 3.10
