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

