# Usando FOLIUM

## Cómo usar Folium

Folium es una biblioteca de Python que se utiliza para crear mapas interactivos. Sigue estos pasos para comenzar a usar Folium:

**Instalar Folium**\
Asegúrate de que Folium esté instalado. Puedes instalarlo usando pip:

```python
pip install folium
```

#### Importación de la Librería

El primer paso en el código es importar la librería Folium.

```
import folium 
```

#### Creación del Mapa Base Centrado en Montería

Para crear un mapa, se necesita la latitud y longitud del punto central. Montería, Córdoba, Colombia, se encuentra aproximadamente en las coordenadas 8.75 grados de latitud norte y −75.88 grados de longitud oeste.

Se crea un objeto `Map` de Folium, especificando la ubicación inicial y el nivel de zoom.

```python
# Coordenadas aproximadas de Montería
monteria_coords = [8.74798, -75.88141]

# Creación del mapa
# 'location' define el centro del mapa.
# 'zoom_start' define el nivel de zoom inicial.
mapa_monteria = folium.Map(location=monteria_coords, zoom_start=13)
```

Se pueden agregar marcadores a diferentes puntos de interés en Montería. Cada marcador puede tener una ventana emergente (popup) o una etiqueta (tooltip) con información adicional.

Por ejemplo, se agregarán marcadores para:

* **Parque Simón Bolívar**: Un punto central y emblemático.
* **Catedral San Jerónimo de Montería**: Un importante sitio religioso e histórico.
* **Aeropuerto Los Garzones**: Principal terminal aérea de la ciudad.

Se necesitan las coordenadas de estos lugares.

## Coordenadas de puntos de interés (ejemplos aproximados)

```python
ubicaciones = {
"Parque Simón Bolívar": [8.7530, -75.8810],
"Catedral San Jerónimo": [8.7525, -75.8830],
"Aeropuerto Los Garzones": [8.8236, -75.8256]
}
```

## Agregar marcadores al mapa

```python
for nombre, coords in ubicaciones.items():
folium.Marker(
location=coords,
popup=f"{nombre}", # Texto para mostrar
tooltip=nombre, # Texto al pasar el cursor
icon=folium.Icon(color="blue", icon="info-sign") # Icono personalizado
).add_to(mapa_monteria)

```

#### Ejemplo de Folium:

en este ejemplo se le pedira a jupyter notebook o atu IDLE favorito que segun la ubicacion que desees el te señale en el mapa el sitio,

```python
import folium

def mostrar_mapa_coordenadas():
  
    try:
        # Solicitar entrada al usuario
        latitud_str = input("Ingrese la latitud (ej. 8.748): ")
        longitud_str = input("Ingrese la longitud (ej. -75.881): ")

        # Convertir las entradas a números flotantes
        latitud = float(latitud_str)
        longitud = float(longitud_str)

        # Validar rangos razonables para latitud y longitud
        if not (-90 <= latitud <= 90):
            print("Error: La latitud debe estar entre -90 y 90.")
            return
        if not (-180 <= longitud <= 180):
            print("Error: La longitud debe estar entre -180 y 180.")
            return

        # Crear el mapa centrado en las coordenadas ingresadas
        coordenadas_ingresadas = [latitud, longitud]
        mapa_personalizado = folium.Map(location=coordenadas_ingresadas, zoom_start=15)

        # Agregar un marcador en las coordenadas ingresadas
        folium.Marker(
            location=coordenadas_ingresadas,
            popup=f"Lat: {latitud}, Lon: {longitud}",
            tooltip="Ubicación Ingresada",
            icon=folium.Icon(color="green", icon="map-marker")
        ).add_to(mapa_personalizado)

   
        display(mapa_personalizado) # 'display' es específico para IPython/Jupyter

    except ValueError:
        print("Error: Por favor, ingrese valores numéricos válidos para latitud y longitud.")
    except Exception as e:
        print(f"Ha ocurrido un error inesperado: {e}")

# Ejecutar la función para probar
if __name__ == "__main__":
    
    
    mostrar_mapa_coordenadas()
```

