# maven-4-migration-checks

A placeholder and notes about checking projects for moving from maven 3.x to maven 4.x

## Found issues
* many warnings are now errors and will fail the build. e.g. "duplicate declaration of version". Need to clean projects up first
* if a maven profile does not exist, it will fail the build
* [MNG-7752](https://issues.apache.org/jira/browse/MNG-7752) for a weird transitive issue
* any time a resource has a pom that has http as a repo it will fail. Need to see if we can mirror all http to the https mirror of everything we already have in place

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
`[Parameter 'localRepository' is deprecated core expression; Avoid use of ArtifactRepository type.`

for 
* site:3.12.1:attach-descriptor 
* checkstyle:3.2.1:checkstyle
