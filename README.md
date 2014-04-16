# cl-notebook
###### A notebook-style in-browser editor for Common Lisp

> Tools, of course, can be the subtlest of traps.
> One day I know I must smash the ~~emerald~~ Emacs.
>
> *with apologies to Neil Gaiman*

# Do not use this yet. Seriously.
######Just walk away for a little while 'till I get it running properly.

### TODO
##### Bugs
- System hangs forever if you send it into an infinite loop (duh). It should time out eventually, and send some notification of the fact.
	- Should it? Are there situations where you'd legitimately want to run an infinite loop in cl-notebook? How would you handle that?
	- Alternative to timing out: run evaluation in a separate thread (they'll be async anyhow) and give the user a keybinding to kill the current computation
	- You'll need to somehow notify all front-ends that there's still a pending computation, and when one has been killed.

##### Features (not necessarily in priority order)
######## Back-end
- Command line args for certain things
	- Forcing output of static files
	- Showing version number
	- Setting listening port
	- Starting the debug system on the server
- Export HTML files
- Export .lisp files
- Build using buildapp?
- Branching for notebooks
- Figure out what to do about packages (thinking about defining a `:cl-notebook-user` that binds everything you need for basics and uses that in the running thread)

######## Front-end
- Really REALLY missing s-expression-based navigation. Look into it.
	- [`subpar`](https://github.com/achengs/subpar) exists, apparently
	- You... may need to roll your own s-exp navigation/deletion stuff here. Useful information:
		- `CodeMirror.runMode(byCellId(10, ".cell-contents").value, "commonlisp", function (token, type) { console.log(token, type)})` effectively tokenizes for you.
		- The CodeMirror matching paren mode might also be a good way to get s-expresison-related stuff happening
- front-end cleanup.
	- Possibly move it into a separate project?
	- Might want to annihilate some syntactic rough edges with a `defpsmacro` or two.

### Dependencies

`alexandria`, `anaphora`, `cl-fad`, `closer-mop`, `optima`, `local-time`, `fact-base`, `house`

### Usage

You need to install the [`house` server](https://github.com/Inaimathi/house), the [`fact-base` triple-store](https://github.com/Inaimathi/fact-base) and [this repo](https://github.com/Inaimathi/cl-notebook) by cloning them.

The rest of the dependencies are [quicklispable](http://www.quicklisp.org/beta/), so you should then be able to hop into a lisp and do `(ql:quickload :cl-notebook)`.

### License

[AGPL3](https://www.gnu.org/licenses/agpl-3.0.html) (also found in the included copying.txt)

*Short version:*

Do whatever you like, BUT afford the same freedoms to anyone you give this software or derivative works (yes, this includes the new stuff you do) to, and anyone you expose it to as a service.

### Credits

This project uses
- [`nativesortable`](https://github.com/bgrins/nativesortable)
- [Code Mirror](http://codemirror.net/)
- [Genericons](http://genericons.com/)
- [`anaphora`](http://www.cliki.net/anaphora)
- [`alexandria`](http://common-lisp.net/project/alexandria/)
- [`parenscript`](http://common-lisp.net/project/parenscript/)
- [`cl-who`](http://weitz.de/cl-who/)
- [`quicklisp`](http://www.quicklisp.org/beta/)
- [`buildapp`](http://www.xach.com/lisp/buildapp/)
