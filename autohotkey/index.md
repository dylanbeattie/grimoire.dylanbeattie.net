---
title: AutoHotkey
layout: home
---
# {{ page.title }}

Parsing block statements

```pegjs
program
	= __ head:block EOB tail:program
      { return [ head ].concat(tail) }
    / __ EOF { return [] }
    
__ = [ \t\r\n]*

comment = '(' [^)]+ ')'
block
	= head:statement EOS tail:block
      { return [ head ].concat(tail) }
    / stmt:statement { return [ stmt ] }

EOB = EOS EOS   

EOS = _ EOL _
	/ EOF

EOF = !.
statement 
	= c:conditional 
		{ return c }
    / 'hey' 
    	{ return { 'statement' : 'hey' } }

conditional 
	= 'if' _ e:expression _ s:statement
		{ return { 'if': { 'e': e, 's': s } } }
    / 'if' _ e:expression EOS b:block
		{ return { 'if': { 'e': e, 'b': b } } }    

expression
	= 'true' / 'false'

_ = [ \t]*
EOL = '\r'? '\n'
```

