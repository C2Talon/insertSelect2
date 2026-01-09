# insertSelect2

Function for KoLmafia scripts to make `<select>` HTML elements searchable on a given page. It does this by reading in a given page, then outputting the page modified to make use of [select2](https://select2.org/) to facilitate that.

A repo with some already-made relay override scripts making use of this for a few pages can be found here: http://github.com/C2Talon/insertSelect2-relays/

## Installation

Can be installed from KoLmafia's CLI via:

```
git checkout https://github.com/C2Talon/insertSelect2.git
```

## Usage

`import`ing this script gives access to this function:

```java
string insertSelect2(string page,string option)
```

* `page` is the HTML of some page to modify
* `option` is optional and is used to change select2-specific options, especially if the defaults are inadequate on a particular page
* `return`s `page` modified to make use of [select2](https://select2.org/) to make `<select>` HTML elements searchable

### Usage examples

Cribbing from [Ezandora's Choice Override](https://github.com/Ezandora/Choice-Override) script for examples here, since choice override scripts are probably where this script would get the most usage. However, this script can be used with any page that can be overridden with a relay script to make any `<select>` elements there searchable.

#### ASH

```java
import "relay/choice.ash"
import <insertSelect2.ash>

void main(string page_text_encoded)
{
	string page_text = page_text_encoded.choiceOverrideDecodePageText();

	page_text = insertSelect2(page_text);

	//modify page_text in other ways here

	write(page_text);
}
```

#### JavaScript

```javascript
const kol = require("kolmafia");

module.exports.main = function (page_text_encoded)
{
	var choice_override_script = require("relay/choice.ash");
	var page_text = choice_override_script.choiceOverrideDecodePageText(page_text_encoded);

	//insertSelect2
	const { insertSelect2 } = require("insertSelect2.ash");
	page_text = insertSelect2(page_text);

	//modify page_text in other ways here

	kol.write(page_text);
}
```

