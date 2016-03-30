# Set the value of an hidden input field #

To set the value of an hidden input field you need to use the ng-value and bind it to a value in the scope (in this case I'm interested in the myData object)

```html
<input type="hidden" name="user_id" id="user_id" ng-value="myData.userId">
```