# Simple Maven that is not so simple
This is a repository for people starting out using maven on the terminal/vim.

## Reason for this project
I am a student that like to figure out things, instead of using an IDE that do all of these things for me.  
I did this project because I find it hard to find any information on maven.


# Aliases for creating maven projects.

These aliases are for creating maven projects on the terminal.  
put this is your `.bashrc` or `.zshrc`
```bash
alias \
	mvnc="mvn archetype:generate -DarchetypeArtifactId=maven-archetype-quickstart" \
	mvnc_fxml_javafx="mvn archetype:generate -DarchetypeGroupId=org.openjfx -DarchetypeArtifactId=javafx-archetype-fxml" \
	mvnc_simple_javafx="mvn archetype:generate -DarchetypeGroupId=org.openjfx -DarchetypeArtifactId=javafx-archetype-simple" 
```

## Screencasting of How to create a maven project
![](res/video_create_javafx.gif)

# How to run maven projects
The command for running a chosen main class is like this.  
```bash
$ mvn clean compile exec:java -D"exec.mainClass"="org.sample.App"
```

The `mvncr` can find and list java main classes you can the chose
what main class to run.
If you copy it into a file remember too  to make it executable 
`$ chmod +x mvncr`
You can run it with command auguments like `mvncr run` or `mvncr compile` or `mvncr clean`.
If you do not write anything it will automatically do a clean compile.
```bash
#!/bin/bash

# A tool to find main classes in a maven project.
# the tool compiles the project and then launch the chosen main class.
# The script should be launch in a directory with a `pom.xml` file.

# Seperated by spaces
javaMainClassList=$(grep -r "public static void main" . | \
    sed -e "s,..src/main/java/,,g;\
    s,.java: * public static void main(String\[] args) .*,,g; \
    s,/,\.,g;")

PS3='Please select java class to run: '
select opt in $javaMainClassList
do
    case "$1" in
        "run")
            printf '\x1b[31m %b \x1b[m' "\nrunning: $opt \n\n"
            mvn clean compile exec:java "-Dexec.mainClass=$opt"
            break
            ;;
        "compile")
            printf '\x1b[34m %b \x1b[m' "\ncompile and running: $opt \n\n"
            mvn compile exec:java "-Dexec.mainClass=$opt"
            break
            ;;
        "clean"|*)
            printf '\x1b[35m %b \x1b[m' "\nclean, compile and running: $opt \n\n"
            mvn clean compile exec:java "-Dexec.mainClass=$opt"
            break ;;
    esac
done
```


# How to compile a .jar file
```bash
$ mvn clean install 
```
This runs test and then compiling to the jar file that will be located at `target/someJarfile.jar`

## Screencasting of How to run maven projects   
![](res/video_run_javafx.gif)

# How to test maven projects
run all test
```bash
$ mvn test
```
for testing specific class use this command 
```bash
$ mvn test -Dtest=SomeClassHere
```


# How to figure out dependencies management
All the dependencies will be in your `pom.xml` file.  
the section in your `pom.xml` file should look like this with dependencies.   
```xml
    <dependencies>

        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter</artifactId>
            <version>5.5.2</version>
            <scope>test</scope>
        </dependency>

        <dependency>
            <groupId>org.json</groupId>
            <artifactId>json</artifactId>
            <version>20190722</version>
        </dependency>

    </dependencies>
```
If you know html, you can figure out how to add more dependencies.  
for finding libs/dependencies use this website [mvnrepository.com](https://mvnrepository.com/).  


### If you are new to the terminal and other FAQ
The dollar sign `$` means run as a normal user.  
The hashtag sign `#` means run as a super user/root.  
libs means library  

### Pull request are welcome
