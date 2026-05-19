# 🪙 Lulubit PRO v3 — Sistema Experto de Inversión Cripto

![Live](https://img.shields.io/badge/datos-100%25%20en%20vivo-brightgreen)
![Agentes](https://img.shields.io/badge/agentes%20IA-6%20expertos-blue)
![Sheets](https://img.shields.io/badge/Google%20Sheets-sincronización%20real-green)
![Refresh](https://img.shields.io/badge/auto--refresh-30%20min-orange)

---

## ✅ Problemas corregidos en v3

| Problema | Solución |
|---|---|
| Agentes IA daban `Error: Failed to fetch` | Corrección del endpoint y manejo de errores robusto |
| Montos en portafolio no se guardaban | Editor de montos persistente con localStorage + Sheets |
| No se sincronizaba con Google Sheets | Integración real con Sheets API v4 + OAuth2 |
| Gráfico no mostraba recomendación óptima | Pie chart dinámico: muestra tus montos reales O distribución óptima ajustada por señales BUY live |
| Histórico no se guardaba en Sheets | `saveDay()` ahora escribe directamente en tu spreadsheet |

---

## 🚀 Uso inmediato (sin configuración)

1. Descarga `index.html`
2. Ábrelo en tu navegador (doble clic)
3. Los precios cargan automáticamente desde CoinGecko
4. Ve a **"Mi Portafolio"** → ingresa cuánto tienes en cada moneda
5. Presiona **💾 Guardar portafolio**
6. Ve a **"Agentes IA"** → presiona **🤖 Analizar Todo**
7. Los agentes analizan **tus montos reales** con los precios **en vivo**

---

## 📊 Google Sheets — Sincronización Real

### Conectar (5 minutos):

1. **[Google Cloud Console](https://console.cloud.google.com)** → Nuevo proyecto `Lulubit`
2. **APIs & Services → Library → Google Sheets API v4 → Enable**
3. **Credentials → Create → OAuth 2.0 Client ID → Web Application**
4. Authorized JavaScript origins:
   - `http://localhost`
   - `https://TU_USUARIO.github.io`
5. Copia el **Client ID**
6. En la app: botón **📊 Google Sheets** → pega el Client ID → **Guardar y Conectar**
7. Autoriza con tu cuenta de Google

### Qué se guarda automáticamente en Sheets:
```
Columna A: Fecha
Columna B: Capital total invertido
Columna C: P&L del día
Columna D: Variación %
Columna E: Precio BTC
Columna F: Precio ETH
Columna G: Precio SOL
Columna H: Fear & Greed Index
Columna I: Señal de mercado
Columna J-R: Monto en BTC, ETH, SOL, AVAX, ICP, XRP, AAVE, UNI
Columna R: Nota del día
```

**Sin OAuth2:** los datos se guardan en el navegador y puedes exportar CSV en cualquier momento.

---

## 🤖 Agentes IA — Cómo funcionan

Cada agente recibe en tiempo real:
- ✅ **Tus montos reales** de inversión (lo que ingresaste en "Mi Portafolio")
- ✅ **Precios live** de CoinGecko para las 26 monedas
- ✅ **Fear & Greed Index** actual
- ✅ **RSI estimado** calculado con datos reales
- ✅ **Desviación** de tu portafolio vs distribución óptima

### Los 6 expertos:

| Agente | Especialidad | Te dice... |
|---|---|---|
| 👔 Dr. Marco Financiero | PhD Finanzas · CFA | Qué VENDER/COMPRAR con montos específicos |
| 🔬 Dra. Elena DataSci | PhD Datos · ML | Score estadístico por activo y outlook 7-14 días |
| 🛡 Prof. Andrés Riesgo | PhD Economía · VaR | Riesgo de tu portafolio y % ideal en stablecoins |
| 📈 Sr. Carlos Técnico | RSI/MACD/BB | Stop-loss y puntos de entrada técnicos |
| 🌐 Dra. Sofía Macro | PhD Economía Global | Ciclo halving y contexto macro |
| ⚡ Dr. Luis DeFi | PhD Blockchain | Análisis AAVE/UNI y estrategias yield |

---

## 📈 Gráfico de distribución inteligente

- **Con montos ingresados**: muestra tu distribución real en USD
- **Sin montos**: muestra la distribución óptima con las señales BUY del mercado actual marcadas con ▲
- Se actualiza automáticamente cada 30 minutos con los precios live

---

## ⏱ Ciclo de actualización automática

```
Cada 30 minutos:
  → Precios actualizados (CoinGecko /coins/markets)
  → Sparklines 7 días actualizados
  → Fear & Greed Index actualizado
  → RSI y señales recalculados
  → Toda la UI se refresca

Timer visual en esquina superior derecha
Botón ↻ para refresh manual en cualquier momento
```

---

## 🌐 Publicar en GitHub Pages

```bash
git init
git add index.html README.md
git commit -m "Lulubit PRO v3"
git remote add origin https://github.com/TU_USUARIO/lulubit-pro.git
git push -u origin main
```

Luego: **Settings → Pages → Deploy from branch → main → / (root)**

URL: `https://TU_USUARIO.github.io/lulubit-pro/`

⚠️ Agrega tu URL de GitHub Pages como **Authorized JavaScript Origin** en Google Cloud Console.

---

## ⚠️ Nota sobre los agentes IA

Los agentes funcionan **únicamente dentro de Claude.ai** (este entorno). Para publicarlo en GitHub Pages con agentes funcionando necesitas:

1. Una API key de Anthropic
2. Un backend proxy (para no exponer la key en el cliente)
3. O usar el modo de análisis local (los agentes usan los datos para dar recomendaciones sin IA)

**Alternativa simple**: Abre el HTML desde Claude.ai artifacts donde los agentes sí tienen acceso a la API.

---

*No constituye asesoría financiera. Datos de mercado: CoinGecko (público). IA: Claude (Anthropic).*
