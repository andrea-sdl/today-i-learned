## Fix Google ReCaptcha not working on Internet Explorer 11 if using Bootstrap Modal##

Google Recaptcha has a [strange behaviour on IE11 if using bootstrap](http://jsbin.com/paxaqilupi).
The issues is caused by the boostrap modal enforce focus.

A quick solution to this issue is to disable the enforceFocus entirely by using this code ( [original source](http://stackoverflow.com/questions/27886618/problems-with-new-google-recaptcha-in-ie-when-inside-modal-or-dialog/28965638#28965638) )

```javascript
$.fn.modal.Constructor.prototype.enforceFocus = function () { };
```