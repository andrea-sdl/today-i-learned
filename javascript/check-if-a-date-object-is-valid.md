# Check if a date object is valid #

super simple way to check if a date is valid [http://stackoverflow.com/questions/1353684/detecting-an-invalid-date-date-instance-in-javascript?lq=1](source)

```javascript
if ( Object.prototype.toString.call(d) === "[object Date]" ) {
  // it is a date
  if ( isNaN( d.getTime() ) ) {  // d.valueOf() could also work
    // date is not valid
  }
  else {
    // date is valid
  }
}
else {
  // not a date
}
```