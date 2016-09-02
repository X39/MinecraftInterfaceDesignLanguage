The Base of a UI
================
To create a MIDL ui, you have to extend the abstract class `MidlGui` which can be found in the
`io.x39.mc.framework.midl` package.
The base constructor expects you to provide a valid file stream to the MIDL file used.

Root Element
============
The root element is always named **ui**.
It allows usage of following attributes:
    
* `ns:<WILDCARD>`
  WILDCARD is any identifier which matches the regex `[a-zA-Z][a-zA-Z0-9]*`.
  The attribute will pre-define the value provided to it as package name which can be used
  with other features of MinecraftInterfaceDesignLanguage.
* `ext:<WILDCARD>`
  WILDCARD is any identifier which matches the regex `[a-zA-Z][a-zA-Z0-9]*`.
  Defindes a package where the framework will find other special attributes.
  Framework will look out for any class that annotates `ExtensiveAttribute`

Extensive Attributes (xAttribute)
=================================
xAttribute are values which are passed to a specific attribute parser which
will then provide the value instead of the interpreded variant.
They are "initialized" using curly brackets
Arguments provided to it are separated via comma (in case no naming is present, the framework will
pass the args as they where defined in the extension class).
syntax:
`'{' <xatt> [ ( <argname>=<value> { ',' <argname>=<value> } ) | ( <value> { ',' <value> } ) ] '}'`

If you want to create your own annotation, you have to annotate a class with the `XAttribute`
annotation.
All theese annotations can be found in the `io.x39.mc.framework.midl.xatt` package.
Further annotations:
* `Attribute`
  The Attribute annotation is used to generate arguments in the xAttribute 
  It expects two arguments:
  * `Class type` The type this attribute expects.
  * `String name` The name of this specific attribute.
* `Convert`
  Specifies converter functions for the different target types.
  The method is expected to get a `MidlGui` as parameter and to any value but void.

Eventing
========
An event in terms of MinecraftInterfaceDesignLanguage, is a special callback function for a UI-Element.
The callback function has to be static and needs to be refered by using the special
attribute `static` or `fnc` (both available in the package `io.x39.mc.framework.midl.xatt.def`)
or simmilar extensive attributes.