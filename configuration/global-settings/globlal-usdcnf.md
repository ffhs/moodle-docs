# Globlal $CNF

#### Get the moodle base url

This is the setting inside config.php that tells Moodle where it is installed.

```php
$CFG->wwwroot
```

#### Get the moodle libdir url

```php
$CFG->libdir
```

#### Get the moodle data root

 The place where Moodle can save uploaded files. 

```php
$CFG->dataroot
```

#### Get the moodle dir root

```php
$CFG->dirroot = __DIR__;
```

```php
require_once($CFG->dirroot .'/blog/lib.php');
```

