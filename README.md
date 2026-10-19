# Recomendador de perfumes

El [notebook](notebooks/analisis_viabilidad_recomendador_perfumes.ipynb) usa `data/fragrances_clean.csv` para recomendar perfumes por notas aromáticas similares y filtrar candidatos según la columna `Gender`. El CSV contiene **24.063 perfumes y 18 columnas**.

La puntuación combina similitud de notas mediante TF-IDF y coseno (75 %), acordes principales (20 %) y perfumistas compartidos (5 %). Cada recomendación exige al menos una nota compartida y muestra las señales que explican su posición. La valoración de usuarios no forma parte de la similitud aromática.

El filtro `hombre` incluye perfumes `men` y `unisex`; `mujer` incluye `women` y `unisex`; `unisex` se limita a esa categoría; `todos` admite las tres. Estas etiquetas provienen directamente del CSV.

## Uso

Requiere Python 3.10 o posterior.

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook notebooks/analisis_viabilidad_recomendador_perfumes.ipynb
```

En el notebook, `recomendar_perfumes(id_perfume, genero="hombre", limite=5)` acepta el ID mostrado en el catálogo o un nombre exacto y único.
