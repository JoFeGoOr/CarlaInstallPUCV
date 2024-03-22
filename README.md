# Carla Install PUCV

## Importante
La guia a continuacion representa el trabajo realizado entre octubre-diciembre del 2023 y la fecha de elaboracion de esta guia es marzo del 2024, la version de CarlaSim a instalar es la 0.9.14, ademas de necesitarse software adicional como lo es RoundRunner y Blender v3.8. En el momento de elaboracion de esta guia ya se encuentra disponible una nueva version de CarlaSim (0.9.15), la cual incluye mejoras en el flujo de elaboracion de mapas, por lo cual se recomienda leer la [documentacion oficial](https://carla.readthedocs.io/en/latest/)

## Enlaces importantes
* Video de instalacion del stack UnrealEngine(CarlaSim) + RoundRunner + Blender -> [link](https://www.youtube.com/watch?v=lLkFA0fPrgs)
* Repositorio con material AudioVisual CarlaSim PUCV e instalacion (se necesita permiso de acceso)-> [link](https://drive.google.com/drive/u/1/folders/1pgqZeGp7VuC2uT_PtHTpwoKisFoOACOo)
* Documentacion Oficial CarlaSim -> [link](https://carla.readthedocs.io/en/latest/)

## Posibles Errores de instalacion

* Al crear un proyecto en unreal engine aparece "Assertion Failed: ResourceTableFrameCounter == INDEX_NONE"
  - Ir a ./your_UEProject/Config/DefaultEngine.ini
  - buscar un bloque que se vea como acontinuacion (si no lo hay, agregarlo al final)
    [/Script/WindowsTargetPlatform.WindowsTargetSettings]
    DefaultGraphicsRHI=DefaultGraphicsRHI_DX11
  - Cambiar > DefaultGraphicsRHI_DX11 → DefaultGraphicsRHI_DX12
* No se crea la carpeta "dist" ((carpeta-carla)\PythonAPI\carla\dist) (si eso pasa es necesario revisar la salida del comando "make PythonAPI", esto nos indicara cual puede ser el problema (puede variar de instalacion en instalacion))
  - Ejecutar "make clean" y luego eliminar la carpeta xerces-c-3.2.3-install y xerces-c-3.2.3-source de la carpeta "carla/Build" luego        ejecutar "make PythonAPI" 2 veces, sea una solucion.
  - En la carpeta "dist" existira un archivo .whl, ese archivo debe ser instalado manualmente para utilizar python junto con el carla,        abrir la capeta "dist" desde terminal y ejecutar pip install 'nombre-archivo-whl'.whl
