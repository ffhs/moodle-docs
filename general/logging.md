# Logging

## Logging user activity

{% embed url="https://docs.moodle.org/dev/Logging\_2" %}

## Logging in moodle programmatically for debugging and monitoring

Since I didn't found any real looging mechanism in moodle, I usualy just use:

```php
file_put_contents('/data/moodledata/steps.log', 'step10', FILE_APPEND);
```

```php
file_put_contents('/data/moodledata/debug.json', json_encode($courses));
```

{% hint style="info" %}
Just for debugging this should be enough. I'am aware that you can debug in phpStorm directly, but sometimes its difficult to work with \(AJAX calls, API, Non regularly occuring problems\).
{% endhint %}

{% hint style="warning" %}
Be sure to log into a folder the webserver-user has write access, since the `/moodle` folder should be read only. Put it into `/data/moodledata/` 
{% endhint %}

