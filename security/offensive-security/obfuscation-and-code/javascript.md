# JavaScript

`Code minification` (opposite: beautify) means having entire code in a single line (.min.js). It is not exclusive to JS ( [Minification tool](https://www.toptal.com/developers/javascript-minifier)) ( [Beautify tool](https://beautifier.io/)).

#### [Direct link to heading](javascript.md#basic-obfuscation) Basic Obfuscation

[**Direct link to heading**](javascript.md#packing-technique) **Packing Technique**

A packer swaps words and symbols from your code into a list (or dictionary) and replaces them with short placeholders. A small `(p,a,c,k,e,d)`-style function then looks up those placeholders and rebuilds the real code when it runs.

This makes the code hard to read, but important strings (like `"password"` or API URLs) could often stay readable so you might need stronger obfuscation.

\# Before packing (No minification)

Copy

```
function greet(name){
    alert("Hello, " + name + "!");
}
greet("Alice");
```

\# After packing (No minification)

Copy

```
eval(function(p,a,c,k,e,d){
    e=function(c){return c.toString(36)};
    if(!''.replace(/^/,String)){
        while(c--) d[c.toString(a)]=k[c]||c.toString(a);
        k=[function(e){return d[e]}];
        e=function(){return'\w+'};
        c=1;
    }
    while(c--)
        if(k[c]) p=p.replace(new RegExp('\b'+e(c)+'\b','g'),k[c]);
    return p;
}('2 0(1){3("4, "+1+"!")}0("5")',6,6,'greet|name|function|alert|Hello|Alice'.split('|'),0,{}))
```

We’ve made the code harder to read, but still some of it is visible. We’ll try tools that fully obfuscate the code and remove those cleartext remnants.

#### [Direct link to heading](javascript.md#advanced-obfuscation) Advanced Obfuscation

Advanced obfuscation can slow execution, so repeated obfuscation or extreme encoders may cause noticeable delays. Tools like [obfuscator.io](https://obfuscator.io/), JJEncode or AAEncode exist but often make code very slow and should be used only for specific needs (e.g., bypassing filters).

\# Before obfuscation (No minification)

Copy

```
function greet(name){
    console.log("Hello, " + name + "!");
}
greet("Alice");
```

\# After obfuscation (With minification) // This code with still run as above

Copy

```
(function(_,$,Z){/* meaningless dead/no-op noise /var x=1337,y=x^42,z=!!(y-1294);(function hide(){var A=[102,117,110,99,116,105,111,110,32,103,114,101,101,116,40,110,41,123,10,32,32,99,111,110,115,111,108,101,46,108,111,103,40,34,72,101,108,108,111,44,32,34,32,43,32,110,32,43,32,34,33,34,41,59,10,125,10,103,114,101,101,116,40,34,65,108,105,99,101,34,41,59];/ confusing renames + pointless math to obscure intent /var B=A.map(function(n,i){return(((n^(i&0x7))-(i%3)+0x00)&0xFF);});/ undo the pointless math to reconstruct real char codes /for(var i=0;i<B.length;i++){B[i]=(((B[i]+(i%3))^(i&0x7))&0xFF);}/ rebuild source and execute with an indirect eval to avoid some simple static scans */var src=String.fromCharCode.apply(null,B);(0,eval)(src);})();})({},[],null);
```

#### [Direct link to heading](javascript.md#deobfuscation) Deobfuscation

We can deobfuscate code with tools like [unPacker](https://matthewfl.com/unPacker.html). Another way to deobfuscate [packed code](javascript.md#packing-technique) above is to find the return value at the end of the packed code and use console.log to print it instead of executing it.

[PreviousObfuscation & Code](./) [NextPivoting & Forwarding](../pivoting-and-forwarding/)

Last updated 10 days ago
