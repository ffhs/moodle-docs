# Context

lib/accesslib.php

* Context: system, courses, activity, blocks...
  * It's like a tree, you can have many contexes at once \(System -&gt; Course -&gt; Activity -&gt; ..\)

### Context types

* context\_coursecat
* context\_course
* context\_module
* context\_block
* context\_helper
* context\_system
* context\_user

## Get context infomation



{% tabs %}
{% tab title="PHP" %}
```php
list($context, $course, $cm) = get_context_info_array($contextid);
```
{% endtab %}
{% endtabs %}

