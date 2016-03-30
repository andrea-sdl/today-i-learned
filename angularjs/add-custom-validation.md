# Adding a custom validation to the form #

to add a custom validation you can use a directive with async validators. This way you can do also remote calls.

In the example the debounce also avoid calling the backend too many times (500 means that it will wait 500ms before updating the model, and it resets every time you add data)
```html
<input  type="text" 
        name="username" 
        required
        ng-required="true"
        tabindex="0"
        ng-minlength="6"
        check-username
        ng-model-options="{ updateOn: 'default blur', debounce: { 'default': 500, 'blur': 0 } }"
        ng-model="data.username" 
        >
```

```javascript
.directive('checkUsername', function ($q) {
            return {
                require: 'ngModel',
                link: function (scope, elm, attrs, ctrl) {
                    ctrl.$asyncValidators.checkUsername = function (modelValue, viewValue) {
                        if (ctrl.$isEmpty(modelValue)) {
                            // consider empty model valid
                            return $q.when();
                        }
                        var def = $q.defer();
                        
                        //since it is using promises def.reject/resolve can be called in async ops
                        if (yourcondition==true)
                        {
                            def.reject();
                        }
                        else{
                            def.resolve();
                        }

                        return def.promise;
                    };
                }
            };
        })
```

BTW you can reference _$q_ also in this way

```javascript
.directive('checkUsername', ['$q','YourCustomService',function ($q,myCustomService) {
            //...
        }])
```