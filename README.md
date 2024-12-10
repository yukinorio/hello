```
<bean id="customObjectMapper" class="com.fasterxml.jackson.databind.ObjectMapper" factory-method="registerJavaTimeModule">
    <property name="dateFormat">
        <bean class="com.fasterxml.jackson.databind.util.StdDateFormat" />
    </property>
</bean>

<bean id="registerJavaTimeModule" class="com.fasterxml.jackson.databind.ObjectMapper" factory-method="registerModule">
    <constructor-arg>
        <bean class="com.fasterxml.jackson.datatype.jsr310.JavaTimeModule" />
    </constructor-arg>
</bean>

<mvc:annotation-driven>
    <mvc:message-converters>
        <bean class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter">
            <property name="objectMapper" ref="customObjectMapper" />
        </bean>
    </mvc:message-converters>
</mvc:annotation-driven>

```
