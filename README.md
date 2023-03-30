# maven-4-migration-checks

A placeholder and notes about checking projects for moving from maven 3.x to maven 4.x

## Found issues
* many warnings are now errors and will fail the build. e.g. "duplicate declaration of version". Need to clean projects up first
* if a maven profile does not exist, it will fail the build
* [MNG-7752](https://issues.apache.org/jira/browse/MNG-7752) for a weird transitive issue
* 

## Needs more investigation
### Copy plugin
```
<plugin>
  <groupId>com.coderplus.maven.plugins</groupId>
  <artifactId>copy-rename-maven-plugin</artifactId>
  <version>1.0.1</version>
</plugin>
```
### Site plugin
site:3.12.1:attach-descriptor 
`[Parameter 'localRepository' is deprecated core expression; Avoid use of ArtifactRepository type.`