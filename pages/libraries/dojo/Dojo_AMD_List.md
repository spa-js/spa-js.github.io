---
layout: default
title: Dojo AMD List
category: bp
---


Dojo 1.9 AMD loader cheat sheet:
--------------------------------
Taken from: [https:|docs.google.com/spreadsheet/ccc?key=0Au0BMjQuiAdJdExGTkpEaXR0M3Y2bzVBTnBpblhidXc&authkey=CM3l1r4N&hl=fr#gid=0](https:|docs.google.com/spreadsheet/ccc?key=0Au0BMjQuiAdJdExGTkpEaXR0M3Y2bzVBTnBpblhidXc&authkey=CM3l1r4N&hl=fr#gid=0)
`
| =============================================================================================
| function                     | requires                     use instead
| ==============================================================================================
| _defaultEasing               | "dojo/_base/fx"
| _extraNames                  | "dojo/_base/lang"
| _toArray                     | "dojo/_base/lang"
| _Url                         | "dojo/_base/url"
| addClass                     | "dojo/dom-class"            | domClass::add
| addOnLoad                    | "dojo/_base/loader"         | dojo/ready!
| addOnUnload                  | "dojo/_base/unload"
| addOnWindowUnload            | "dojo/_base/unload"
| animateProperty              | "dojo/_base/fx"
| Animation/_Animation         | "dojo/_base/fx"
| anim                         | "dojo/_base/fx"
| attr                         | "dojo/_base/html"           | dojo/dom-prop's set/get
| blendColors                  | "dojo/_base/Color"          | blendColors
| body                         | "dojo/_base/window"
| boxModel (prop)              | "dojo/dom-geometry"
| byId                         | "dijit/registry"
| byId                         | "dojo/dom"
| byNode                       | "dijit/registry"
| cache                        | "dojo/text"
| clone                        | "dojo/_base/lang"
| Color                        | "dojo/_base/Color"
| colorFromArray               | "dojo/_base/Color"         | Color::fromArray
| colorFromHex                | "dojo/_base/Color"          | Color::fromHex
| colorFromRgb                | "dojo/_base/Color"          | Color::fromRgb
| colorFromString             | "dojo/_base/Color"          | Color::fromString
| config                      | "dojo/_base/config"
| connect                     | "dojo/_base/connect"
| contentBox                  | "dojo/_base/html"           | get/setContentBox, dojo/dom-geometry
| coords                      | "dojo/_base/html"           | html::     getBorderBox
| create                      | "dojo/dom-construct"
| Deferred                    | "dojo/_base/Deferred"
| delegate                    | "dojo/_base/lang"
| deprecated                  | "dojo/_base/kernel"
| destroy                     | "dojo/dom-construct"
| disconnect                  | "dojo/_base/connect"
| doc                         | "dojo/_base/window"
| docScroll                   | "dojo/dom-geometry"
| empty                       | "dojo/dom-construct"
| every                       | "dojo/_base/array"
| exists                      | "dojo/_base/lang"
| experimental                | "dojo/_base/kernel"
| extend                      | "dojo/_base/lang"
| fadeIn                      | "dojo/_base/fx"
| fadeOut                     | "dojo/_base/fx"
| fieldToObject               | "dojo/_base/xhr"
| fieldToObject               | "dojo/dom-form"             | fieldToObject
| filter                      | "dojo/_base/array"
| fixEvent                    | "dojo/_base/event"          | event::fix
| fixIeBiDiScrollLeft         | "dojo/dom-geometry"
| forEach                     | "dojo/_base/array"
| formToJson                  | "dojo/dom-form"             | form::toJson
| formToObject                | "dojo/dom-form"             | form::toObject
| formToQuery                 | "dojo/dom-form"             | form::toQuery
| fromJson                    | "dojo/_base/json"
| fx.chain                    | "dojo/fx"                   | fx::chain
| fx.combine                  | "dojo/fx"                   | fx::combine
| fx.slideTo                  | "dojo/fx"                   | fx::slideTo
| fx.wipeIn                   | "dojo/fx"                   | fx::wipeIn
| fx.wipeOut                  | "dojo/fx"                   | fx::wipeOut
| getAttr                     | "dojo/dom-attr"             | domAttr::get
| getBorderExtents            | "dojo/dom-geometry"
| getComputedStyle            | "dojo/dom-style"
| getContentBox               | "dojo/dom-geometry"
| getDocumentElementOffset    | "dojo/dom-geometry"
| get                         | "dojo/dom-prop"
| getMarginBox                | "dojo/dom-geometry"
| getMarginExtents            | "dojo/dom-geometry"
| getMarginSize               | "dojo/dom-geometry"
| getNodeProp                 | "dojo/dom-attr"             | domAttr::getNodeProp
| getObject                   | "dojo/_base/lang"
| getPadBorderExtents         | "dojo/dom-geometry"
| getPadExtents               | "dojo/dom-geometry"
| getStyle                    | "dojo/dom-style"            | domStyle::get
| getUniqueId                 | "dijit/registry"
| global                      | "dojo/_base/window"
| hasAttr                     | "dojo/dom-attr"             | domAttr::has
| hasClass                    | "dojo/dom-class"            | domClass::contains
| hitch                       | "dojo/_base/lang"
| indexOf                     | "dojo/_base/array"
| isAlien                     | "dojo/_base/lang"
| isArray                     | "dojo/_base/lang"
| isArrayLike                 | "dojo/_base/lang"
| isBodyLtr                   | "dojo/dom-geometry"         | domGeom
| isDescendent                | "dojo/dom"                  | dom
| isFunction                  | "dojo/_base/lang"           | lang
| isIE                        | "dojo/_base/sniff"          | sniff                  Note: The return of sniff.js is currently the has() function and isXXX properties are not exported
| isMozilla                   | "dojo/_base/sniff"          | sniff
| isObject                    | "dojo/_base/lang"           | lang
| isOpera                     | "dojo/_base/sniff"          | sniff
| isSafari                    | "dojo/_base/sniff"          | sniff
| isString                    | "dojo/_base/lang"           | lang
| json.stringify              | "dojo/json"                 | json
| keys                        | "dojo/keys"                 | keys
| lastIndexOf                 | "dojo/_base/array"          | arr
| map                         | "dojo/_base/array"          | arr
| marginBox                   | "dojo/_base/html"           | html                   get/setMarginBox    dojo/dom-geometry
| _mixin                      | "dojo/_base/lang"           | lang
| mixin                       | "dojo/_base/lang"           | lang
| moduleUrl                                                 |                        require.toUrl()
| number                      | "dojo/number"               | NumberUtils
| objectToQuery               | "dojo/_base/xhr"            | ioq                    objectToQuery dojo/io-query
| on                          | "dojo/on"                   | on
| partial                     | "dojo/_base/lang"           | lang
| place                       | "dojo/_base/html"           | html
| place                       | "dojo/dom-construct"        | domConstruct
| position                    | "dojo/dom-geometry"         | domGeom
| publish                     | "dojo/_base/connect"        | connect
| query                       | "dojo/query"                | query
| queryToObject               | "dojo/_base/xhr"            | ioq                    queryToObject   dojo/io-query
| rawXhrPost                  | "dojo/_base/xhr"            | xhr
| rawXhrPut                   | "dojo/_base/xhr"            | xhr
| ready                       | "dojo/ready"                | ready
| removeAttr                  | "dojo/dom-attr"             | domAttr                remove
| removeClass                 | "dojo/dom-class"            | domClass               remove
| replaceClass                | "dojo/dom-class"            | domClass               replace
| replace                     | "dojo/_base/lang"           | lang
| requireLocalization         | "dojo/_base/loader"         | requireLocalization
| safeMixin                   | "dojo/_base/declare"        | declare safeMixin
| setAttr                     | "dojo/dom-attr"             | domAttr                set
| setContentSize              | "dojo/dom-geometry"         | domGeom
| setContext                  | "dojo/_base/window"         | win
| set                         | "dojo/dom-prop"             | domProp
| setMarginBox                | "dojo/dom-geometry"         | domGeom
| setObject                   | "dojo/_base/lang"           | lang
| setSelectable               | "dojo/_base/html"           | html    ???
| setSelectable               | "dojo/dom"                  | dom
| setStyle                    | "dojo/dom-style"            | domStyle               set
| some                        | "dojo/_base/array"          | arr
| stopEvent                   | "dojo/_base/event"          | event                  stop
| string                      | "dojo/string"               | string
| style                       | "dojo/_base/html"           | html
| subscribe                   | "dojo/_base/connect"        | connect
| toDom                       | "dojo/dom-construct"        | domConstruct
| toggleClass                 | "dojo/dom-class"            | domClass               toggle
| toJson                      | "dojo/_base/json"           | json
| toPixelValue                | "dojo/dom-style"            | domStyle
| toUrl                                                     |                        require.toUrl()  [Default not dojo/require]
| trim                        | "dojo/_base/lang"           | lang
| unsubscribe                 | "dojo/_base/connect"        | connect
| when                        | "dojo/_base/Deferred"       | Deferred
| withDoc                     | "dojo/_base/window"         | win
| withGlobal                  | "dojo/_base/window"         | win
| xhrDelete                   | "dojo/_base/xhr"            | xhr
| xhr                         | "dojo/_base/xhr"            | xhr                    xhr.get() ...
| -----------------------------------------------------------------------------------------------
| _scopeName           attached as property of dojo dijit dojox objects
| dojo/fx/easing Toggler Need refactor to minimal dependencies   Toggler
|
|
| -----------------------------------------------------------------------------------------------
| MACROS:
| -----------------------------------------------------------------------------------------------
| "dojo/domReady!"                Used to replace dojo.ready(). Callback will be called once dom is fully ready
| "dojo/text!"                    Pull in pure text content and pass it in as an argument to the calback.
| "dojo/i18n!{pkg}/nls/{class}"   Read in nls text. Set local var to "i18n"
|
|
`
