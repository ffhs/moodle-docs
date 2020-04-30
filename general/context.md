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

## Get context infomation array by context id

{% tabs %}
{% tab title="PHP" %}
```php
list($context, $course, $cm) = get_context_info_array($contextid);
```
{% endtab %}
{% endtabs %}

## Get the course context by course id

```php
$context = context_course::instance($courseid);
echo "Context id: ".$context->id;
```

## Get context of parent

```php
class block_course_checker extends block_base {
    // [..]
    $this->instance->parentcontextid
```

