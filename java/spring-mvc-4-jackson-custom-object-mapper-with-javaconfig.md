# Customize the Spring MVC 4 Jackson Object Mapper with JavaConfig #

I needed to configure the jackson object mapper in spring mvc 4, but it didn't seems easy to find the solution with a JavaConfig setup.

The whole point is to have it injected in the javaconfig through the messageconvertes.
**beware** this doesn't automatically change every objectmapper reference, so if you use it elsewhere, you need to reconfigure it again. (I think there's a factory to help in these situations).

```java
@EnableWebMvc
@Configuration
@ComponentScan({"your.package"})
public class SpringWebApiPublicConfig extends AbstractWebApiConfig {

    //..your code

    @Override
    public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {
        converters.add(getCustomJacksonConverter());
        super.configureMessageConverters(converters);
    }

    public MappingJackson2HttpMessageConverter getCustomJacksonConverter(){
        final MappingJackson2HttpMessageConverter converter = new MappingJackson2HttpMessageConverter();
        final ObjectMapper objectMapper = new ObjectMapper();
        objectMapper.configure(SerializationFeature.WRITE_DATE_KEYS_AS_TIMESTAMPS, false);
        objectMapper.configure(SerializationFeature.WRITE_DATES_AS_TIMESTAMPS, false);
        objectMapper.configure(SerializationFeature.WRITE_DATE_TIMESTAMPS_AS_NANOSECONDS, false);
        objectMapper.configure(DeserializationFeature.FAIL_ON_UNKNOWN_PROPERTIES, false);
        converter.setObjectMapper(objectMapper);
        return converter;
    }

}
```