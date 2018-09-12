function debug(){
  "use strict"
  var isDebug = parseInt(window.localStorage.getItem('debug'))
  if(isDebug){ console.log.apply(null, arguments) }
    // turn it on in your browser by
    // window.localStorage.setItem('debug',1)
}


version 2

var dbg = parseInt(window.localStorage.getItem('debug'))
if(dbg){ dbg = console.log
} else { dbg = function(){} } 
  // turn it on in your browser by
  // window.localStorage.setItem('debug',1)
  
  
version 3

// DEBUGING
// dbg.on/off in devtools to turn it on/off
var isDebug = parseInt(window.localStorage.getItem('debug'))
var dbg 

if(isDebug){
  dbg          = console.log
  dbg.group    = console.group
  dbg.groupEnd = console.groupEnd
  dbg.table    = console.table
}
if(!isDebug){
  dbg          = function(){} 
  dbg.group    = function(){} 
  dbg.groupEnd = function(){} 
  dbg.table    = function(){} 
}

dbg.on = function(){
  "use strict"
  console.log('%c debuging mode ON',
    'background: green; color: white')
  window.localStorage.setItem('debug',1)
  isDebug = 1
}
dbg.off = function(){
  "use strict"
  console.log('%c debuging mode OFF',
    'background: red; color: white')
  window.localStorage.setItem('debug',0)
  isDebug = 0
}
dbg.toggle = function(){
  "use strict"
  switch(isDebug){
    case 1:
      dbg.off()
      break
    default:
      dbg.on()
      break
  }
}
