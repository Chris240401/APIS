Hi , Mi nombre es Christian Ramírez La programación es un lenguaje universal que te permite crear software, aplicaciones y sitios web. Puedes aprender diferentes lenguajes de programación

presento mi proyecto

** Ejercicio de Automatización E2E **

⏩ Comience Comience a usar VS Code, IntelliJ, Maven, Gradle, NPM, GitHub Codespaces, Docker o la línea de comandos

💡 Ejemplos Ejemplos y demostraciones de integraciones con otros frameworks.

📺 Vídeos de inicio rápido Guías paso a paso para principiantes para empezar desde cero Kárate Automatización de pruebas realizadaSimple.

Karate es la única herramienta de código abierto que combina la automatización de pruebas de API, simulacros , pruebas de rendimiento e incluso la automatización de la interfaz de usuario en un marco único y unificado . La sintaxis es neutral en cuanto al lenguaje y fácil incluso para quienes no son programadores. Las afirmaciones y los informes HTML están integrados y puede ejecutar pruebas en paralelo para mayor velocidad.

También hay un ejecutable independiente multiplataforma para equipos que no se sienten cómodos con Java. No es necesario compilar el código. Simplemente escriba pruebas en una sintaxis simple y legible , cuidadosamente diseñada para HTTP, JSON, GraphQL y XML. Y puede combinar la automatización de pruebas de API y UI dentro del mismo script de prueba.

También existe una API de Java para aquellos que prefieren integrar mediante programación las ricas capacidades de automatización y afirmación de datos de Karate.

image

Características

-Basado en el popular estándar Cucumber/Gherkin, con soporte IDE y opciones de coloración de sintaxis -No se requieren conocimientos de Java e incluso los no programadores pueden escribir pruebas. -Los scripts son texto sin formato, no requieren ningún paso de compilación ni IDE, y los equipos pueden colaborar utilizando Git/SCM estándar.

Referencias Pruebas API con Karate : vídeo + demostraciones de Peter Thomas (creador/desarrollador principal de Karate) Introducción a todas las funciones de Karate : vídeo + demostraciones de Peter Thomas (creador/desarrollador principal de Karate)

Empezando Si es un desarrollador de Java, Karate requiere al menos Java 11 y luego Maven , Gradle o un IDE de Java que incorpore cualquiera de ellos para poder instalarse. Tenga en cuenta que Karate funciona bien en OpenJDK.

Si es nuevo en la programación o la automatización de pruebas, se recomienda el complemento oficial de IntelliJ .

Si no desea utilizar Java, se recomienda la extensión Karate para Visual Studio Code , y los programadores de JavaScript, .NET, Ruby y Python se sentirán como en casa.

Tanto el complemento oficial de Visual Studio Code como el de IntelliJ admiten la depuración paso a paso de las pruebas de Karate.

experto Todo lo que necesitas está disponible en el karate-coreartefacto. Puede ejecutar pruebas con esto directamente , pero los equipos pueden elegir la variante JUnit (que se muestra a continuación) que incorpora JUnit 5 y mejora ligeramente la experiencia en IDE .

com.intuit.karate karate-junit5 1.4.1 test Gradle Alternativamente para Gradle :
testCompile 'com.intuit.karate:karate-junit5:1.4.1'
Consulte también la wiki para saber cómo usar Karate con Gradle .

Núcleo de Karate "Fat JAR" Si mezcla Karate en un proyecto Maven o Gradle con muchas otras dependencias, puede tener problemas debido a conflictos de dependencias. Por ejemplo, muchos proyectos Java dependen directa (o indirectamente) de Netty, Thymeleaf o ANTLR, etc.

Si enfrenta problemas como "clase no encontrada", simplemente ingrese la karate-coredependencia y use el all clasificador en su pom.xml(o build.gradle).

Por ejemplo, cuando se utiliza Maven:

com.intuit.karate karate-core ${karate.version} all test Tenga en cuenta que para proyectos muy complicados puede considerar usar un perfil de Maven para que las dependencias relacionadas con las pruebas no choquen con sus dependencias en tiempo de desarrollo. Por supuesto, es una opción tener las pruebas de Karate en un proyecto y una carpeta independientes de Maven, sin dejar de estar en el mismo repositorio de Git.
Inicio rápido Puede que le resulte más fácil utilizar el arquetipo Karate Maven para crear un proyecto de esqueleto con un solo comando. Luego puede omitir las siguientes secciones, ya que se crearán para usted la pom.xmlestructura de directorios recomendada, la prueba de muestra y los corredores JUnit 5 .

Si está detrás de un proxy corporativo, o especialmente si su instalación local de Maven ha sido configurada para apuntar a un repositorio dentro de su red local, es posible que el siguiente comando no funcione. Una solución alternativa es desactivar temporalmente o cambiar el nombre de su settings.xmlarchivo Maven y volver a intentarlo.

Puede reemplazar los valores de com.mycompanyy myprojectsegún sus necesidades.

mvn archetype:generate
-DarchetypeGroupId=com.intuit.karate
-DarchetypeArtifactId=karate-archetype
-DarchetypeVersion=1.4.1
-DgroupId=com.mycompany
-DartifactId=myproject Esto creará una carpeta llamada myproject(o el nombre que le hayas asignado).

