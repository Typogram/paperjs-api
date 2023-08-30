# PaperScript

## Static Methods

*   `PaperScript.compile(code[, options])`

    Compiles PaperScript code into JavaScript code.

    * Options:
    * `options.url: String` — the url of the source, for source-map generation
    * `options.source: String` — the source to be used for the source- mapping, in case the code that’s passed in has already been mingled.
    * Parameters:
    * `code:` `String` — the PaperScript code
    * `options:` `Object` — the compilation options — optional
    * Returns:
    * `Object` — an object holding the compiled PaperScript translated into JavaScript code along with source-maps and other information.
*   `PaperScript.execute(code, scope[, options])`

    Compiles the PaperScript code into a compiled function and executes it. The compiled function receives all properties of the passed `PaperScope` as arguments, to emulate a global scope with unaffected performance. It also installs global view and tool handlers automatically on the respective objects.

    * Options:
    * `options.url: String` — the url of the source, for source-map generation
    * `options.source: String` — the source to be used for the source- mapping, in case the code that’s passed in has already been mingled.
    * Parameters:
    * `code:` `String` — the PaperScript code
    * `scope:` `PaperScope` — the scope for which the code is executed
    * `options:` `Object` — the compilation options — optional
    * Returns:
    * `Object` — the exports defined in the executed code
*   `PaperScript.load([script])`

    Loads, compiles and executes PaperScript code in the HTML document. Note that this method is executed automatically for all scripts in the document through a window load event. You can optionally call it earlier (e.g. from a DOM ready event), or you can mark scripts to be ignored by setting the attribute `ignore="true"` or `data-paper-ignore="true"`, and call the `PaperScript.load(script)` method for each script separately when needed.

    * Parameters:
    * `script:` `HTMLScriptElement` — the script to load. If none is provided, all scripts of the HTML document are iterated over and loaded — optional, default: `null`
    * Returns:
    * `PaperScope` — the scope produced for the passed `script`, or `undefined` of multiple scripts area loaded
