# Makefile help comments

Makefile help comments: how you can add easy documentation to a Makefile.

Add this task to a Makefile:

```makefile
.PHONY: help
help:
	@awk '/^##/{a=1-a}a' $(MAKEFILE_LIST) | cut -c3-
```

Then add any help comments to your Makefile. A help comment starts with two hash marks, and ends with two hash marks.

```makefile
##
# This is a help comment.
# You can use as many lines as you wish.
##
```

Now you can run the task:

```sh
make help
```


## Makefile example

```
##
# Makefile help comments: how you can add easy documentation to a Makefile.
#
# A help comment starts with two hash marks, and ends with two hash marks.
# This syntax purposefully makes it easy for developers to convert any
# existing Makefile comments into help comments.
#
# Compared to other kinds of well-known make self-documentation tools,
# this implementation is simpler to use and also is much more flexible.
#
# To use this:
#
#     make help
#
# https://github.com/sixarm/makefile-help-comments
##

## 
# help: display this help message.
##
.PHONY: help
help:
	@awk '/^##/{a=1-a}a' $(MAKEFILE_LIST) | cut -c3-

##
# You can write help comments anywhere you want,
# such as between tasks, like this help comment.
##

##
# alfa: echo the word alfa.
##
alfa: 
	@echo "alfa"

##
# You can write anything you want in a help comment,
# such as ASCII art, and whatever you write is displayed.
#
#          ^__^
#          (oo)\_______
#          (__)\       )\/\
#              ||----w |
#              ||     ||
##

## 
# bravo: echo the word bravo.
##
bravo: 
	@echo "bravo"

# This line is a normal comment.
# This line is another normal comment.
# These normal comments are not printed by the help task.

## 
# charlie: echo the word charlie.
##
charlie: 
	@echo "charlie"

##
# If you wish, you can end with a footer comment with more information.
# To contact the author, email joel@joelparkerhenderson.com.
##
```
