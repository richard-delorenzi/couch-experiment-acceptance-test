Some help on RestFixture
========================

This document cantains some of the things I have discovered while using RestFixture

Multiple setHeader
------------------

setHeader is used to add headers to the following requests. If you have multiple headers you need to put them one per line. To do this in fitnesse enclose them in `!- … -!`. e.g. 

    |setHeaders|!-Authorization: Basic YWRtaW46cGFzc3dvcmQ=
    Accept: application/json -!|


Authentication header
---------------------

I have a setHeader of `Authorization: Basic YWRtahe45Pkhth3dvcmQ=` I used wireshark to snoop it, while using a web browser.

Json
----
If the pages you are fetching are JSON then you need to do `|setHeader|Accept: application/json|` at the top of the table. Then in the ?body section you put a javascript expression, if it is true then it passes. `jsonbody` is the object returned. e.g. if `{"ok":true}` is expected then write `jsonbody.ok`

You can not use `||` for `or`. So add to top of page `!define or { || }` then use `${or}` instead of `||`.

