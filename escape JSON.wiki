## PHP 5.3 (wkcd)
```
data-costam='<?=json_encode(esc($var), JSON_HEX_APOS)?>'
```

## MODERN PHP
```
<?php
$a = array('<foo>',"'bar'",'"baz"','&blong&', "\xc3\xa9");

echo "Normal: ",  json_encode($a), "\n";
// Normal: ["<foo>","'bar'","\"baz\"","&blong&","\u00e9"]

echo "Tags: ",    json_encode($a, JSON_HEX_TAG), "\n";
// Tags: ["\u003Cfoo\u003E","'bar'","\"baz\"","&blong&","\u00e9"]

echo "Apos: ",    json_encode($a, JSON_HEX_APOS), "\n";
// Apos: ["<foo>","\u0027bar\u0027","\"baz\"","&blong&","\u00e9"]

echo "Quot: ",    json_encode($a, JSON_HEX_QUOT), "\n";
// Quot: ["<foo>","'bar'","\u0022baz\u0022","&blong&","\u00e9"]

echo "Amp: ",     json_encode($a, JSON_HEX_AMP), "\n";
// Amp: ["<foo>","'bar'","\"baz\"","\u0026blong\u0026","\u00e9"]

echo "Unicode: ", json_encode($a, JSON_UNESCAPED_UNICODE), "\n";
// Unicode: ["<foo>","'bar'","\"baz\"","&blong&","é"]

echo "All: ",     json_encode($a, JSON_HEX_TAG | JSON_HEX_APOS | JSON_HEX_QUOT | JSON_HEX_AMP | JSON_UNESCAPED_UNICODE), "\n\n";
// All: ["\u003Cfoo\u003E","\u0027bar\u0027","\u0022baz\u0022","\u0026blong\u0026","é"]




$b = array();

echo "Empty array output as array: ", json_encode($b), "\n";
// Empty array output as array: []

echo "Empty array output as object: ", json_encode($b, JSON_FORCE_OBJECT), "\n\n";
// Empty array output as object: {}


$c = array(array(1,2,3));

echo "Non-associative array output as array: ", json_encode($c), "\n";
// Non-associative array output as array: [[1,2,3]]
echo "Non-associative array output as object: ", json_encode($c, JSON_FORCE_OBJECT), "\n\n";
// Non-associative array output as object: {"0":{"0":1,"1":2,"2":3}}

$d = array('foo' => 'bar', 'baz' => 'long');


echo "Associative array always output as object: ", json_encode($d), "\n";
// Associative array always output as object: {"foo":"bar","baz":"long"}

echo "Associative array always output as object: ", json_encode($d, JSON_FORCE_OBJECT), "\n\n";
// Associative array always output as object: {"foo":"bar","baz":"long"}
?>





vim: syn=php
