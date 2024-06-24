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

## Usage

  `$ stfc-claim --user example@gmail.com --password pass1234 --claim...`

  `$ stfc-claim --help`

## Options

  -h, --help <u>string</u>       Show help

  -u, --user <u>string</u>       Scopley User Name

  -p, --password <u>string</u>   Scopley Password

  -c, --claim             Claim available gifts

  -a, --keep-alive        Keep gift claim running and claim available gifts
                          every 10 minutes

  -b, --bundles <u>string</u>    A comma seperated list of bundle ids to include

  -i, --ignore <u>string</u>    A comma seperated list of bundle ids to ignore

  -m, --max               If gifts that are at max amount should still be
                          claimed

  -v, --verbose           Enable verbose logging for debugging

