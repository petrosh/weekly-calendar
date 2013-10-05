weekly-calendar
===============

Ideal for nutrition charts!

Functions
---------

- Display last calendar  
- Start another chart by picking a starting date
- Access to older charts

Plugins
-------

- [glDatePicker](https://github.com/glad/glDatePicker)
    To pickup a starting date   

- [store.js](https://github.com/marcuswestin/store.js)
    To store charts

Php
---

Get date and make array

```php
$cosa=strtotime($date);
//$result.='## '.date('Y',$cosa)."\n\n";
$nextWeek = (7 * 24 * 60 * 60);
$ora=$cosa;
for ($i=0; $i <19 ; $i++) { 
	if($i<10)$g='0'.$i; else $g=$i;
	$result.="	w$g ".date('d/F/Y',$ora)."\n";
	$ora+=$nextWeek;
}
```

output

```
w00 09/October/2013
w01 16/October/2013

...

w18 11/February/2014
```