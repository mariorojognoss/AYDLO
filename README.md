# AYDLO
Para ejecutar todos los scripts a la vez es necesario completar estos pasos

 - sacar todos los csv y codificarlos para linux (asegurarse que no tienen comillas dobles "")
 - crear el esquema de carpetas para añadir los scripts y los CSV, por ejemplo:
    - se pueden añadir otros csv de otros proyectos, por eso es recomendable nombrarlos de manera reconocible, en cambios los sh son validos para todos.
        - ./ecosistema/(ecosistema.sh + ecosistema<nombre_proyecto>.csv)
        - ./organizaciones/(organizaciones.sh + organizaciones<nombre_proyecto>.csv)
        - ./personas/(personas.sh + personas<nombre_proyecto>.csv)
        - ./proyecto/(proyecto.sh + proyecto<nombre_proyecto>.csv)
        - ./recursossemanticos/(recursossemanticos.sh + recursossemanticos<nombre_proyecto>.csv)
        - ./semanticadebil/(semanticadebil.sh + semanticadebil<nombre_proyecto>.csv)
 - Añadir el script para ejecutar todos los demás a la vez
 - Ejecutar el script "./<nombre_script.sh>"

El script es el siguiente:



|Tipo|Contenido
|-----|--------
|Recurso semántica débil| Imágenes enlaces
|


```
origen=<ruta_origen>
destino=<ruta_destino>
proyecto=<proyecto>
rutacsvEcosistema="./ecosistema/ecosistema_<nombre_proyecto>.csv"
rutacsvOrganizacion="./organizaciones/organizacion_<nombre_proyecto>.csv"
rutacsvPersonas="./personas/personas_<nombre_proyecto>.csv"
rutacsvProyecto="./proyecto/proyecto_<nombre_proyecto>.csv"
rutacsvRecursossemanticos="./recursossemanticos/recursossemanticos_<nombre_proyecto>a.csv"
rutacsvSemanticadebil="./semanticadebil/semanticadebil_<nombre_proyecto>.csv"

mkdir ./logs

./ecosistema/ecosistema.sh "$origen" "$destino" "$rutacsvEcosistema" > ./logs/ecosistema_${proyecto}.txt 2> ./logs/ecosistema_${proyecto}_error.txt
./organizaciones/organizaciones.sh "$origen" "$destino" "$rutacsvOrganizacion" > ./logs/organizacion_${proyecto}.txt 2> ./logs/organizacion_${proyecto}_error.txt
./personas/personas.sh "$origen" "$destino" "$rutacsvPersonas" > ./logs/personas_${proyecto}.txt 2> ./logs/personas_${proyecto}_error.txt
./proyecto/proyecto.sh "$origen" "$destino" "$rutacsvProyecto" > ./logs/proyecto_${proyecto}.txt 2> ./logs/proyecto_${proyecto}_error.txt
./recursossemanticos/recursossemanticos.sh "$rutacsvRecursossemanticos" > ./logs/recursossemanticos_${proyecto}.txt 2> ./logs/recursossemanticos_${proyecto}_error.txt
./semanticadebil/semanticadebil.sh "$origen" "$destino" "$rutacsvSemanticadebil" > ./logs/semanticadebil_${proyecto}.txt 2> ./logs/semanticadebil_${proyecto}_error.txt
```