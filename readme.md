Root Element
============
The root element is always named **ui**.
It allows usage of following attributes:
    
* `ns:<WILDCARD>`
    WILDCARD is any identifier which matches the regex `[a-zA-Z][a-zA-Z0-9]*`.
    The attribute will pre-define the value provided to it as package name which can be used
    with other features of MIL.
* `ext:<WILDCARD>`
    WILDCARD is any identifier which matches the regex `[a-zA-Z][a-zA-Z0-9]*`.
    Defindes a package where the framework will find other special attributes.
    Framework will look out for any class that implements the IExtensiveAttribute interface

Extensive Attributes
====================
Extensive attributes are values which are passed to a specific attribute parser which
will then provide the value instead of the interpreded variant.
They are "initialized" using curly brackets
Arguments provided to it are separated via comma.
syntax:
`'{' <xatt> [ <value> { ',' <value> } ] '}'`

Eventing
========
An event in terms of MIL, is a special callback function for a UI-Element.
The callback function has to be static and needs to be refered by using the special
attribute `static` (available in the namespace `io.x39.mc.framework.mil.xatt`)
or simmilar extensive attributes.