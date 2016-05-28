[![view on npm](http://img.shields.io/npm/v/command-line-usage.svg)](https://www.npmjs.org/package/command-line-usage)
[![npm module downloads](http://img.shields.io/npm/dt/command-line-usage.svg)](https://www.npmjs.org/package/command-line-usage)
[![Build Status](https://travis-ci.org/75lb/command-line-usage.svg?branch=master)](https://travis-ci.org/75lb/command-line-usage)
[![Dependency Status](https://david-dm.org/75lb/command-line-usage.svg)](https://david-dm.org/75lb/command-line-usage)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](https://github.com/feross/standard)

# command-line-usage
A simple module for creating a usage guide.

## Synopis
The `commandLineUsage()` function takes one or more `section` objects as input. Each section comprises an optional `header` property and one of either `content`, `banner` or `optionList`.

The `header` is always bold and underlined. A `content` string is indented and wrapped to 80 columns.

```js
const getUsage = require('command-line-usage');

const descriptionSection = {
  header: 'A typical app',
  content: 'Generates something [italic]{very} important. This is a rather long, but ultimately inconsequential description intended solely to demonstrate description appearance. '
}
const usage = getUsage(descriptionSection)

console.log(usage)
```

Inline ansi formatting can be used anywhere within the usage template using the formatting syntax described [here](https://github.com/75lb/ansi-escape-sequences#module_ansi-escape-sequences.format).

## Examples

### Typical
A typical, three sections guide. [Code](https://github.com/75lb/command-line-usage/blob/master/example/simple.js).

![usage](https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/simple.png)

### Option List groups
Demonstrates breaking the option list up into groups. This example also sets a `typeLabel` on each option definition (e.g. a `typeLabel` value of `files` is more meaningful than the default `string[]`). [Code](https://github.com/75lb/command-line-usage/blob/master/example/groups.js).

![usage](https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/groups.png)

### Banners

#### Header
Demonstrates a banner at the top. This example also adds a `synopsis` section. [Code](https://github.com/75lb/command-line-usage/blob/master/example/header.js).

![usage](https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/header.png)

#### Footer
The footer is displayed at the end of the template. [Code](https://github.com/75lb/command-line-usage/blob/master/example/footer.js).

![usage](https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/footer.png)

### Examples section (table layout)
An examples section is added. In this case the example list is defined as an array of objects (each with consistently named properties) so will be formatted by [table-layout](https://github.com/75lb/table-layout).   [Code](https://github.com/75lb/command-line-usage/blob/master/example/examples.js).

![usage](https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/example-columns.png)

### Description section (table layout)
Demonstrates usage of custom table layout in the description. In this case the second column (containing the hammer and sickle) has `nowrap` enabled, as the input is already formatted as desired. [Code](https://github.com/75lb/command-line-usage/blob/master/example/description-columns.js).

![usage](https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/description-columns.png)

## Modules

<dl>
<dt><a href="#module_command-line-usage">command-line-usage</a></dt>
<dd></dd>
</dl>

## Classes

<dl>
<dt><a href="#OptionList">OptionList</a></dt>
<dd></dd>
</dl>

<a name="module_command-line-usage"></a>

## command-line-usage

* [command-line-usage](#module_command-line-usage)
    * [getUsage(sections)](#exp_module_command-line-usage--getUsage) ⇒ <code>string</code> ⏏
        * [~ContentSection](#module_command-line-usage--getUsage..ContentSection)

<a name="exp_module_command-line-usage--getUsage"></a>

### getUsage(sections) ⇒ <code>string</code> ⏏
**Kind**: Exported function  
<table>
  <thead>
    <tr>
      <th>Param</th><th>Type</th><th>Description</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td>sections</td><td><code>Section</code> | <code>Array.&lt;Section&gt;</code></td><td><p>one of more section objects.</p>
</td>
    </tr>  </tbody>
</table>

<a name="module_command-line-usage--getUsage..ContentSection"></a>

#### getUsage~ContentSection
A Content section comprises a header and one or more lines of text.

**Kind**: inner typedef of <code>[getUsage](#exp_module_command-line-usage--getUsage)</code>  
**Properties**

<table>
  <thead>
    <tr>
      <th>Name</th><th>Type</th><th>Description</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td>header</td><td><code>string</code></td><td>The section header.</td>
    </tr><tr>
    <td>content</td><td><code>string</code> | <code>Array.&lt;string&gt;</code> | <code>Array.&lt;object&gt;</code></td><td>One or more lines of text. Pass a recordset array for tabulated content.</td>
    </tr>  </tbody>
</table>

**Example**  
```js
{
  header: 'A typical app',
  content: 'Generates something [italic]{very} important. This is a rather long, but ultimately inconsequential description intended solely to demonstrate description appearance. '
}
```
<a name="OptionList"></a>

## OptionList
**Kind**: global class  
<a name="new_OptionList_new"></a>

### new OptionList(data)
<table>
  <thead>
    <tr>
      <th>Param</th><th>Type</th><th>Description</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td>data</td><td><code>Section</code> | <code>Array.&lt;Section&gt;</code></td><td><p>an array of <a href="https://github.com/75lb/command-line-args#exp_module_definition--OptionDefinition">option definition</a> objects. In addition to the regular definition properties, command-line-usage will look for:</p>
<ul>
<li><code>description</code> - a string describing the option.</li>
<li><code>typeLabel</code> - a string to replace the default type string (e.g. <code>&lt;string&gt;</code>). It&#39;s often more useful to set a more descriptive type label, like <code>&lt;ms&gt;</code>, <code>&lt;files&gt;</code>, <code>&lt;command&gt;</code> etc.</li>
</ul>
</td>
    </tr>  </tbody>
</table>


* * *

&copy; 2015-16 Lloyd Brookes \<75pound@gmail.com\>. Documented by [jsdoc-to-markdown](https://github.com/75lb/jsdoc-to-markdown).
