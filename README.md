#Simple Telegram Bot Sample


## Installation

To install the stable version:

```bash
npm install --save telegram-node-bot
```

This assumes you are using [npm](https://www.npmjs.com/) as your package manager.
If you don’t, you can access these files on [unpkg](https://unpkg.com/telegram-node-bot/), download them, or point your package manager to them.


## Get started

First of all you need to create your bot and get Token, you can do it right in telegram, just write to @BotFather.

Now let's write simple bot!

```js
'use strict'

const Telegram = require('telegram-node-bot')
const TelegramBaseController = Telegram.TelegramBaseController
const TextCommand = Telegram.TextCommand
const tg = new Telegram.Telegram('YOUR_TOKEN')

class PingController extends TelegramBaseController {
    /**
     * @param {Scope} $
     */
    pingHandler($) {
        $.sendMessage('pong')
    }

    get routes() {
        return {
            'pingCommand': 'pingHandler'
        }
    }
}

tg.router
    .when(
        new TextCommand('ping', 'pingCommand'),
        new PingController()
    )
```
That's it!
