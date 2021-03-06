# GamePad.js [![Build Status](https://travis-ci.org/uupaa/GamePad.js.svg)](https://travis-ci.org/uupaa/GamePad.js)

[![npm](https://nodei.co/npm/uupaa.gamepad.js.svg?downloads=true&stars=true)](https://nodei.co/npm/uupaa.gamepad.js/)

Easy way to using GamePad API.


This module made of [WebModule](https://github.com/uupaa/WebModule).

## Documentation
- [Spec](https://github.com/uupaa/GamePad.js/wiki/)
- [API Spec](https://github.com/uupaa/GamePad.js/wiki/GamePad)

## Browser, NW.js and Electron

```js
<script src="<module-dir>/lib/WebModule.js"></script>
<script src="<module-dir>/lib/GamePadDevice.js"></script>
<script src="<module-dir>/lib/GamePad.js"></script>
<script>
GamePads.VERBOSE = true;

var players = [{ ... }, { ... }];

var pad = new GamePad(function(connect(player) {
    console.log("connected. player: " + player);
});

function gameLoop() {
    if (pad.connected) {
        pad.input();

        if (pad[0]) {
            input(pad[0].values, pad[0].diffs);
        }
        if (pad[1]) {
            input(pad[1].values, pad[1].diffs);
        }
    }
    update();
    render();
    requestAnimationFrame(gameLoop);
}
gameLoop();


function input(values,  // @arg Uint8Array - current values
               diffs) { // @arg Uint8Array - diff values
    // --- Jump ---
    if (diffs[GAMEPAD_KEY_A]) {
        if (values[GAMEPAD_KEY_A]) {  // A BUTTON OFF -> ON
            startJump(...);
        } else {       // A BUTTON ON -> OFF
            endJump(...);
        }
    }

    // --- D-PAD ---
    if (values[GAMEPAD_KEY_L]) {
        moveLeft(...);
    } else if (values[GAMEPAD_KEY_R]) {
        moveRight(...);
    }
}

</script>
```


