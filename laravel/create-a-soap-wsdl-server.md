# Soap server with Laravel #

Really quick & dirty notes on how to get a soap working


### Packages ###
```
sudo apt-get update && sudo apt-get install php7.0-soap
 ```
 
### Put  the soap.wsdl under the public folder###


### Create the SoapController ###

```php
<?php

namespace App\Http\Controllers;
use Illuminate\Http\Request;
use Illuminate\Http\Response;
use SoapServer;
use App\Http\Requests;


class SoapController extends Controller
{
    public function soap() {
        $server = new SoapServer('soap.wsdl');
        $server->setClass('App\SoapCompatibility');
        $response = new Response();
        $response->headers->set("Content-Type", "text/xml; charset=utf-8");

        ob_start();
        $server->handle();
        $response->setContent(ob_get_clean());

        return $response;
    }
}
```

### Create the SoapCompatibility class ###

The functions of this class will be called when calling the soap webservice

```php
<?php

/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

namespace App;

use Log;
/**
 * Description of SoapCompatibility
 *
 * @author andrea
 */
class SoapCompatibility {
    const RESULT_OK = "OK";
    const RESULT_KO = "OK";

    public function myFunction($param1, $param2) {
        Log::info("inside myFunction");
        
         return array(
             'items' => '['.$param1.']'.  str_random(16),
             'result' => SoapCompatibility::RESULT_OK
             );
    } 
}
```

### Add the routing ###
```php
Route::group(['prefix' => 'soap/v1'], function () {
    Route::get('CustomWS', 'SoapController@soap');
    Route::post('CustomWS', 'SoapController@soap');
});
```

### Tests ?? ###

Tests don't work at this time probably because phpunit and ob_get_clean doesn't play nicely together.
