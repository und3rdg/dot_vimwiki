
jquery timer, alternative for setTimeout, setInterval

https://github.com/jchavannes/jquery-timer

```
var timer = $.timer(function() {
  alert('This message was sent by a timer.');
});
timer.set({ time : 5000, autostart : true });
```

controll
```
timer.set(options);
timer.play(reset);  // Boolean. Defaults to false.
timer.pause();
timer.stop();  // Pause and resets
timer.toggle(reset);  // Boolean. Defaults to false.
timer.once(time);  // Number. Defaults to 0.
timer.isActive  // Returns true if timer is running
timer.remaining // Remaining time when paused
```  
