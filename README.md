
<bean id="customObjectMapper" class="com.fasterxml.jackson.databind.ObjectMapper">
    <property name="dateFormat">
        <bean class="com.fasterxml.jackson.databind.util.StdDateFormat" />
    </property>
</bean>

<bean class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter">
    <property name="objectMapper" ref="customObjectMapper" />
</bean>

<mvc:annotation-driven>
    <mvc:message-converters>
        <bean class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter">
            <property name="objectMapper" ref="customObjectMapper" />
        </bean>
    </mvc:message-converters>
</mvc:annotation-driven>
