
Fast and very compatible with all browsers.
Very straight forward
https://jsperf.com/nodelist-to-array/27

Working with everything what have a .length:

function nodeListToArray(nodeList){
  var i = nodeList.length
  var arr = new Array(i)
  while(i--){ arr[i] = nodeList[i] }
  return arr
}

On top of that fancy addition,
but working only with NodeList's:

NodeList.prototype.toArray = function(){
  return nodeListToArray(this)
}
    

