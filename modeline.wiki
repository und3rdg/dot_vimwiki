=== fold with 2 empty lines ===
```
// vim: foldmethod=expr foldexpr=getline(v\:lnum)=~'^\\s*$'&&getline(v\:lnum+1)=~'^\\s*$'&&getline(v\:lnum+2)=~'\\S'?'<1'\:1
``` 

=== indent 4 spaces ===
<? // vim: tabstop=4 sw=4 ft=html
<? // vim: noexpandtab tabstop=4 sw=4 ft=html

=== indent 2 spaces ===
<? // vim: tabstop=2 sw=2 ft=html
<? // vim: noexpandtab tabstop=2 sw=2 ft=html

=== indent html, syntax php ===
<? // vim: tabstop=2 sw=2 ft=html syn=php
<? // vim: tabstop=4 sw=4 ft=html syn=php
<? // vim: noexpandtab tabstop=2 sw=2 ft=html syn=php
<? // vim: noexpandtab tabstop=4 sw=4 ft=html syn=php

