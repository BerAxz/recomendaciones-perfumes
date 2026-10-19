# Recomendador de perfumes por reglas de asociación

Análisis exploratorio y demostración académica para estudiar relaciones entre notas aromáticas de perfumes. Cada perfume consolidado es una transacción; las notas de su ficha son los ítems. No se usan usuarios, compras ni historiales comerciales.

## Estructura

```text
.
├── data/
│   └── parfumo_data_clean.csv
├── notebooks/
│   └── analisis_viabilidad_recomendador_perfumes.ipynb
├── requirements.txt
└── README.md
```

El notebook detecta automáticamente las columnas reales del CSV, analiza la cobertura de notas, prepara las transacciones, compara configuraciones de Apriori y presenta recomendaciones construidas con reglas reales del catálogo.

## Ejecutar

Requiere Python 3.10 o posterior.

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook notebooks/analisis_viabilidad_recomendador_perfumes.ipynb
```

En Windows, activa el entorno con `.venv\\Scripts\\activate`. El notebook busca el archivo en `data/parfumo_data_clean.csv`; si lo mueves, cambia `RUTA_CSV` en la sección de carga.

## Decisiones del análisis

- La fuente es el CSV de Parfumo incorporado en `data/`.
- Cada fragancia se identifica por marca y nombre. URLs repetidas se eliminan primero y las variantes/publicaciones restantes se consolidan por marca y nombre base (retirando sufijos de concentración observados en el título) y se conserva la ficha con más notas; no se mezclan sus listas.
- Los productos sin notas se incluyen al medir cobertura, pero no se consideran transacciones vacías para Apriori porque los campos faltantes representan información desconocida.
- Los acordes generales se excluyen del conjunto de ítems para mantener el análisis en notas aromáticas.
- Las reglas representan coocurrencias estadísticas de las fichas y no necesariamente similitud olfativa percibida.

El CSV Parfumo fue incorporado localmente a este repositorio. El notebook analiza ese archivo tal cual y no descarga datos durante la ejecución.
