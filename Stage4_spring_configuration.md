# Stage 4 - Spring MVC
Spring MVC dependency:

Add this to the `<dependencies>` tag in */pom.xml*

```xml
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>4.2.2.RELEASE</version>
		</dependency>
```

Add **DispatcherServlet** to *web.xml*:

```xml
	    <servlet>
	        <servlet-name>dispatcher</servlet-name>
	        <servlet-class>
	            org.springframework.web.servlet.DispatcherServlet
	        </servlet-class>
	        <init-param>
	            <param-name>contextConfigLocation</param-name>
	            <param-value>/WEB-INF/todo-servlet.xml</param-value>
	        </init-param>
	        <load-on-startup>1</load-on-startup>
	    </servlet>
	
	    <servlet-mapping>
	        <servlet-name>dispatcher</servlet-name>
	        <url-pattern>/spring-mvc/*</url-pattern>
	    </servlet-mapping>
```

*/WEB-INF/todo-servlet.xml:*

```xml

<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:context="http://www.springframework.org/schema/context"
	xmlns:mvc="http://www.springframework.org/schema/mvc" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-4.0.xsd
	    http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc-4.0.xsd
	    http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-4.0.xsd">

	<context:component-scan base-package="com.johnbryce" />

	<mvc:annotation-driven />

</beans>
```

A **ViewResolver**, add it inside */WEB-INF/todo-servlet.xml* after the `<context:component-scan base-package="com.johnbryce" />` tag.

```xml
  <bean
        class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix">
            <value>/WEB-INF/views/</value>
        </property>
        <property name="suffix">
            <value>.jsp</value>
        </property>
    </bean>
```
