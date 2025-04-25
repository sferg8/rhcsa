cp file /tmp and cp file /tmp/ behave identically if /tmp is a directory. But here are the rules:

If destination is an existing directory (with or without /), the file is copied into it:
cp file /tmp → /tmp/file
cp file /tmp/ → /tmp/file

If destination is a nonexistent path without trailing slash, cp treats it as a file rename:
cp file /tmp → creates /tmp (as file) only if /tmp does not exist

If destination has a trailing slash but doesn't exist, it's an error:
cp file /tmp/ → error: /tmp/ not found

Get to know tar and compression adding and removing specfic files