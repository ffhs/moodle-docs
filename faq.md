---
description: Common questions about Moodle and development.
---

# FAQ

## What is the difference between `$this->config` and `$CFG`?

The `$CFG` is the global config object of Moodle which must be included with `global $CFG;` and you can access this object from any **function or class** without having to do anything special. Just reference with`global $CFG;` to access this object. The object of `$this->config` is a config object for a given class e.g. `antivirus\scanner.php`, here is  a part of the code snippet:

{% code-tabs %}
{% code-tabs-item title="antivirus\\scanner.php" %}
```php
/** @var stdClass the config for antivirus */
protected $config;

/**
 * Class constructor.
 *
 * @return void.
 */
public function __construct() {
    // Populate config variable, inheriting class namespace is matching
    // full plugin name, so we can use it directly to retrieve plugin
    // configuration.
    $ref = new \ReflectionClass(get_class($this));
    $this->config = get_config($ref->getNamespaceName());
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## More...

More...