Soporte IDE Consulte la wiki- IDE Support .

Estructura de carpetas Un script de prueba de Karate tiene la extensión de archivo .featureque es el estándar seguido de Cucumber. Eres libre de organizar tus archivos utilizando las convenciones habituales de paquetes de Java.

La tradición de Maven es tener archivos fuente que no sean Java en una src/test/resourcesestructura de carpetas separada, pero le recomendamos que los mantenga al lado de sus *.javaarchivos. Cuando tiene un proyecto grande y complejo, terminará con algunos archivos de datos (por ejemplo *.js, *.json, *.txt) también y es mucho más conveniente ver los archivos *.javay *.featurey todos los artefactos relacionados en el mismo lugar.

Esto se puede lograr fácilmente con el siguiente ajuste en su sección maven.

src/test/java **/*.java ... Esto es muy común en el mundo de los usuarios de Maven y tenga en cuenta que se trata de pruebas y no de código de producción.
Alternativamente, si usa Gradle, agregue la siguiente sourceSetsdefinición

sourceSets { test { resources { srcDir file('src/test/java') exclude '**/*.java' } } } Con lo anterior implementado, no tiene que seguir cambiando entre sus carpetas src/test/javay src/test/resources, puede tener todos sus códigos de prueba y artefactos debajo src/test/javay todo funcionará como se esperaba.

Una vez que te acostumbres a esto, es posible que incluso empieces a preguntarte por qué los proyectos necesitan una src/test/resourcescarpeta.

Ejemplo de arranque de primavera Soumendra Daas ha creado un buen ejemplo y una guía que puedes utilizar como referencia aquí: hello-karate. Esto demuestra un proyecto Java Maven + JUnit 5 configurado para probar una aplicación Spring Boot .

Convenciones de nombres Dado que se trata de pruebas y no de código Java de producción, no necesita estar sujeto a la com.mycompany.foo.barconvención ni a la explosión innecesaria de subcarpetas que se produce. Le sugerimos que tenga una jerarquía de carpetas de solo uno o dos niveles de profundidad, donde los nombres de las carpetas identifiquen claramente qué 'recurso', 'entidad' o API es el servicio web bajo prueba.

Por ejemplo:

src/test/java | +-- karate-config.js +-- logback-test.xml +-- some-reusable.feature +-- some-classpath-function.js +-- some-classpath-payload.json | -- animals | +-- AnimalsTest.java | +-- cats | | | +-- cats-post.feature | +-- cats-get.feature | +-- cat.json | -- CatsRunner.java | -- dogs | +-- dog-crud.feature +-- dog.json +-- some-helper-function.js -- DogsRunner.java Suponiendo que utiliza JUnit, existen algunas buenas razones para la convención de nomenclatura recomendada (mejor práctica) y la elección de ubicación de archivos que se muestran arriba:

No utilizar la *Test.javaconvención para las clases JUnit (por ejemplo CatsRunner.java, ) en la carpeta catsy dogsgarantiza que estas pruebas no se recogerán al invocar mvn test(para todo el proyecto) desde la línea de comando . Pero aún puedes invocar estas pruebas desde el IDE, lo cual es conveniente cuando estás en modo de desarrollo. AnimalsTest.java(el único archivo que sigue la *Test.javaconvención de nomenclatura) actúa como el 'conjunto de pruebas' para todo el proyecto. De forma predeterminada, Karate también cargará todos *.featurelos archivos de los subdirectorios. Pero como some-reusable.featureestá arriba AnimalsTest.java en la jerarquía de carpetas, no será recogido. Que es exactamente lo que queremos, porque some-reusable.featureestá diseñado para ser llamado sólo desde uno de los otros scripts de prueba (quizás pasando algunos parámetros). También puede utilizar etiquetas para omitir archivos. some-classpath-function.jsy some-classpath-payload.jsonestán en la 'raíz' del 'classpath' de Java , lo que significa que pueden leerse (y reutilizarse) fácilmente desde cualquier script de prueba utilizando el classpath:prefijo, por ejemplo: read('classpath:some-classpath-function.js'). Las rutas relativas también funcionarán. Para obtener detalles sobre lo que realmente incluye un script o *.featurearchivo, consulte la guía de sintaxis .

Unidad 5 Karate es compatible con JUnit 5 y la ventaja es que puedes tener múltiples métodos en una clase de prueba. Solo se necesita 1 importy, en lugar de una anotación a nivel de clase, se utiliza una API DRY y fluida para expresar qué pruebas y etiquetas desea usar.

Tenga en cuenta que la clase Java no necesita serlo publice incluso los métodos de prueba no necesitan serlo public, por lo que las pruebas terminan siendo muy concisas.

Karate recorrerá subdirectorios y buscará *.featurearchivos. Por ejemplo, si tiene la clase JUnit en el com.mycompanypaquete, también se ejecutarán *.featurelos archivos en com.mycompany.fooy . com.mycompany.barÉsta es una de las razones por las que es posible que desee preferir una estructura de directorios "plana" como se explicó anteriormente .
