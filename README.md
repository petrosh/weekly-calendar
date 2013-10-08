weekly-calendar
===============

Ideal for nutrition charts!

Functions
---------

- Display current calendar and edit notes.  
- Start another chart by picking name and starting date.  
- Access to older charts.  

Data
----

### Current chart `WCcurrent`

- **Name** – Name of the current chart  
	`current[ name ]`

### Charts `WCcharts`

- **Name** – Unique identifier to recall  
- **Note set** – A set of notes linked to specific weeks  
- **Starting date** – The offset to display the calendar  

```javascript
var charts = [
	{ name: '----', noteset: '----', startingdate: '----' },
	{ name: '----', noteset: '----', startingdate: '----' },
	{ name: '----', noteset: '----', startingdate: '----' }
]
```

### Weekly Note Sets `WCnotesets`

- **Name** – Unique identifier to recall  
- **Week duration** – Used to loop  
- **Week notes** – For every week:  
	- **Week number**  
	- **Note**  

```javascript
var notesets = [
	{ name: '----', duration: '--', weeknotes: { 1: '----', 5: '----', ... 12: '----' } }
	{ name: '----', duration: '--', weeknotes: { 2: '----', 4: '----', ... 7: '----' } }
]
```

### Runtime notes `WCnotes`

- **Note set name** – Runtime notes are linked to a noteset  
- **Notes** – For every note  
	- **Day**  
	- **Note**  

```javascript
var notes = [
	{ noteset: '----', notes: { day: 'yyyy-mm-dd', note: '----', day: 'yyyy-mm-dd', note: '----' } }
]
```

Workflow
--------

### New chart

- **Pickup name, noteset and starting date**  
	`chart[ name ], chart[ noteset_name ], chart[ starting_date ]`

### New note set

- **Pickup name and duration**  
	`noteset[ name ], noteset[ duration ]`

Generating week list and editable fields

- **Edit fields and save**  
	`weeknotes[ week_number ] = string`

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
			<div data-field-span="1">
				<label>NOTE</label>
				<input type="text">
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

