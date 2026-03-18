# Streamlit Social Dashboard MVP

## Objetivo
Crear una web app interna en Streamlit que:
- reciba una lista de links de posteos de TikTok e Instagram
- extraiga métricas públicas con Apify
- calcule views, interacciones y engagement rate
- releve hasta 5 comentarios por posteo
- haga análisis de sentimiento sobre esa muestra
- muestre dashboard y conclusiones generadas por IA

## Alcance MVP
### Input
- Textarea con URLs, una por línea
- Plataformas soportadas: Instagram y TikTok

### Métricas por post
- views
- likes
- comments_count
- shares
- saves
- interactions = likes + comments_count + shares + saves
- engagement_rate = interactions / views * 100

### Comentarios
- máximo 5 comentarios por posteo
- si hay menos, usar los disponibles
- si no hay comentarios, marcar el posteo
- aclarar que la muestra no representa necesariamente a toda la audiencia

### Dashboard
#### Tab 1: Performance
- KPIs generales
- tabla por contenido
- gráfico de línea con views por fecha
- bloque de conclusiones con IA

#### Tab 2: Comentarios
- total de comentarios analizados
- distribución de sentiment
- tabla de comentarios
- bloque de lectura cualitativa con IA

## Reglas
- ER siempre expresado en porcentaje
- saves se suman a interacciones
- tolerar métricas faltantes
- mostrar advertencia cuando saves o comentarios no estén disponibles

## Stack
- Streamlit
- Python
- Pandas
- Plotly
- Apify API
- OpenAI API para conclusiones
- dotenv para variables de entorno

## Estructura sugerida
- app.py
- services/apify_client.py
- services/ai_insights.py
- services/metrics.py
- services/comments.py
- utils/parsers.py
- utils/normalizers.py
- requirements.txt
- .env.example
- README.md

## Notas de producto
- La V1 prioriza velocidad y simplicidad
- El scraping debe ser modular para poder reemplazar actores de Apify más adelante
- El límite de comentarios debe quedar parametrizable, aunque por defecto sea 5
