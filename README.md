# Descargando el proyecto arquetipo

`git clone https://github.com/MaQuiNa1995/Custom-Maven-Archetype.git`

# Compilación

(Este paso no hará falta cuando despliegue en maven central el arquetipo)

`mvn install`

Si hiciste un install y modificaste el arquetipo y este tiene la misma versión que el que hiciste el install deberás añadir el modificador -U

`mvn install -U`

# Usando el arquetipo
```
mvn archetype:generate ^
  -DarchetypeGroupId=com.github.maquina1995 ^
  -DarchetypeArtifactId=archetype ^
  -DarchetypeVersion=1.0.0-RELEASE ^
  -DgroupId=com.github.maquina1995 ^
  -DartifactId=prueba ^
  -Dversion=1.0.0-BETA
```

Si usas Linux cambia los `^` por `\`

Despues de ver que todos los paquetes están bien en las trazas de consola que te han salido despues de ejecutar daremos enter y ya tendremos el proyecto creado 

## Ejecutar Test
```
cd prueba
mvn test
```

## Ejecutar Aplicación
```
cd prueba
mvn spring-boot:run
```

referencias: https://maven.apache.org/guides/mini/guide-creating-archetypes.html