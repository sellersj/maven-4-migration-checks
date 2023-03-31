# maven-4-migration-checks

A placeholder and notes about checking projects for moving from maven 3.x to maven 4.x

## Found issues
* many warnings are now errors and will fail the build. e.g. "duplicate declaration of version". Need to clean projects up first
* if a maven profile does not exist, it will fail the build
* [MNG-7752](https://issues.apache.org/jira/browse/MNG-7752) for a weird transitive issue
* any time a resource has a pom that has http as a repo it will fail. Need to see if we can mirror all http to the https mirror of everything we already have in place. [MNG-7733](https://issues.apache.org/jira/browse/MNG-7733)

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

### Dependencies found an issue with
These are either MNG-7752 or MNG-7733
```
Found org.apache.abdera:abdera-extensions-json:jar:0.4.0-incubating is http issue: true pom version: true
Found org.apache.abdera:abdera-extensions-main:jar:0.4.0-incubating is http issue: true pom version: true
Found org.apache.abdera:abdera-parser:jar:0.4.0-incubating is http issue: true pom version: true
Found org.apache.httpcomponents:httpmime:jar:4.0.3 is http issue: false pom version: true
Found org.apache.neethi:neethi:jar:2.0.4 is http issue: true pom version: true
Found org.apache.tiles:tiles-core:jar:2.2.2 is http issue: true pom version: true
Found org.apache.tiles:tiles-jsp:jar:2.2.2 is http issue: false pom version: true
Found org.apache.tiles:tiles-servlet:jar:2.2.2 is http issue: false pom version: true
Found org.apache.tiles:tiles-template:jar:2.2.2 is http issue: false pom version: true
Found org.apache.ws.commons.axiom:axiom-impl:jar:1.2.5 is http issue: true pom version: true
Found org.springframework.security:spring-security-core:jar:2.0.8.RELEASE is http issue: true pom version: true
Found org.springframework.webflow:spring-js:jar:2.3.4.RELEASE is http issue: true pom version: true
Found org.springframework:spring-context-support:jar:4.2.9.RELEASE is http issue: true pom version: false
Found org.springframework:spring-context-support:jar:4.3.14.RELEASE is http issue: true pom version: false
Found org.springframework:spring-context-support:jar:4.3.2.RELEASE is http issue: true pom version: false
Found org.springframework:spring-context-support:jar:4.3.25.RELEASE is http issue: true pom version: false
Found org.springframework:spring-context-support:jar:4.3.30.RELEASE is http issue: true pom version: false
Found org.springframework:spring-context-support:jar:4.3.9.RELEASE is http issue: true pom version: false
Found org.springframework:spring-webmvc:jar:3.2.14.RELEASE is http issue: true pom version: true
Found org.springframework:spring-webmvc:jar:3.2.17.RELEASE is http issue: true pom version: true
Found org.springframework:spring-webmvc:jar:3.2.18.RELEASE is http issue: true pom version: true
Found org.springframework:spring-webmvc:jar:3.2.3.RELEASE is http issue: true pom version: false
Found org.springframework:spring-webmvc:jar:3.2.9.RELEASE is http issue: true pom version: true
Found org.springframework:spring-webmvc:jar:4.1.6.RELEASE is http issue: false pom version: true
Found org.springframework:spring-webmvc:jar:4.2.9.RELEASE is http issue: true pom version: true
Found org.springframework:spring-webmvc:jar:4.3.14.RELEASE is http issue: true pom version: true
Found org.springframework:spring-webmvc:jar:4.3.2.RELEASE is http issue: true pom version: true
Found org.springframework:spring-webmvc:jar:4.3.25.RELEASE is http issue: true pom version: true
Found org.springframework:spring-webmvc:jar:4.3.30.RELEASE is http issue: true pom version: true
```
