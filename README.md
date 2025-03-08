See the [upstream repo](https://github.com/jqlang/jq). The purpose of this repo is to add some builtins for tracking when arrays/objects get copied, which is useful for making sure that complicated jq program runs are asymptotically correct.

We add three builtins:
* `acopy(n)` which marks the array/object it's passed with tag `n`--nonzero tags are reported on copies (note `n` should fit in one byte, otherwise it will be silently truncated); note `acopy` will add tags for values which are neither objects nor arrays, but only copies of these are mentioned (since other copies are cheap).
* `ccopy(a)` which returns the tag `a` is marked with
* `refcnt` which returns the current reference count of the object it is passed if it's an array or object and raises an error otherwise
