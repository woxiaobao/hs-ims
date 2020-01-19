### 项目架构

版本统一管理，解决项目直接的依赖

当前版本test
当前版本test
当前版本test
当前版本test
当前版本test


#### 文件目录

```yaml
└── sources
    ├── basics
    │   ├── common
    │   │   
    │   ├── demo-api
    │       
    ├── parent
    │   └── pom.xml
    └── service
        ├── demo-server
── pom.xml

```

- 最外层的pom.xml

```yaml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.fais.hs.manage</groupId>
    <artifactId>ims-build</artifactId>
    <name>a系统</name>
    <packaging>pom</packaging>
    <version>1.0.0-SNAPSHOT</version>

    <properties>
    </properties>

    <modules>
        <module>sources/parent</module>
        <module>sources/basics/demo-api</module>
        <module>sources/basics/common</module>
        <module>sources/service/demo-server</module>
    </modules>

</project>
```

- parent 中的pom.xml
```yaml
<?xml version="1.0" encoding="UTF-8"?>
<project>
    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.3.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

    <groupId>com.fais.hs.manage</groupId>
    <artifactId>parent</artifactId>
    <name>系统父工程</name>
    <packaging>pom</packaging>
    <version>1.0.0-SNAPSHOT</version>

    <properties>
        <fais.version>1.0.0-SNAPSHOT</fais.version>
    </properties>

    <dependencyManagement>
        <dependencies>

        </dependencies>
    </dependencyManagement>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
        </dependency>
        
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <!--<repositories>-->
        <!--<repository>-->
            <!--<id>trc</id>-->
            <!--<url>http://121.41.17.205:18081/nexus/content/groups/public/</url>-->
            <!--<releases>-->
                <!--<enabled>true</enabled>-->
            <!--</releases>-->
            <!--<snapshots>-->
                <!--<enabled>true</enabled>-->
                <!--<updatePolicy>always</updatePolicy>-->
                <!--<checksumPolicy>warn</checksumPolicy>-->
            <!--</snapshots>-->
        <!--</repository>-->
    <!--</repositories>-->
</project>

```

- demo-server中的pom.xml的依赖关系
```yaml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>ims-build</artifactId>
        <groupId>com.fais.hs.manage</groupId>
        <version>1.0.0-SNAPSHOT</version>
        <relativePath>../../../pom.xml</relativePath>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>demo-server</artifactId>
    <name>demo-service</name>
    <packaging>jar</packaging>
    <version>${fais.version}</version>

    <dependencies>
        <dependency>
            <groupId>com.fais.hs.manage</groupId>
            <artifactId>common</artifactId>
            <version>${fais.version}</version>
        </dependency>
        <dependency>
            <groupId>com.fais.hs.manage</groupId>
            <artifactId>demo-api</artifactId>
            <version>${fais.version}</version>
        </dependency>
    </dependencies>
</project>
```
