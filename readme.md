When there is no ascii character in string, `make_id()` returns empty string.
This scheme makes nodes with no ascii character remain anonymous, although they need to have name (like headings).

 ### Patch description
In `make_id()`, after drop every non-ascii characters, check whether id is empty string or not.
If id is empty string, let name be hex value of it's own, replace `0x` with `u` (since first character must be `[a-z]`.
(ex. `ø` (0x00f8) to `u00f8`, `øø` (0x00f8 0x00f8) to `u00f8u00f8`)
Otherwise (case when at least on ascii character exists), i didn't modify anything.
