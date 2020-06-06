# SimpleMaven
This is a repository for people starting out using maven on the terminal/vim.

## Reason for this project
I am a student that like to figure out things, instead of an Ide that do all of these things for me.  
I did this project because I find it hard to figure all of these things out.


# Mappings for creating maven projects.

These mappigs are for creating maven projects on the terminal.
put this is your `.bashrc` or `.zshrc`
```bash
alias \
	mvnc="mvn archetype:generate -DarchetypeArtifactId=maven-archetype-quickstart" \
	mvnc_fxml_javafx="mvn archetype:generate -DarchetypeGroupId=org.openjfx -DarchetypeArtifactId=javafx-archetype-fxml" \
	mvnc_simple_javafx="mvn archetype:generate -DarchetypeGroupId=org.openjfx -DarchetypeArtifactId=javafx-archetype-simple" 
```

## Screencasting of How to create a maven project
![](video_create_javafx_project.gif)

# How to run maven projects
you have to run this command first `$ mvn clean compile` before you can run most of the projects.  
the command for running a chosen class is like this.  
```bash
$ mvn exec:java -D"exec.mainClass"="org.sample.App"
```

## Screencasting of How to run maven projects   
![](video_run_simple_maven.gif)

# How to test maven projects
run all test
```bash
$ mvn test
```
for testing specific class use this command 
```bash
$ mvn test -Dtest=SomeClassHere
```
## Screencasting of How to test on maven projects


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
