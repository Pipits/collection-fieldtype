# Collection Field Type

A field type for selecting Collection keys - Perch Runway only.



## Installation

- Download the field type
- Unzip the download
- Place the `collection` folder in `perch/addons/fieldtypes`.



## Requirements

- Perch Runway 3.0 or higher



## Usage

```html
<perch:content id="collections" type="collection" label="Collections">
```

Limit number collection that can be selected with the `max` attribute:

```html
<perch:content id="collections" type="collection" label="Collections" max="1">
```

If multiple collections are selected, the keys are rendered in the template as a comma-separated string:

```
Key 1,Key 2,Key 3
```


## Examples:

An example of how you might use it is to allow an editor to select a single collection to be displayed on a page:

```html
<perch:content id="collections" type="collection" label="Collections" max="1">
```

```php
$collection_key = perch_content('Collection', true);

if($collection_key) {
    perch_collection($collection_key, [
        'template' => 'list.html'
    ]);
}
```


An example of how you can allow the editor to select multiple collections to be displayed on a page:

```html
<perch:content id="collections" type="collection" label="Collections">
```

```php
$collection_keys = perch_content('Collections', true);
$collection_keys = explode(',', $collection_keys);

foreach($collection_keys as $collection_key) {
    perch_collection($collection_key, [
        'template' => 'list.html'
    ]);
}
```