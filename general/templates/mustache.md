# Mustache

The templates in php are attached to the renderers. There is a renderer method "render\_from\_template\($templatename, $context\)" that does the trick.

Note $context is nothing to do with normal Moodle 'contexts'. It is the data passed to the template \(the 'context' mentioned in mustache documentation\).

{% tabs %}
{% tab title="Call" %}
```php
public function export_for_template(\renderer_base $output) {
    return [
        'title' => '<h1>foo</h1>'
    ];
}
```

This `{{title}}` is a simple variable substitution. The variable named "title" will be searched for in the current context \(and any parent contexts\) and when a value is found, the entire tag will be replaced by the variable \(HTML escaped\).

This `{{{title}}}` is an unescaped variable substitution. Instead of escaping the variable before replacing it in the template, the variable is included raw. This is useful when the variable contains a block of HTML \(for example\).
{% endtab %}

{% tab title="Result" %}
`{{title}}`  = &lt;h1&gt;foo&lt;/h1&gt;

`{{{title}}}`  = **foo**
{% endtab %}
{% endtabs %}



