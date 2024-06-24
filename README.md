# STFC Warp Speed Gift Claim

```text
                                            _____
                                __...---'-----`---...__
                            _===============================
            ______________,/'      `---..._______...---'
            (____________LL). .    ,--'
            /    /.---'       `. /
            '--------_  - - - - _/
                    `~~~~~~~~'

░█▀▀░▀█▀░█▀▀░█▀▀░░░█░█░█▀█░█▀▄░█▀█░░░█▀▀░█▀█░█▀▀░█▀▀░█▀▄░░░█▀▀░█░░░█▀█░▀█▀░█▄█
░▀▀█░░█░░█▀▀░█░░░░░█▄█░█▀█░█▀▄░█▀▀░░░▀▀█░█▀▀░█▀▀░█▀▀░█░█░░░█░░░█░░░█▀█░░█░░█░█
░▀▀▀░░▀░░▀░░░▀▀▀░░░▀░▀░▀░▀░▀░▀░▀░░░░░▀▀▀░▀░░░▀▀▀░▀▀▀░▀▀░░░░▀▀▀░▀▀▀░▀░▀░▀▀▀░▀░▀
```

Claim your STFC Web Gifts at warp speed. Simply run with your username and
password and your gifts will be auto claimed every 10 minutes

## Installation

Download the latest version of stfc-warp-claim [here](https://github.com/arschmitz/stfc-warp-claim/archive/refs/heads/main.zip) unzip and run the executable for your operating system.

## Useage

stfc-warp-claim is a command line utility allowing the claiming of gifts from the stfc web store. By default it runs based on the command line options below. An optional http server can also be started to accept commands

Note: Gifts marked as "special" or that have a cost will not be claimed. 

### CLI Usage

  `$ stfc-claim --user example@gmail.com --password pass1234 --claim...`

  `$ stfc-claim --help`

### CLI Options

  -h, --help <u>string</u>       Show help

  -u, --user <u>string</u>       Scopley User Name

  -p, --password <u>string</u>   Scopley Password

  -c, --claim             Claim available gifts

  -a, --keepAlive        Keep gift claim running and claim available gifts
                          every 10 minutes

  -b, --bundles <u>string</u>    A comma seperated list of bundle ids to include

  -i, --ignore <u>string</u>    A comma seperated list of bundle ids to ignore

  -m, --max               If gifts that are at max amount should still be
                          claimed

  -v, --verbose           Enable verbose logging for debugging

  -s, --server             run http server to accept commands

  --port  <u>number</u>           Port for server to listen for requests on (Default 3131)
 
  --interval <u>number</u>        Interval in seconds on which to check for gifts

## Server API

### `[POST][/claim]` Claim gifts with given options

```js
fetch("http://localhost:3131/claim", {
    "headers": {
        "content-type": "application/json",
    },
    "method": "POST",
    body: JSON.stringify({
      max: true,
    })
});
```

Claim Available Gifts.

+ Request

    + Body ([object[ClaimOptions]](#ClaimOptions))

+ Response 200 (application/json)

    + Attributes ([array[Gift]](#Gift))

### `[POST][/start]` Start automatic gift claim

```js
fetch("http://localhost:3131/start", {
    "headers": {
        "content-type": "application/json",
    },
    "method": "POST",
    body: JSON.stringify({
      max: true,
    })
});
```

Start Automatic gift claim on a given interval.

+ Request

    + Body ([object[ClaimOptions]](#ClaimOptions))

+ Response 200 (application/json)

### `[GET][/stop]` Start automatic gift claim

```js
fetch("http://localhost:3131/stop", {
    "headers": {
        "content-type": "application/json",
    },
});
```

Stop automatic gift claim

+ Response 200 (application/json)

### `[GET][/kill]` Terminate stfc-warp-claim

```js
fetch("http://localhost:3131/kill", {
    "headers": {
        "content-type": "application/json",
    },
});
```

Terminate stfc-warp-claim

+ Response 200 (application/json)
## Data structures

### Gift
* `id` <u>Number[required]</u>: Id of the gift bundle

* `title` <u>String[required]</u>: Title of the gift bundle,

* `status` <u>String</u>[required] <b>[not claimed | success | error]</b>: Status of the gift claim

* `reason` <u>String</u>[optional] <b>[not available | not included | is special | has cost | at max]: Reason a gift was not claimed</b> 

### ClaimOptions 

* `user` <u>String</u>[optional]: Scopley Username (will invalidate current login)

* `password` <u>String</u>[optional]: Scopley Password (will invalidate current login)

* `bundleIds` <u>Array(Number)[optional]</u>: Array of bundle ids to claim
* `ignoreIds` <u>Array(Number)[optional]</u>: Array of bundle ids to ignore
* `keepAlive` <u>Boolean</u>[optional]: Keep gift claim running and claim available gifts every 10 minutes
* `max` <u>Boolean</u>[optional]: If gifts that are at max amount should still be claimed
* `interval` <u>Number</u>[optional]: Interval in seconds on which to check for gifts
