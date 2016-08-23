
# CSV Writer

## API

### new CsvWriter(params)

* params `<Object>`:

    ```js
    {
        path: 'path/to/write-file',
        header: [
            {
                id: 'FIELD_ID',
                title: 'FIELD_TITLE'
            },
            ...
        ]
    }
    ```


### CsvWriter#writeRecords(records)

* params
  * records `<Array<Object|Array>>`:
* returns `<Promise>`

## Usage

### Pass records as objects

```js
var CsvWriter = require('csv-writer');
var writer = new CsvWriter({
    path: 'path/to/file.csv',
    header: [
        {id: 'name', title: 'NAME'},
        {id: 'lang', title: 'LANGUAGE'},
    ]
});

var data = [
    {name: 'Ryuichi', lang: 'Japanese, English'},
    {name: 'Michael', lang: 'English'}
];

writer.writeRecords(data);     // returns a promise

// This will produce a file path/to/file.csv with following contents:
//
//   NAME,LANGUAGE
//   Ryuichi,"Japanese, English"
//   Michael,English
```

### Pass records as arrays

```js
var CsvWriter = require('csv-writer');
var writer = new CsvWriter({
    path: 'path/to/file.csv'
});

var data = [    // Here, `data` is an array of arrays
    ['NAME', 'LANGUAGE'],
    ['Ryuichi', 'Japanese, English'],
    ['Michael', 'English']
];

writer.writeRecords(data);     // returns a promise

// This will produce a file path/to/file.csv with following contents:
//
//   NAME,LANGUAGE
//   Ryuichi,"Japanese, English"
//   Michael,English
```
