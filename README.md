# Maven

## Instalacion

```bash
mvn --version
```
## Creando un Proyecto por Linea de Comandos

Creando un arquetipo
```bash
mvn archetype:generate -DgroupId=com.taller.app -DartifactId=mi-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```

```bash
cd mi-app
tree

.
└── mi-app
    ├── pom.xml
    └── src
        ├── main
        │   └── java
        │       └── com
        │           └── taller1
        │               └── app
        │                   └── App.java
        └── test
            └── java
                └── com
                    └── taller1
                        └── app
                            └── AppTest.java

12 directories, 3 files
```

## Principales Comandos

Elimina el directorio **target** del proyecto maven.
```bash
mvn clean
```
Compila el codigo fuente.

```bash
mvn compile
```
Empaqueta el aplicativo.

```bash
mvn package
```

Construye el proyecto maven e instala los archivos (JAR, WAR, pom.xml, etc) del proyecto en el repositorio local.

```bash
mvn install
```

Permite desplegar los artefactos en un repositorio remoto.
El repositorio remoto debe estar configurado correctamente en el archivo project **pom.xml** mediante el tag **distributionManagement**. El archivo **settings.xml** permite a maven utilizar mecanismos de autenticacion.

```bash
mvn deploy
```

Permite validar que el proyecto maven este correctamente creado y toda la informacion este disponible.

```bash
mvn validate
```

Genera todo el arbol de dependencias del proyecto maven.

```bash
mvn dependency:tree
```

Este comando permite analizar todas las dependencias declaradas no usadas y las no declaradas usadas. Es muy util para reducir el tamaño del aplicativo eliminando dependencias no utilizadas del archivo **pom.xml**.

```bash
mvn dependency:analyze
```

Este comando genera un sitio para el proyecto maven. Dentro del directorio **target** se creara el directorio **sitio** donde encontrara los archivos HTML que provee informacion acerca del proyecto maven.

```bash
mvn site:site
```

Este comando permite generar los casos de prueba del proyecto maven que utiliza el plugin **maven-surefire-plugin.**

```bash
mvn test
```

This command build the project, runs all the test cases and run any checks on the results of the integration tests to ensure quality criteria are met.

```bash
mvn test
```

This command is used to build a project from a different location. We are providing the pom.xml file location to build the project. It’s useful when you have to run a maven build from a script.

```bash
mvn -f maven-example-jar/pom.xml package
```

This command is used to run the maven build in the offline mode. It’s useful when we have all the required JARs download in the local repository and we don’t want Maven to look for any JARs in the remote repository.

```bash
mvn -o package
```

Runs the maven build in the quiet mode, only the test cases results and errors are displayed.

```bash
mvn -q package
```

Prints the maven version and runs the build in the debug mode. It’s opposite of the quiet mode and you will see a lot of debug messages in the console.

```bash
mvn -X package
```

The skipTests system property is used to skip the unit test cases from the build cycle. We can also use **-Dmaven.test.skip=true** to skip the test cases execution.

```bash
mvn -DskipTests package
```
