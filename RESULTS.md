# Special-Character Branch/File Coverage

Owner: b.patidar@veeam.com

Fixture repo for testing the Securiti GitHub connector's handling of special characters in branch names and file names. Each row below was attempted as its own branch `test-branch-<label>-<char>-x`, with a matching file `special-chars/file-<label>-<char>-x.txt` committed on that branch where creation succeeded.

| Char | Label | Branch created | File created | Notes |
|---|---|---|---|---|
| `!` | bang | OK | OK |  |
| `"` | dquote | OK | OK |  |
| `#` | hash | OK | OK |  |
| `$` | dollar | OK | OK |  |
| `%` | percent | OK | OK |  |
| `&` | amp | OK | OK |  |
| `'` | squote | OK | OK |  |
| `(` | lparen | OK | OK |  |
| `)` | rparen | OK | OK |  |
| `*` | star | FAIL | - | not a valid ref name |
| `+` | plus | OK | OK |  |
| `,` | comma | OK | OK |  |
| `-` | hyphen | OK | OK |  |
| `.` | dot | OK | OK |  |
| `/` | slash | OK | SKIP | '/' is the path separator, cannot appear inside one filename component |
| `:` | colon | FAIL | - | not a valid ref name |
| `;` | semi | OK | OK |  |
| `<` | lt | OK | OK |  |
| `=` | eq | OK | OK |  |
| `>` | gt | OK | OK |  |
| `?` | question | FAIL | - | not a valid ref name |
| `@` | at | OK | OK |  |
| `[` | lbracket | FAIL | - | not a valid ref name |
| `\` | backslash | FAIL | - | not a valid ref name |
| `]` | rbracket | OK | OK |  |
| `^` | caret | FAIL | - | not a valid ref name |
| `_` | underscore | OK | OK |  |
| `` ` `` | backtick | OK | OK |  |
| `{` | lbrace | OK | OK |  |
| `|` | pipe | OK | OK |  |
| `}` | rbrace | OK | OK |  |
| `~` | tilde | FAIL | - | not a valid ref name |
| (space) | space | FAIL | - | not a valid ref name |

## Summary
- Branches created: 25/33
- Files created: 24/33
- 8 characters are rejected by git's own ref-name rules and cannot exist in a branch name under any circumstances: `*`, `:`, `?`, `[`, `\`, `^`, `~`, and literal space.
- `/` is valid in a branch name (git treats it as a hierarchical separator) but cannot be part of a single file name, so its branch has no dedicated test file.
