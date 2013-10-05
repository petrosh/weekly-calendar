weekly-calendar
===============

Ideal for nutrition charts!

Functions
---------

- Display last calendar  
- Start another chart by picking name and starting date
- Access to older charts

Data
----

Data **serialization**

```javascript
var data = [
	{id: 'miao', string: '2013-10-01 19:21:22'},
	{id: 'cairo', string: '00:00:10'},
	{id: 'istambul', string: '00:01'}
];
store.set('SAcurrent',data);
```

A **chart** is composed by:

- **Chart name** – Unique identifier to recall  
- **Weekly note set** – A set of notes linked to specific weeks  
- **Starting date** – The offset to display the calendar  

A **Weekly note set** is composed by:

- **Set name** – Unique identifier to recall
    - **Note name** – Unique identifier to recall  
    - **Note** – Text string  
    - **Weeks** – Weeks to display note  

Workflow
--------

### New chart

- **Pickup a name** – Check identifier (save chart no set no starting date)  
- **Pickup a note set or create a new one** – Set notes by week (append set to chart)  
- **Pickup a starting date** – Table output will begin (appens starting date to chart)

### View chart

- **Change starting date** – Table output will begin (appens new starting date to chart)  
- **Delete a chart** – Cannot undo

## UIs needed

Plugins
-------

- [glDatePicker](https://github.com/glad/glDatePicker) – To pickup a starting date  
- [store.js](https://github.com/marcuswestin/store.js) – To store charts

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

