# hibernate4-java8

Provides support for java8 DateTime api (JSR-310) for hibernate4 applications started in java8 enviroment.

Supports following classes:
- java.time.Instant
- java.time.LocalDateTime
- java.time.LocalDate
- java.time.LocalTime
- java.time.OffsetDateTime
- java.time.OffsetTime
- java.time.ZonedDateTime


This library is simple copy-paste port (with import fixes) of original hibernate-java8 module from Hibernate5 source base.

Using this library will decrease switching cost to pure Hibernate5. Same code works well with Hibernate5 with
hibernate-java8 module from it.


Have been tested on Wildfly9. Works well with envers (despite of JPA-Convertors which are not working with it)


## Usage:

Simply add the jar to  `$WILDFLY_HOME/modules/system/layers/base/org/hibernate/main` and register in module.xml:

```xml
<module xmlns="urn:jboss:module:1.3" name="org.hibernate">
    <resources>
        <resource-root path="hibernate-core-4.3.11.Final.jar"/>
        <resource-root path="hibernate-envers-4.3.11.Final.jar"/>
        <resource-root path="hibernate-entitymanager-4.3.11.Final.jar"/>
		<resource-root path="hibernate4-java8-4.3.11.Final.jar" />
    </resources>

    <dependencies>
        <module name="asm.asm"/>
        <module name="com.fasterxml.classmate"/>
        <module name="javax.api"/>
        <module name="javax.annotation.api"/>
        <module name="javax.enterprise.api"/>
        <module name="javax.persistence.api"/>
        <module name="javax.transaction.api"/>
        <module name="javax.validation.api"/>
        <module name="javax.xml.bind.api"/>
        <module name="org.antlr"/>
        <module name="org.apache.commons.collections"/>
        <module name="org.dom4j"/>
        <module name="org.javassist"/>
        <module name="org.jboss.as.jpa.spi"/>
        <module name="org.jboss.jandex"/>
        <module name="org.jboss.logging"/>
        <module name="org.jboss.vfs"/>
        <module name="org.hibernate.commons-annotations"/>
        <module name="org.hibernate.infinispan" services="import" optional="true"/>
        <module name="org.hibernate.jipijapa-hibernate4-3" services="import"/>
    </dependencies>
</module>
```


and in entities add references to proper types via hibernate's `@Type` annotations