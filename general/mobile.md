---
description: This page contains some information about the mobile behaviour in Moodle.
---

# Mobile

Moodle brings some helper classes to detect the `current device` of the users. The methods are defined in the `core_useragent` class located under `lib/classes/useragent.php`.

{% hint style="danger" %}
It's important that you have enabled the `enabledevicedetection` setting. Per default it's enabled. 

More info under:

* [https://docs.moodle.org/36/en/Theme\_settings\#Enable\_device\_detection](https://docs.moodle.org/36/en/Theme_settings#Enable_device_detection)
* [https://docs.moodle.org/36/en/Themes\_FAQ\#How\_are\_the\_device\_types\_used\_in\_Moodle.3F](https://docs.moodle.org/36/en/Themes_FAQ#How_are_the_device_types_used_in_Moodle.3F)
{% endhint %}

If you want to check if you're on a mobile device you can use following code snippet:

```php
// Check if on mobile device.
if (core_useragent::get_device_type() == 'mobile') {
    $mobiledevice = true;
}
```



