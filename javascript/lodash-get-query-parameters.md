## Get all the parameters in the url with lodash/underscore ##
This oneliner is really helpful!
```javascript
_.fromPairs(_.compact(_.map(location.search.slice(1).split('&'), function(item) {  if (item) return item.split('='); })));;
```

it'll return something like
```javascript
{
    post: "2",
    category: "programming",
    language: "coffeescript"
}
```

reference: http://www.timetler.com/2013/11/14/location-search-split-one-liner/