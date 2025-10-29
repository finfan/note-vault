#modules #javascript #code #codesnippets
Create a file (for example a mathUtils JavaScript file) mathUtils.js
Then in your html files script tag add the following
```html
<script type="module" src="index.js"></script>
```

index.js
```javascript
import {getCircumference} from "./mathUtil.js"
```

mathUtil.js
```javascript
const PI = 3.14159

export function getCircumference(radius){
	return 2 * PI * radius
}
```

#tablerow
Insert rows in an exciting table

```javascript
// Find a <table> element with id="myTable":  
let table = document.getElementById("myTable");  
  
// Create an empty <tr> element and add it to the 1st position of the table:  
let row = table.insertRow(0);  
  
// Insert new cells (<td> elements) at the 1st and 2nd position of the "new" <tr> element:  
let cell1 = row.insertCell(0);  
let cell2 = row.insertCell(1);  
  
// Add some text to the new cells:  
cell1.innerHTML = "NEW CELL1";  
cell2.innerHTML = "NEW CELL2";
```

#createtable

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Part List (JS)</title>
</head>
<body>

<!-- Where the table will go -->
<div id="table‑container"></div>

<script>
  // 1. The header titles we want
  const headers = ['Part Number', 'Description', 'Rev', 'Qty'];

  // 2. (Optional) Some sample data rows
  const data = [
    ['PN001', 'Resistor 10kΩ', 'R1', 20],
    ['PN002', 'Capacitor 100µF', 'R1', 15],
    ['PN003', 'Microcontroller', 'R2', 5]
  ];

  /**
   * Build a table with the given headers and optional rows.
   *
   * @param {string[]} headerNames  - Array of header titles
   * @param {Array[]}  rows         - Optional 2‑D array of cell data
   * @returns {HTMLTableElement}    - The constructed <table> element
   */
  function createTable(headerNames, rows = []) {
    const table = document.createElement('table');

    /* -------- Header -------- */
    const thead = document.createElement('thead');
    const headerRow = document.createElement('tr');

    headerNames.forEach(name => {
      const th = document.createElement('th');
      th.textContent = name;          // <-- sets the header text
      headerRow.appendChild(th);
    });

    thead.appendChild(headerRow);
    table.appendChild(thead);

    /* -------- Body -------- */
    const tbody = document.createElement('tbody');

    rows.forEach(rowData => {
      const tr = document.createElement('tr');

      rowData.forEach(cellData => {
        const td = document.createElement('td');
        td.textContent = cellData;     // <-- sets the cell value
        tr.appendChild(td);
      });

      tbody.appendChild(tr);
    });

    table.appendChild(tbody);
    return table;
  }

  /* -------- Render the table -------- */
  const tableContainer = document.getElementById('table‑container');
  const table = createTable(headers, data);
  tableContainer.appendChild(table);
</script>

</body>
</html>

```

#sumtablecolumn 

```javascript
//create a variable to sum
let shipmentValue = 0.0

//add each row value to the shipmentValue
shipmentValue += line.Unit_Price * line.Quantity
```

#files #filesystemapi
Working with files in JavaScript
```javascript
async function getFile() {
  // Open file picker and destructure the result the first handle
  const [fileHandle] = await window.showOpenFilePicker();
  const file = await fileHandle.getFile();
  return file;
}
```

#save #filesystemapi
Save a file in JavaScript
```javascript
async function save() {
	let stream = await fileHandle.createWritable()
	await stream.write(text.innerText)
	await stream.close()
}
```

#saveas #filesystemapi
Save as file in JavaScript
```javascript
async function saveAs() {
	fileHandle = await window.showSaveFilePicker()
}
```
