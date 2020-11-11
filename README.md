# maven-quick-start
Sample project to use with Maven Quick Start

Maven: Building Blocks
* Three Main Groups
    * Goals
    * Phases
    * Lifecycles

Maven: Goals
* Like Ant task
* Plugin + goal name
* Example: compile goal on Compiler plugin

Maven: Phases
* One or Many Goals
    * Part of Greater Lifecycle
* Example
    * compile maps to compiler:compile

Maven: Lifecycles
Jar Lifecycle      "collection of Phases"

- compile
- test
- package
- install
- deploy

Putting it Together

* Lifecycles contain Phases
* Phases map to Goals
* Many Lifecycles
* Based on Maven Project
* Enterprise Application vs Simple Jar

mkdir -p src/main/java
mkdir -p src/main/resources
mkdir -p src/test/java
mkdir -p src/test/resources

touch src/main/java/.gitkeep
touch src/main/resources/.gitkeep
touch src/test/java/.gitkeep
touch src/test/resources/.gitkeep

cd src/main/java
mkdir -p clinic/programming/training
touch Application.java
cd ../../..
mvn package

cd /Users/timurdjumaev/maven-quick-start/target/
# our maven-quick-start-1.0.jar has been created in target subdir.
# we can run it by:         #where cp is classpass 
java -cp maven-quick-start-1.0.jar clinic.programming.training.Application
# Output:
Starting Application
Inside Application 

# Cleaning our project work space / Cleaning previous Build Output
~/maven-quick-start  main ?4
mvn clean
# Clean lifycycle is completely sepated from jar lifecycle, target folder has been removed

# Multiple Goals and Phases in Single Build
# The following command executes clean lifecycle by removing previous build and then trigers a new Phase of Jar lyfecycle
mvn clean package

# The following command will copy jar file out of target directory and place it into special
# location known as local maven repository (LOCAL CACHE OF VARIOUS BUILDS AND ARTIFACTS)
mvn clean install
# Output:
[INFO] Installing /Users/timurdjumaev/maven-quick-start/target/maven-quick-start-1.0.jar to /Users/timurdjumaev/.m2/repository/clinic/programming/maven-quick-start/1.0/maven-quick-start-1.0.jar
[INFO] Installing /Users/timurdjumaev/maven-quick-start/pom.xml to /Users/timurdjumaev/.m2/repository/clinic/programming/maven-quick-start/1.0/maven-quick-start-1.0.pom



 # MAVEN PLUGINS - a way to exhance or extend or change the way MAVEN works
* Critical Part of Maven
* Everything
    * Default/Core Functionality
    * Additional Functionality
* Maven = Plugin Engine
    * Plugins Implement Functionality
    * Add more Goals
* Plugins Are Dependencies
    * Download from Repositories

* Plugin Examples:
    - Compile Source Code
    - Run Unit Test
    - Publish to Artifact Repository
    - Deploy to Remote Server
    - Publish Documentation
    - Much more

* Basic Set
* Common/Core
    - Known to Maven
    - Downloaded Upon Reference
* Others
    - Mentioned in Project POM
* Changed Plugin Behavior
    - Specify in POM Configuration

# MAVEN DEPENDENCIES
* Dependancy Management
* Finding Dependencies (External Repositories)
* Controling When Used (Scoped)
# The main strength of Maven is Dependency Manegement.
- Just specify the main dependency of the project and Maven will automatically find any additional dependancies
- By default MAVEN is configured to resolved dependancies from Maven Central repo online, however additional repositories can be configured also
- Maven will look at Local private repo first wich acts like a cache
- When specifying the dependancy we must determine which scope deploys dependancy for our project
- Maven supports 6 Scopes, 4 commonly used:
    - Compile:
        * Default
        * Compilation and Execution
        * Added to Dependancy Projects
        * Included in Containers (war/ear)
    - Runtime:
        * Deployment/Runtime
        * Not required for Compilation
        * Included in Containers (war/ear)
    - Test:
        * Testing only
        * Not needed for compilation, deployment/runtime
    - Provided:
        * Provided by Target: Web Application, Application Server
    - System:
        * Rarely used
        * Local Dependencies - Lib Folder
        * Not recommended, unless Extreme Scenario
    - Import:
        * Rarely used, almost never
        * Specialized cases
        * Replace Dependencies


# The command below will show how dependencies resolve against each other                    
mvn dependency:tree
mvn dependency:tree > dependency-list.txt

# TESTING

cd /Users/timurdjumaev/maven-quick-start/src/test/java
mkdir -p clinic/programming/training
cd clinic/programming/training
nano ApplicationTest.java

We also need to update our POM by adding snippet of junit:junit:
4.13.1	from Maven Central Repo https://search.maven.org/artifact/junit/junit/4.13.1/jar

<dependency>
  <groupId>junit</groupId>
  <artifactId>junit</artifactId>
  <version>4.13.1</version>
</dependency>

After saving our POM file we can run the test by:

mvn test (Maven compiles and tests our source code)
mvm clean install

Now when the test is run you can go to ~/maven-quick-start/target/surefire-reports and see the report of testing!



# The project structure can be generated by using Maven Archetype
https://maven.apache.org/archetypes/maven-archetype-quickstart/

mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4


 

