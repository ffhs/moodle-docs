# Block

```php
<?php
class block_simplehtml extends block_base {

    public function init() {
        $this->title = 'plugin title';
        $this->content_type = BLOCK_TYPE_TEXT;
    }
    
    public function get_content() {
        if ($this->content !== null) {
          return $this->content;
        }
     
        $this->content         =  new stdClass;
        $this->content->text   = 'The content of our SimpleHTML block!';
        $this->content->footer = 'Footer here...';
     
        return $this->content;
    }
}
```

### Block configuration via overriding methods

```php
public function hide_header() {
  return true;
}

// Enable global configuration
public function has_config() {
  return true;
}

// Locations where block can be displayed.
public function applicable_formats() {
  return array('my' => true);
}

```

{% hint style="warning" %}
Don't use `global PAGE` in a block use`$this-page`
{% endhint %}



