# refreshing-maven

```
Seeing the content of parent pom along with child pom
  - mvn help:effective-pom
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
