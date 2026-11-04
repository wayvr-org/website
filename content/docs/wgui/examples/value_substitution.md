---
title: "Value Substitution"
description: "Use theme variables and value substitution in Wgui for theming and dynamic content."
---

## Value substitution (themes)

```xml
<layout version="2">
  <theme>
    <var key="hello" value="Hello, world!" />
    <var key="text_color" value="#FF0000" />
  </theme>

  <elements>
    <!-- "~hello" will be replaced to "Hello, world!" -->
    <label text="~hello"/>
    <!-- "~text_color" will be replaced to "#FF0000" -->
    <label text="This text will be red" color="~text_color"/>
  </elements>
</layout>
```
