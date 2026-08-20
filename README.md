# Curso de análisis de datos

Materiales y notebooks para una clase de análisis de datos con Python y Jupyter.

## Contenido

- [Bienvenida a Jupyter](notebooks/00_bienvenida.ipynb)
- [Introducción a pandas](notebooks/01_pandas_introduccion.ipynb)
- [Datos de ejemplo](datos/ventas.csv)
- [Ejercicios](ejercicios/README.md)
- [Dependencias](requirements.txt)

## Abrir en Google Colab

Puedes abrir un notebook de este repositorio en Colab con una URL como esta:

`https://colab.research.google.com/github/yimpoX/curso-analisis-datos/blob/main/notebooks/00_bienvenida.ipynb`

## Ejecutar localmente

```bash
git clone https://github.com/yimpoX/curso-analisis-datos.git
cd curso-analisis-datos
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

En Windows, activa el entorno con `.venv\Scripts\activate`.

## Flujo sugerido para estudiantes

1. Hacer fork o una copia del repositorio.
2. Abrir el notebook de la semana en Colab o JupyterLab.
3. Resolver las celdas marcadas como ejercicio.
4. Escribir las conclusiones en Markdown.
5. Entregar el enlace al repositorio o el archivo `.ipynb`.

No subas contraseñas, tokens ni datos personales al repositorio.
