## File inclusion

theme.xml:

```xml
<layout>
  <theme>
    <var key="my_red" value="#FF0000" />
    <var key="my_green" value="#00FF00" />
    <var key="my_blue" value="#0000FF" />
  </theme>
</layout>
```

bar.xml:

```xml
<layout>
  <elements>
    <!-- utilize theme variables included in theme.xml -->
    <rectangle width="16" height="16" color="~my_red"/>
    <rectangle width="16" height="16" color="~my_green"/>
    <rectangle width="16" height="16" color="~my_blue"/>
  </elements>
</layout>
```

main.xml:

```xml
<layout>
  <!-- Include theme -->
  <include src="theme.xml"/>

  <elements>
    <!-- Include as additional elements here -->
    <include src="bar.xml"/>
  </elements>
</layout>
```
