# Automatización RPA para la gestión de reservas

Proyecto desarrollado en **UiPath Studio** como parte del Trabajo de Fin de Grado.

La automatización permite procesar de forma masiva una serie de casos de reserva a partir de un fichero Excel, accediendo a una web, consultando vuelos disponibles y generando reportes finales con el resultado de cada ejecución.

## Descripción del proyecto

El objetivo principal de este proyecto es demostrar cómo una solución RPA puede reducir la carga de trabajo manual en un proceso repetitivo, mejorando la eficiencia, la trazabilidad y la gestión de errores.

El robot toma como entrada un conjunto de casos definidos en un fichero Excel. Para cada caso, valida los datos necesarios, accede a la web correspondiente, selecciona el origen y el destino, consulta los vuelos disponibles y aplica el criterio de selección indicado. Finalmente, registra el resultado del procesamiento en los reportes generados por la automatización.

## Tecnologías utilizadas

- UiPath Studio
- Microsoft Excel
- Automatización web
- Gestión de excepciones de negocio y excepciones técnicas

## Estructura del proyecto

```text
TFG/
├── Data/
│   ├── Config.xlsx
│   └── PlantillaEntrada.xlsx
├── Framework/
│   ├── ActualizarReporte.xaml
│   ├── ActualizarReporteIncidencias.xaml
│   ├── CerrarAplicaciones.xaml
│   └── ExcepcionDeNegocio.xaml
├── Main.xaml
├── Main.xaml.json
├── Tramitar.xaml
├── entry-points.json
├── project.json
└── project.uiproj
```

## Archivos principales

### Main.xaml

Es el flujo principal de la automatización.

Se encarga de inicializar el proceso, leer la configuración, cargar los casos de entrada y coordinar la ejecución del resto de workflows.

### Tramitar.xaml

Contiene la lógica principal de tramitación de cada caso.

En este flujo se realizan las acciones sobre la web, la introducción de los datos, la consulta de vuelos disponibles y la selección del vuelo según el criterio indicado en el fichero de entrada.

### Framework/ActualizarReporte.xaml

Actualiza el reporte general con el resultado final de cada caso procesado.

Este reporte permite comprobar el estado en el que ha finalizado cada caso, incluyendo los casos procesados correctamente y aquellos que han terminado con una excepción de negocio.

### Framework/ActualizarReporteIncidencias.xaml

Registra las incidencias técnicas detectadas durante la ejecución.

Este reporte permite conservar la línea completa del caso afectado, facilitando su posterior revisión o reprocesamiento.

### Framework/CerrarAplicaciones.xaml

Se encarga del cierre controlado de aplicaciones o ventanas utilizadas durante la automatización.

### Framework/ExcepcionDeNegocio.xaml

Gestiona los casos en los que no se puede continuar el procesamiento por una condición propia del negocio, como datos inválidos o ausencia de resultados válidos.

### Data/Config.xlsx

Fichero de configuración del proceso.

Desde este archivo se pueden modificar los principales parámetros de ejecución de la automatización sin necesidad de editar directamente los workflows de UiPath.

Entre otros aspectos, permite configurar:

- La ruta del fichero Excel de entrada.
- La ruta donde se generará el reporte general.
- La ruta donde se generará el reporte de incidencias.

Esto permite adaptar la automatización a distintos equipos o entornos simplemente modificando las rutas y valores del archivo `Config.xlsx`, sin tener que cambiar la lógica interna del robot.

### Data/PlantillaEntrada.xlsx

Plantilla de Excel que sirve como modelo para preparar los casos de entrada que procesará el robot.

Este archivo está pensado para que cualquier persona que quiera ejecutar la automatización pueda conocer la estructura que debe tener el fichero de entrada: columnas necesarias, formato esperado y ejemplo de datos válidos.

Para utilizar el robot, se puede copiar esta plantilla, rellenarla con los casos correspondientes y configurar su ruta en el archivo `Data/Config.xlsx`.


## Posibles mejoras futuras

Entre las posibles ampliaciones del proyecto se encuentran:

- Integración con UiPath Orchestrator.
- Uso de colas para gestionar los casos.
- Almacenamiento de resultados en base de datos.
- Mejora del sistema de monitorización.

## Autoría

Proyecto desarrollado como parte del Trabajo de Fin de Grado.

**Autora:** Lidia Jiménez Soriano  
**Tecnología principal:** UiPath  
**Tipo de proyecto:** Automatización RPA

## Licencia

Este proyecto tiene finalidad académica.
