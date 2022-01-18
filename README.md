# Que incorpora el arquetipo

## Pom

- Integración con Github Actions
    - Ejecución de tests
    - Análisis de covererage en codacy
- Plugins Maven
    - jacoco-maven-plugin `${project.build.directory}`
        - Generación de `target/jacoco.exe` para la pipe o sonar
    - spring-boot-maven-plugin
    - maven-jar-plugin
    - maven-source-plugin
    - maven-compiler-plugin `${project.build.directory}/generated-sources`
        - lombok-mapstruct-binding
        - lombok
        - mapstruct-processor
    - maven-javadoc-plugin
- Dependencias Maven
    - spring-boot-starter-web
    - spring-boot-devtools
    - lombok
    - mapstruct
- Dependencias Test Maven
    - spring-boot-starter-test

## Código fuente

Código main springboot con mensaje hola mundo
```
@SpringBootApplication
public class Main implements CommandLineRunner {

	public static void main(String... args) {
		SpringApplication.run(Main.class);
	}

	@Override
	public void run(String... args) throws Exception {
		System.out.println("Hello world from a custom fresh archetype !!!!");
	}
}
```

## Código tests

Adición de test con prueba de levantamiento de contexto
```
@SpringBootTest
class RigorousTest {

	@Test
	void rigorousTest() {
		Assertions.assertTrue(true);
	}

}
```

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
# Si quieres usar las github actions en tu repositorio de github

Necesitarás
- Cuenta github https://github.com/join
- Cuenta Codacy https://www.codacy.com/signup
- Configurar Github Action https://github.com/codacy/codacy-coverage-reporter-action
    - Definir un secret de tu token de codacy `CODACY_TOKEN` en tu github
    - Definir un secret `CODACY_PROJECT_TOKEN` a nivel de tu repositorio de tu proyecto en codacy

# Referencias
Referencias para crear un arquetipo o modificar el actual: https://maven.apache.org/guides/mini/guide-creating-archetypes.html
