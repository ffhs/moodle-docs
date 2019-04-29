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

## What is a moodle component?

A component can be a **moodle plugin**, such as an activity or an **core subsystem**.

* The term component is used in some places such as in the file api.

{% code-tabs %}
{% code-tabs-item title="lib/filelib.php" %}
```php
function file_save_draft_area_files(
    $draftitemid, 
    $contextid, 
    $component, 
    $filearea, 
    $itemid, 
    array $options=null, 
    $text=null, 
    $forcehttps=false) {
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

* The function `get_string` uses the **component** keyword as well

```php
get_string('managefeeds', 'block_rss_client') // identifier:, component:
```

* The class `core_component` provides functions such as:

```php
classloader()
fetch_subsystems()
fetch_plugintypes()
fetch_plugins()
load_classes()
```

> See also the DB table **mdl\_files**

## More...

More...



