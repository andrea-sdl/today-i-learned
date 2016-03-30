# Print validation error with ng-messages #

NgMessages is really nice, once you put it you can also choose the order of the validation (which is the same as the one showed in the divs.)
this example also shows how you'd interact with a custom validation.

Please note that _checkUsername_ isn't automatically mapped by angular but it's added by us with the JS code _ctrl.$asyncValidators.checkUsername_
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
                   
    <div ng-messages="myForm.username.$error" ng-show="myForm.username.$invalid && myForm.username.$dirty" class="register-error-div">
        <div ng-message="required" >Username not found</div>
        <div ng-message="minlength">Username too short</div>
        <div ng-message="checkUsername">User already present</div>
    </div>
```