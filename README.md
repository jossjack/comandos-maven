# Maven

## Instalacion

### Ubuntu
1. Descargar Maven desde https://maven.apache.org/download.cgi
2. Descomprime la carpeta en alguna ubicación de tu preferencia.
3. En mi caso la he descomprimido y luego copiado en /opt/maven3/ de esta forma
```bash
cp -r /home/myuser/Downloads/apache-maven-3.3.3/ /opt/maven3/
```
4. Agrega el directorio de maven al PATH y crea una variable de entorno M2_HOME
5. Como pre-requisito deberas tener instalado Java y definida la variable de entorno JAVA_HOME
6. Editar archivo .bashrc de tu user con el comando vi ~/.bashrc
```bash
export M2_HOME="/opt/maven3"
export JAVA_HOME="/usr/lib/jvm/default-java"
export PATH=$PATH:$M2_HOME/bin:$JAVA_HOME/bin
```
7.Refresca el PATH y la variable desde una consola ejecutando el comando
```bash
source ~/.bashrc
```
8. Validar que se haya instalado correctamente verficando la version de Maven
```bash
mvn --version
```

Deberias tener una salida similar a esta:
```bash
Apache Maven 3.6.3
Maven home: /usr/share/maven
Java version: 1.8.0_265, vendor: Private Build, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
Default locale: es_EC, platform encoding: UTF-8
OS name: "linux", version: "5.4.0-51-generic", arch: "amd64", family: "unix"
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
