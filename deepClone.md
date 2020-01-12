function copyObj(aObject) {
  if (!aObject) { // more strict would be aObject === null
    return aObject;
  }
  var bObject, v, k;
  bObject = Array.isArray(aObject) ? [] : {};
  for (k in aObject) {
    v = aObject[k];
    bObject[k] = (typeof v === "object") ? copy(v) : v;
  }
  return bObject;
}
x={x:'xx', y: {yx: 'zz', yy: null}, z: [1,2,3,null]}
const y = copy(x)
y.z[1] = 'y'

console.log('xxxxx', x)
console.log('yyyyy', y)
