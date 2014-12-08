#Slim with minimal modifications

Fork of the original micro framework Slim with minimal modifications.

###Modification
./Route.php@462
```
-        $return = call_user_func_array($this->getCallable(), array_values($this->getParams()));
+        $return = call_user_func_array($this->getCallable(), array(0=>$this->getParams()));
```
##Example
This modification will return an associative array.

###index.php
```php
$app->get('/hello/:myFirstIndex/:mySecondIndex', function($params) {
  print_r($params);
});
```

###Request
```
GET /hello/foo/bar HTTP/1.1
```

###Output
```
Array
(
    [myFirstIndex] => foo
    [mySecondIndex] => bar
)
```
