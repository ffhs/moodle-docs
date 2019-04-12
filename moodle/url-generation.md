# URL generation

### Get an internal moodle URL

```php
return new \moodle_url('/admin/tool/capability/index.php');
```

#### Get an internal moodle URL with GET parameters

```php
return new \moodle_url('/course/view.php', ['id' => $PAGE->course->id]);
```

#### Redirect to URL

```php
redirect($url, 'optional message', 10);
```

#### Base-URL

For Base-URL Media-Urls and so on look here:

{% page-ref page="../moodle-configuration/settings/globlal-usdcnf.md" %}

### Get an url of an module

```php
// $cm is an cm_info object
$url = method_exists($cm->url, 'out') ? $cm->url->out() : '';
```

### Get an url of an pluginfile

```php
$fileurl = \moodle_url::make_pluginfile_url($file->get_contextid(), $file->get_component(), $file->get_filearea(),
        $file->get_itemid(), $file->get_filepath(), $file->get_filename());

$sebfilepath = $fileurl->get_port() ?
        $fileurl->get_scheme() . '://' . $fileurl->get_host() . ':' . $fileurl->get_port() . $fileurl->get_path() :
        $fileurl->get_scheme() . '://' . $fileurl->get_host() . $fileurl->get_path();
```

