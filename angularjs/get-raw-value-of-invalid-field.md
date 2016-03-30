# Get the Raw Value of an Invalid field #

If you have form validation active, then the value of the input field isn't propagated to the ng-model until it's valid.

If you want to show the value of the field itself (for example if you want to preview it) you can simply use
```javascript
form.field_name.$viewValue
```