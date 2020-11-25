# Get Timezone with Offset
> **Lien Chen** *2020-11-25*

* Get Array set with offset key and area value, finally output json.
    * Sort by offset time

```php
<?php

$timezoneList = \DateTimeZone::listIdentifiers(\DateTimeZone::ALL);
$list = [];
foreach ($timezoneList as $timezone) {
    date_default_timezone_set($timezone);
    $list[date('P')][] = $timezone;
}
ksort($list, SORT_NUMERIC);
echo json_encode($list);
```