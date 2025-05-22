---
icon: memo
---

# Que es Jupyter Notebook

## Explicación del entorno de Jupyter Notebook[¶](broken-reference) <a href="#explicaci-c3-b3n-del-entorno-de-jupyter-notebook" id="explicaci-c3-b3n-del-entorno-de-jupyter-notebook"></a>

### ¿Qué es Jupyter Notebook? <a href="#c2-bfqu-c3-a9-es-jupyter-notebook" id="c2-bfqu-c3-a9-es-jupyter-notebook"></a>

{% hint style="info" %}
En este módulo, aprenderás a utilizar Jupyter Notebook, una herramienta fundamental para el análisis de datos y la programación en Python. A continuación, se describen los aspectos clave que debes conocer para comenzar a trabajar en este entorno.
{% endhint %}

<details>

<summary>La importancia de Jupyter Notebook en el desarrollo de la ingeniería industrial y el manejo de datos</summary>

Jupyter Notebook es una herramienta esencial en el ámbito de la ingeniería industrial debido a su capacidad para combinar texto, código y visualizaciones en un solo documento. Esto facilita la documentación y presentación de análisis complejos de datos. Los ingenieros industriales pueden usar Jupyter para:

* Prototipar y validar rápidamente modelos de optimización.
* Visualizar datos de manera interactiva, lo cual es crucial para la identificación de patrones y tendencias.
* Colaborar de manera eficiente gracias a la facilidad de compartir notebooks con colegas.
* Integrar fácilmente diferentes lenguajes de programación, como Python y R, que son comúnmente utilizados en el análisis de datos.

El uso de Jupyter Notebook ayuda a mejorar tanto la eficiencia como la claridad en la comunicación de resultados analíticos.

</details>

<details>

<summary>Que es Jupyter Notebook</summary>

Jupyter Notebook es un entorno de desarrollo interactivo que permite crear y compartir documentos que contienen código en vivo, ecuaciones, visualizaciones y texto narrativo. Es ampliamente utilizado en ciencia de datos, aprendizaje automático y educación.

</details>

<details>

<summary>Otro Concepto:</summary>

Jupyter Notebook es una herramienta de código abierto que te permite crear y compartir documentos que contienen código ejecutable, visualizaciones y texto enriquecido. Es ideal para:

1. Análisis de datos: Permite explorar, limpiar y visualizar datos de manera interactiva.

2) Aprendizaje: Es una excelente herramienta para aprender a programar y experimentar con diferentes conceptos.

3. Documentación: Puedes crear informes y tutoriales que combinen código, texto y resultados.

</details>

<details>

<summary>C<strong>oncepto tres</strong></summary>

Los cuadernos Jupyter Notebooks son una aplicación web de código abierto que facilita un entorno computacional interactivo, lo que permite a los usuarios crear y compartir documentos que integran código en vivo, visualizaciones y texto narrativo sin problemas. Estos cuadernos, particularmente populares en la ciencia de datos, admiten más de 40 lenguajes de programación, principalmente Python, Julia y R, lo que los convierte en herramientas versátiles para el análisis de datos y con fines educativos. Su formato único promueve una combinación de exploración y documentación, lo que permite a los usuarios realizar análisis, visualizar resultados y mejorar la comunicación con partes interesadas no técnicas, lo que eleva el aspecto colaborativo de los proyectos basados **en datos**.

</details>

### **Consejo sobre Jupyter Notebook**

{% hint style="info" %}
Aprovecha la función de "Checkpoint" en Jupyter Notebooks para guardar versiones de tu trabajo exitosamente ejecutado. Esto te permitirá volver a ese estado si cometes errores o si deseas comparar diferentes versiones de tu análisis. Además, personaliza tu entorno utilizando extensiones de JupyterLab para mejorar tu productividad y adecuar el entorno a tus necesidades específicas.
{% endhint %}

{% tabs %}
{% tab title="Fuente1" %}
[https://storm.genie.stanford.edu/article/data-analysis-jupyter-notebook-and--sql-172832](https://storm.genie.stanford.edu/article/data-analysis-jupyter-notebook-and--sql-172832)
{% endtab %}

{% tab title="Fuente 2" %}
[https://www.bmc.com/blogs/instalación-de-jupyter-para-big-data-y-analíticas/](https://www.bmc.com/blogs/instalaci%C3%B3n-de-jupyter-para-big-data-y-anal%C3%ADticas/)
{% endtab %}

{% tab title="Fuente 3" %}
[https://careerfoundry.com/es/blog/data-analytics/jupyter-notebook-tutorial/](https://careerfoundry.com/es/blog/data-analytics/jupyter-notebook-tutorial/)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Estructura de un Notebook" %}
Un notebook está compuesto por celdas. Cada celda puede contener:

* Código: Aquí escribes el código que quieres ejecutar (Python, R, etc.).
* Markdown: Puedes escribir texto formateado, como títulos, listas y ecuaciones, en este caso se utiliza el lenguaje de escritura Latex.
{% endtab %}

{% tab title="Características clave de Jupyter Notebook" %}
* Interactivo: Puedes ejecutar código línea por línea y ver los resultados inmediatamente.
* Visual: Puedes crear visualizaciones directamente en el notebook utilizando bibliotecas como Matplotlib y Seaborn.
* Extensible: Jupyter Notebook se puede personalizar con una gran variedad de extensiones.
* Colaborativo: Puedes compartir tus notebooks con otros y colaborar en tiempo real.
{% endtab %}

{% tab title="Interfaz de Jupyter Notebook" %}
* La interfaz de Jupyter es intuitiva y está dividida en varias secciones:
* Celdas: Las celdas son bloques donde puedes escribir código o texto. Puedes alternar entre celdas de código y celdas de texto (Markdown).
* Menú superior: Aquí encontrarás opciones para guardar, abrir, crear nuevos notebooks y más.
* Barra lateral: Muestra los archivos y notebooks disponibles en el directorio actual.
{% endtab %}

{% tab title="Uso de Celdas" %}
* Celdas de Código: Escribe código Python aquí y ejecútalo presionando Shift + Enter.
* Celdas de Texto (Markdown): Puedes documentar tu trabajo usando Markdown para formatear texto, incluir imágenes y enlaces.
{% endtab %}
{% endtabs %}

### **Ejercicio Practico:**

Para crear un libro de Jupyter Notebook, utilizaremos Google Colab, ya que es fácil y gratuito. Si prefieres hacerlo en tu PC local, también es posible, pero nos centraremos en el trabajo en la nube por ahora.

1. Abre tue cuenta de Google.
2. Accede a tu Google Drive y crea una carpeta para
3.  Para crear un archivo nuevo en un programa llamado "Google Collaboratory", sigue estos pasos:

    1. Abre la carpeta donde deseas crear el archivo.
    2. Si no encuentras "Google Collaboratory", abre tu navegador web.
    3. Busca "Google Colab" y accede al sitio oficial.
    4. Vincula tu cuenta de Google con el "Notebook" de Google Colab.
    5. Crea un nuevo archivo y comienza a trabajar

    &#x20;

{% hint style="info" %}
Usa Jupyter Notebook para automatizar cálculos y análisis repetitivos, lo cual es común en la ingeniería industrial. Puedes escribir scripts de Python para realizar simulaciones, análisis de datos, y generar reportes automáticamente, mejorando la eficiencia y reduciendo el riesgo de errores manuales.
{% endhint %}
