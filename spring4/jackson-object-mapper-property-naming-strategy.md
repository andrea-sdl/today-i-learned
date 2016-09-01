# Add custom naming strategy for Jackson with Spring REST


```java
    public static final PropertyNamingStrategy CUSTOM_CAMEL_CASE = new CustomCamelCaseStrategy();
    public MappingJackson2HttpMessageConverter getCustomJacksonConverter(){
        final MappingJackson2HttpMessageConverter converter = new MappingJackson2HttpMessageConverter();
        final ObjectMapper objectMapper = new ObjectMapper();
        //setup...

        //set naming strategy
        objectMapper.setPropertyNamingStrategy(CUSTOM_CAMEL_CASE);

        converter.setObjectMapper(objectMapper);
        return converter;
    } 
        

    @Override
    public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {
        converters.add(getCustomJacksonConverter());
        super.configureMessageConverters(converters);
    }
```