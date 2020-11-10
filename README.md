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


