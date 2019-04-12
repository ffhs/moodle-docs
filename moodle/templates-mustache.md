# Templates \(mustache\)

{% tabs %}
{% tab title="Call" %}
```php
public function export_for_template(\renderer_base $output) {
    return [
        'title' => '<h1>foo</h1>'
    ];
}
```

```text
{{title}}
{{{title}}}
```
{% endtab %}

{% tab title="Result" %}
&lt;h1&gt;foo&lt;/h1&gt;

### foo
{% endtab %}
{% endtabs %}



