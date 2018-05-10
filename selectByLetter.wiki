
```javascript
    storage:{
      letter: '',
      index: 0,
      letterArr: []
    },

    getMenuItems: function(that){
      "use strict"
      this.clearLetterState()

      // menu items from DOM
      var $items =  $(that).parent().find('.nano li:nth-of-type(n+2)')
      var itemsArr = Array.from($items)

      var itemsObj = itemsArr.reduce(function(obj, item){
        var firstLetter = item.innerText.toLowerCase().slice(0,1)
        if(obj[firstLetter] === undefined){
          obj[firstLetter] = []
        }
        obj[firstLetter].push(item.id)
        return obj
      }, {})
      // console.table(itemsObj)
      return itemsObj
    },

    onKeyUpHover: function(obj){
      "use strict"
      var that = this
      $(window).off("keyup")
      $(window).bind("keyup",function(e){
        var keyPress = String.fromCharCode(e.keyCode).toLowerCase();
        that.storage.letterArr = obj[keyPress]
        var idxArr = that.storage.letterArr

        if(idxArr){
          var idxId = that.letterState(keyPress)
          that.focusByElement(idxArr, idxId)
        }
      })
    },

    letterState: function(letter){
      "use strict"
      // resset index if different letter was pressed
      if(letter !== this.storage.letter){
        this.storage.index = 0
      }
      this.storage.letter = letter

      // array/index incressing or resseting
      var arrLength = this.storage.letterArr.length -1
      var lastIndex = this.storage.index
      if(this.storage.index < arrLength){
        this.storage.index ++
      } else {
        this.storage.index = 0
      }
      return lastIndex
    },

    focusByElement: function(letterIdsArr, index){
      "use strict"
      var element = letterIdsArr[index]
      if(element){
        document.getElementById(element).focus()
      }
    },

    clearLetterState: function(){
      "use strict"
      this.storage.letter = ''
      this.storage.index = 0
    },

    initFocusByLetter: function(event){
      "use strict"
      var getLettersIndex = this.getMenuItems(event)
      this.onKeyUpHover(getLettersIndex)
    },
    
    init: function(){
    
      $element.on("click", function(){
        that.initFocusByLetter(this)
      })
    }
  
```
