# game-keyboard

Check current state of keyboard keys in the browser. Suitable for games.

# Example

```javascript
var Keyboard = require("game-keyboard");
var keyMap = require("game-keyboard/key_map")["US"];
var keyboard = new Keyboard(keyMap);

// with no keys pressed
keyboard.isPressed("up"); // returns false
keyboard.consumePressed("up"); // returns false

// start pressing up arrow
keyboard.isPressed("up"); // returns true
keyboard.consumePressed("up"); // returns true

// continuing to press up arrow
keyboard.isPressed("up"); // returns true
keyboard.consumePressed("up"); // returns false
```

# Constructor

The constructor takes a keymap, which is an object that maps keyboard codes (e.keyCode) to human-readable names.
The human-readable names in the keymap are what you use as the argument to `isPressed` and `consumePressed`.
This library comes with a "US" keymap in `key_map.js`. I'll happily accept contributions for keymaps of other locales.

# `isPressed(key)`

Test if a key is currently pressed.

Accepts a key name that is specified in the keymap that was given to the constructor.

# `consumePressed(key)`

Test if a key is currently pressed, and makes the key look not pressed to subsequent calls of `consumePressed`.
To make the key look pressed again, the key must be released and re-pressed. This does not affect how `isPressed` sees the key.

This is useful for when you want to do some action only the first time a key is pressed, but not every frame that it is held down. For example: entering text.

Accepts a key name that is specified in the keymap that was given to the constructor.

# Install

With [npm](https://www.npmjs.com/) do:

```
npm install game-keyboard
```

# License

MIT. See the file LICENSE.TXT.
