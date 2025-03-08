See the [upstream repo](https://github.com/jqlang/jq). The purpose of this repo is to add some builtins for tracking when arrays/objects get copied, which is useful for making sure that complicated jq program runs are asymptotically correct.

We add three builtins:
* `_tag(n)` which marks the array/object it's passed with tag `n`. When an array or object with a nonzero tag is copied, a message with the tag and type will be printed to stderr. Note `tag` will add tags for values which are neither objects nor arrays, but only copies of these are mentioned (since other copies are cheap). The current behavior copies the tag on copies.
* `_readtag(a)` which returns the tag `a` is marked with
* `_refcount` which returns the current reference count of the object it is passed if it's an array or object and raises an error otherwise
