# refreshing-maven

```
USe tcf terminal plugin in eclipse to use command line terminal and execute maven jobs.
```

```
Seeing the content of parent pom along with child pom
  - mvn help:effective-pom
```

```
Standard Maven directory structure

https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html

src/main/java
    --- java source code
    
src/main/resources
    --- configuration files like log4j.xml,.properties, etc
    
src/test/java
    --- jnuit test classess
    
src/test/resources
    --- test resources
    
To override these standard locations

update build tag in pom

eg 

<build>
  <sourceDirectory>src/nonstandard/java</sourceDirectory>
  <target>myTarget</target>
</build>

```

```
Profiles

  <profiles>
		<profile>
      <id>production_id</id>
      <build>
      	<directory>production</directory>
      </build>
    </profile>
    
    
    mvn -Pproduction_id package  --- runnuing through command line
    
    
    other way through activation
    
    <profiles>
		<profile>
      <id>production</id>
      <activation>
      	<!-- Use any of the below activation types -->
      	<!-->activeByDefault></activeByDefault -->
      	<!--file></file-->
      	<!--jdk></jdk-->
      	<!--os></os-->
      	<property>
      		<name>env.JAVA_HOME</name>
      		<value>/opt/java</value>
      	</property>
      </activation>
      <build>
      	<directory>production</directory>
      </build>
    </profile>

```

```
Manually running a Plugin and it's goal

  - mvn compiler:compile
```

```
To see details of specific plugin eg compiler plugin
  - -D is taking name if the specific plugin
 - mvn help:describe -Dplugin=compiler
 
To see details of specific plugin goal eg compile goal of compiler plugin: It will also show all properties associated with the plugin goal
  - mvn help:describe -Dcmd=compiler:compile -Ddetail
  
To specify property for a plugin goal through command line
 
 -mvn compiler:compile -Dmaven.compiler.verbose=true
 
To set property for a plugin goal through pom definition eg verbose property

<build>
<pluginManagement>
  <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.2</version>
        <configguration>
          <verbose>true</verbose>
        </configguration>
      </plugin>        
  </plugins>
</pluginManagement>
</build> 
```

```
To see 'goal' details of compiler plugin
  - Here help is a goal of compiler plugin
  - -D is used to passed parameters

mvn compiler:help -Ddetail=true -Dgoal=compile
```

```
Building custom plugins
  Below command will generate project to create custom plugin
mvn archetype:create -DgroupId= -DartifactId= -DarchetypeArtifactId=maven-archetype-mojo -DarchetypeGroupId=org.apache.maven.archetypes

```
