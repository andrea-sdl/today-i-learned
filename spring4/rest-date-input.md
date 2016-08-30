# Convert a Date input in a object passed in GET

A quick way to pass an object in GET is to use the ModelAttribute annotation.
This way the request parameters will get mapped onto the bean props if they match.


```java
    @RequestMapping(method = {RequestMethod.GET})
    public RestResponseV2<DashboardResults> list(@ModelAttribute DateSearchQuery searchQuery) {
    }
```

The DateSearchQuery object contains 2 dates object which can be converted thanks to the DateTimeFormat, both by using the pattern, or the iso attribute.

```java
public class DateSearchQuery {
    
    @DateTimeFormat(iso=DateTimeFormat.ISO.DATE)
    private Date from;
    @DateTimeFormat(pattern='yyyy-MM-dd')
    private Date to;

    public Date getFrom() {
        return from;
    }

    public void setFrom(Date from) {
        this.from = from;
    }

    public Date getTo() {
        return to;
    }

    public void setTo(Date to) {
        this.to = to;
    }
}
```