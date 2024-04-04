# readytogo-global
Store and retrieve global data

## Usage

```javascript
import { instanceofGlobal, getGlobal, executeOnce } from '@readytogo/global';

let textField = getGlobal('textField', 'initial value');

instanceofGlobal(textField); // true

textField = getGlobal('textField', 'secondary value');

executeOnce('printValue', () => {
	console.log(textField.getValue());
	textField.setValue('new value');
	console.log(textField.getValue());
});
```

```
$ node example.js
initial value
new value
```

## Note
getGlobal() will always return the instance associated with the unique key. The initial value will only be set if the value has never been set before. executeOnce() will only execute the callback function one time per unique key. To execute the same callback function again, the unique key must be different. In the usage above, the 'secondary value' will never be set or printed because the initial value has already been set before. The instanceofGlobal() function checks whether something is an instance of Global class.

