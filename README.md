
Demo project for [#1918](https://github.com/facebook/buck/issues/1918) and [#2074](https://github.com/facebook/buck/issues/2074).


# 2074

Change `.buckversion` to `f09152d` and run `./buckw build sample_tests`.

# 1918

Work on a fork, which is based on Uber fork.

Change `.buckfork` to `mgrebenets` and `.buckversion` to `07e7e1b69e` and turn `./buckw test sample`.

Result: works as expected.

Change `.buckfork` to `facebook` and `.buckversion` to `6c2f9a` and try `./buckw test sample` again.

Result: fails to import "MyLibPrivate.h"
