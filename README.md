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

### Serialization

```javascript
var data = [
	{id: 'miao', string: '2013-10-01 19:21:22'},
	{id: 'cairo', string: '00:00:10'},
	{id: 'istambul', string: '00:01'}
];
store.set('SAcurrent',data);
```

### Chart

- **Chart name** – Unique identifier to recall  
- **Weekly note set** – A set of notes linked to specific weeks  
- **Starting date** – The offset to display the calendar  

```javascript
var charts = [
	{ name: '----', noteset: '----', startingdate: '----' },
	{ name: '----', noteset: '----', startingdate: '----' },
	{ name: '----', noteset: '----', startingdate: '----' }
]
```

### Weekly Note Set

- **Set name** – Unique identifier to recall
    - **Note name** – Unique identifier to recall  
    - **Note** – Text string  
    - **Weeks** – Weeks to display note  

```javascript
var notesets = [
	{ name: '----', week: '--',  }
]
```

Workflow
--------

### New chart

- **Pickup a name** – Check identifier (save chart no set no starting date)  
- **Pickup a note set or create a new one** – Set notes by week (append set to chart)  
- **Pickup a starting date** – Table output will begin (appens starting date to chart)

### View chart

- **Change starting date** – Table output will begin (appens new starting date to chart)  
- **Delete a chart** – Cannot undo

## UIs

- **TABLE**

```html
<form class="gridform">
	<!-- WEEK -->
	<legend>WEEK n</legend>
		<!-- DAY -->
		<div data-row-span="2">
			<div data-field-span="1">
				<label>day month year</label>
				<input type="text" value="note of the week" class="disabled">
			</div>
		</div>
	...
</form>
```

Plugins
-------

- [glDatePicker](https://github.com/glad/glDatePicker) – To pickup a starting date  
- [store.js](https://github.com/marcuswestin/store.js) – To store charts  
- [gridforms](https://github.com/kumailht/gridforms) – To edit notes  

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

