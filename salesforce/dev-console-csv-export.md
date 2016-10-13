# Export result from SF Developer console query editor

Right now, there's no option to achieve this but I found a helpful answer on [SO](http://salesforce.stackexchange.com/a/54844). While the workbench can be potentially used for normal exports, workbench does not work for parent relationship queries and gives error: `Parent relationship queries are disabled in Workbench`.

When on your SF dev console tab, open browser console by pressing F12 and copy/paste the following script:

```javascript
var o = document.evaluate("//div[@id='editors-body']/div[not(contains(@style,'display:none') or contains(@style,'display: none'))]//table/tbody/tr",document,null,0,null);
var r = [];
while(row = o.iterateNext()){
    var cols = row.getElementsByTagName('td');
    var a = [];

    for(var i=0; i<cols.length; i++){
        a.push( formatData( cols[i].textContent ) );
    }

    r.push( a );
}

// generating csv file
var csv = "data:text/csv;charset=utf-8,filename=download.csv,";
var rows = [];

for(var i=0; i<r.length; i++){
    rows.push( r[i].join(",") );
}

csv += rows.join('\r\n');

popup(csv);

function formatData(input) {
    // replace " with “
    var regexp = new RegExp(/["]/g);
    var output = input.replace(regexp, "“");
    //HTML
    var regexp = new RegExp(/\<[^\<]+\>/g);
    var output = output.replace(regexp, "");
    if (output == "") return '';
    return '"' + output + '"';
}

// showing data in window for copy/ paste
function popup(data) {
    var generator = window.open('', 'csv', 'height=400,width=600');
    generator.document.write('<html><head><title>CSV</title>');
    generator.document.write('</head><body style="overflow: hidden;">');
    generator.document.write('<a href="'+encodeURI(csv)+'" download="Sf_export.csv">Download CSV</a><br>');
    generator.document.write('<textArea style="width: 100%; height: 97%;" wrap="off" >');
    generator.document.write(data);
    generator.document.write('</textArea>');
    generator.document.write('</body></html>');
    generator.document.close();
    return true;
}
```
