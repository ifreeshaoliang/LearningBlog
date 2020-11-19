# <center>Maven</center>
## 介绍
### maven是什么？
它是个项目管理和构建的自动化工具。我们比较关心的是它构建项目的能力。

### maven能干什么
1. **自动下载jar包**：先从本地仓库中找，如果没有，先去中央仓库找，再去远程仓库（有的话），找到就下载到本地仓库，否则抛异常。
2. **处理jar包的依赖**：如果a.jar需要b.jar, maven会自动下载b.jar。
3. **管理jar包版本**，更新jar包等等。
4. **编译java文件**：将java程序编译成.class文件，批量处理的（同时处理成千上百个）。
5. **测试代码**。
6. **打包文件**：打包成jar文件，或者war文件。
7. **部署项目**。

## 使用
ps：默认maven已经安装了

[maven实践-简单项目构建](maven_bulid.md)

[maven常用操作](maven.md)
## 讲解
### maven构建过程
1. 清理：将之前项目编译的东西删除掉，为新编译的代码做准备。
2. 编译：将Java代码编译成.class文件
3. 测试：批量测试程序代码，验证程序正确性。
4. 报告：生成测试报告文件。
5. 打包：将你项目中的所以的class文件和配置文件等所有资源打包到压缩包里，一般是jar包里。
6. 安装：把5中生成的文件jar/war安装到本机仓库。
7. 部署，把程序安装好，可执行。

### maven核心概念
1. [POM](#POM)
2. [约定的目录结构](#约定的目录结构)
3. [坐标](#坐标)
4. [依赖管理](#依赖管理)
5. [仓库管理](#仓库管理)
6. [生命周期](#生命周期)
7. [插件和目标](#插件和目标)
8. [继承](#继承)
9. [聚合](#聚合)

#### POM
POM即project object model，项目对象模型。

```
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
            http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- 基本配置 -->
    <groupId>...</groupId>
    <artifactId>...</artifactId>
    <version>...</version>
    <packaging>...</packaging>


    <!-- 依赖配置 -->
    <dependencies>...</dependencies>
    <parent>...</parent>
    <dependencyManagement>...</dependencyManagement>
    <modules>...</modules>
    <properties>...</properties>

    <!-- 构建配置 -->
    <build>...</build>
    <reporting>...</reporting>

    <!-- 项目信息 -->
    <name>...</name>
    <description>...</description>
    <url>...</url>
    <inceptionYear>...</inceptionYear>
    <licenses>...</licenses>
    <organization>...</organization>
    <developers>...</developers>
    <contributors>...</contributors>

    <!-- 环境设置 -->
    <issueManagement>...</issueManagement>
    <ciManagement>...</ciManagement>
    <mailingLists>...</mailingLists>
    <scm>...</scm>
    <prerequisites>...</prerequisites>
    <repositories>...</repositories>
    <pluginRepositories>...</pluginRepositories>
    <distributionManagement>...</distributionManagement>
    <profiles>...</profiles>
</project>
```


#### 约定的目录结构
每一个maven项目在磁盘里都是一个文件夹(以Hello项目为例)
![](../imges/conventionalDirectoryStructure.jpg)

idea中还会有个.iml文件，它是idae项目的标识文件。iml即infomation  of  module。

在Maven中，项目的依赖关系在pom.xml文件中指定。在IntelliJ IDEA中，即使对于Maven项目，相同的信息也存储在iml文件中。

IDEA并不直接理解Maven模型，它将其转换为所有子系统使用的idea本身的项目模型，所以可以在IDEA中构建/运行/测试/部署/调试Maven项目，而无需使用Maven。它比直接读取Maven模型更快，更容易维护。

#### 坐标
~~~~
<dependencies>
    
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.11</version>
        <scope>test</scope>
    </dependency>
    
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>5.1.9</version>
    </dependency>


</dependencies>
~~~~

在 dependencies 标签中，添加项目需要的 jar 所对应的 maven 坐标。

* dependency：
一个 dependency 标签表示一个坐标

* groupId：
团体、公司、组织机构等等的唯一标识。团体标识的约定是它以创建这个项目的组织名称的逆向域名（例如 org.javaboy）开头。一个 Maven 坐标必须要包含 groupId。一些典型的 groupId 如 apache 的 groupId 是 org.apache.

* artifactId：
相当于在一个组织中项目的唯一标识符。

* version：
一个项目的版本。一个项目的话，可能会有多个版本。如果是正在开发的项目，我们可以给版本号加上一个 SNAPSHOT，表示这是一个快照版（新建项目的默认版本号就是快照版）

* scope：
表示依赖范围。
![](../imges/mavenDependentRange.png)

找依赖要用到jar包，用 mvnrepository.com，下载到本地仓库。

#### 依赖管理

#### 仓库管理

#### 生命周期

#### 插件和目标

#### 继承

#### 聚合
