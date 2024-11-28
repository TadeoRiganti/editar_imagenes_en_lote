# editar_imagenes_en_lote
Compendio de scripts para editar imagenes en lote.

## Descripción

La intención de este repositorio es experimentar con librerias de procesamiento de imagenes en lote, primero mediante scripts locales y mas adelante armar una aplicacion web que permita hacer lo mismo. 

## Objetivos

1. Experimentar distintas librerias y soluciones.
2. Documentar cada tecnica / metodo.
3. Implementarlo como herramientas de trabajo.

## Lista de scripts

### Modificar el brillo

- Objetivo: Aumentar el brillo en un 20%.
- Libreria: Pilow (PIL Fork)
- Materiales: Imagenes dentro de una carpeta.
- Tareas: 
  - Abrir imagen carpeta origen. 
  - Modificar imagen segun los parametros.
  - Guardar el output en carpeta destino. 

#### Version 1

El script se manejara desde un editor de texto y se controlara mediante variables:
- directorio_imagenes
- factor_brillo 

<hr>

## Lista de tareas

- [x] Crear repositorio
- [x] Completar `README.md`
- [x] Crear branch 'script_brightness'
- [ ] Agregar una tabla de contenidos dentro del README.md
- [x] Armar la Home de la WIKI
    - [x] Home
       - [x] Sobre el proyecto
          - [ ] Introducción
          - [ ] Compendio de scripts 
          - [x] Script - Modificar brillo
             - [x] Version 1 
       - [x] Documentacion tecnica
          - [ ] Activar Entorno virtual
          - [ ] Crear `Requirements.txt`
          - [ ] Instalar librerias con `Requirements.txt`
