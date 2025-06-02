# Demo Java Maven Project with CycloneDX SBOM

This is a simple Java Maven project that demonstrates how to generate a [CycloneDX](https://cyclonedx.org/) Software Bill of Materials (SBOM).

---

## 🚀 Project Setup

### 1. Create the Project

Use Maven to generate a basic Java application:

```bash
mvn archetype:generate -DgroupId=com.example \
  -DartifactId=demo-app-sbom \
  -DarchetypeArtifactId=maven-archetype-quickstart \
  -DinteractiveMode=false
cd demo-app-sbom
```

### 2. Add CycloneDX Maven Plugin
Edit your pom.xml and add the CycloneDX plugin inside the <build> section:

``` xml
<build>
  <plugins>
    <plugin>
      <groupId>org.cyclonedx</groupId>
      <artifactId>cyclonedx-maven-plugin</artifactId>
      <version>2.7.9</version>
      <executions>
        <execution>
          <phase>verify</phase>
          <goals>
            <goal>makeBom</goal>
          </goals>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

For JSON output, add this:

``` xml
<configuration>
  <outputFormat>json</outputFormat>
</configuration>
```

### 3. Generate the SBOM
Run the following command:

``` bash
$ mvn clean verify
```

After the build, the SBOM will be located at:

```
target/bom.xml        # or bom.json if using JSON format
```


## License (Testing)

This project is licensed under the [GNU General Public License v3.0](LICENSE).