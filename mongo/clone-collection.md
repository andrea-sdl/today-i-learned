# How to clone a collection #

Very fast and efficient way ;)

```javascript
db.myoriginal.aggregate([ { $out: "mycopy" } ])
```