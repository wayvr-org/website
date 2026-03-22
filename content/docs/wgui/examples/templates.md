## Templates

```xml
<layout>
  <!-- "title" attrib will be passed to every matching ${title} -->
  <template name="DecoratedTitle">
    <rectangle color="#FFFF00" padding="8" round="4" gap="4">
      <label text="${title}"/>
    </rectangle>
  </template>

  <elements>
    <!-- "title" used here -->
    <DecoratedTitle title="This is a title.">
  </elements>
</layout>

```
