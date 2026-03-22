## Macros

```xml
<layout>
  <macro name="my_macro"
    margin="4" min_width="100" min_height="100" flex_direction="row" gap="8"
    align_items="center" justify_content="center"/>

  <elements>
    <!-- This div will have all attributes specified in "my_macro" -->
    <div macro="my_macro">
      <label text="hello, world!"/>
    </div>
  </elements>
</layout>

```
