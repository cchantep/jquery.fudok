# jQuery plugin for Fudok

This jQuery plugin allows to merge form submission with PDF template managed on [Fudok service](https://go.fudok.com).

PDF merge can be called directly on your pages with JS, using AJAX/XHR features. Doing so you can check data as you want before merging them with PDF.

```javascript
$.fudok({
  'action': "merge",
  'fudok_token': "a610e9b1048499110433bb790489303a07182aac", // replace by yours
  'fudok_template': "ca62e08d-2082-4cd4-837c-d46a362091e3", // replace by yours
  'data':"#formId",
  // or as dictionary -> 'data':{'firstName':"First"}
  // 'form_target': "_blank",
});
```

You want to see this plugin in action: [demo](http://rawgit.com/cchantep/jquery.fudok/master/demo.html).

## Get started

You can download plugin files from the source repository: [js/](https://github.com/cchantep/jquery.fudok/tree/master/js) and [i18n/](https://github.com/cchantep/jquery.fudok/tree/master/js) sub-directories.

This plugin is also available as a [NPM package](https://www.npmjs.com/package/jquery.fudok): `npm install jquery.fudok`

> You can also use a bundle hosted by Fudok, gathering a jQuery version and this plugin: [//go.fudok.com/en/js/merge-bundle.gz.js](http://go.fudok.com/en/js/merge-bundle.gz.js).

## Setup

Plugin `jQuery.fudok` can be given following options.

- (Mandatory) `action` with `"merge"` value: Indicate jQuery Fudok plugin which action should be processed.
- (Mandatory) `fudok_token`: Application token of your account (see "My account" screen).
- `fudok_template`: ID of template you want to merge form values with. It's displayed in a badge aside template information in "My account" screen.
- `data`: Field data to be merge with PDF/Dhek template. It can be either a [jQuery selector](http://api.jquery.com/category/selectors/) referencing a form element (e.g. `"#formId"`), or a plain JS dictionary (array with string a keys, e.g. `{'firstName':"First"}`). 
  - If a form element is specified (jQuery selector), fields (text/radio/checkbox/email/password/... input, select and textarea) are considered, name of each having to match an area key defined in template, or its value is silently ignored/considered undefined.
  - If dictionary is given, each key should match an area key defined in template, or it's ignored (considered undefined).

If you want to have not editable value merged using such jQuery plugin, you can either add hidden or readonly field, when specifying data as form selector, or adding an hardcoded/static entry if using dictionary.

```html
<!-- As a hidden field -->
<input type="hidden" name="area_key" value="uneditable_value" />

<!-- ... or as a readonly field -->
<input type="text" readonly="readonly"
  name="area_key" value="uneditable_value" />

```
