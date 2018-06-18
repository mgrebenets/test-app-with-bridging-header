
Demo project for #1918.

Work on a fork, which is based on Uber fork.

Change `.buckfork` to `mgrebenets` and `.buckversion` to `07e7e1b69e` and turn `./buckw test mylib`.

Result: works as expected.

Change `.buckfork` to `facebook` and `.buckversion` to `6c2f9a` and try `./buckw test mylib` again.

Result: fails to import "MyLibPrivate.h"
