// TEST OBJECT WITH SELECTORS (jquery/querySelector)
var Test = {
  elements: function(){
    "use strict"
    if(!dbg){ return }
    Object.keys(this).forEach((item) => { 
      if(item === 'test'){ return }
      if(!this[item] || this[item].length === 0){
        console.warn("missing: " + "elements." + item)
      }
    })
  }
}

var elements = {
  container : document.querySelector('.filter_dropdown_container'),
  types     : document.querySelectorAll('[data-filter_type]'),
  getUrl    : document.querySelector('[data-filter_url]'),
  submit    : document.querySelector('[data-filter_submit]'),
  parm      : document.querySelector('[data-filter_parm]'),
  subList   : document.querySelectorAll('.filter_sub_list'),
  list      : document.querySelectorAll('.filter_list'),
  test      : Test.elements
}

elements.test()

