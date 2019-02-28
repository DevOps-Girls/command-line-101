## File permissions and flags

Note that commands in Linux have flags. The `ls` command we used earlier has a lot of other options - to see the options available, type:

```
man ls
```

`man` is a command to display the *manual* for a specific command. To exit the page, type `q`.

Now that we know that, we can see more from `ls` - by using the *long format* for display. For example, we can run a list in long format for the `/tmp/test` directory we made earlier, by running:

```
ls -l /tmp/test/
```

Which should output something like:

```
drwxr-xr-x   3 john.contad  wheel  102 Mar  1 10:40 .
drwxrwxrwt  14 root         wheel  476 Mar  1 10:40 ..
-rw-r--r--   1 john.contad  wheel    0 Mar  1 10:40 test.txt
```

On the first column, you have the permissions for the object, followed by the owner, the group, and last time the file was modified or created. The first column is particularly helpful, because this lists what we can do with the file.

Note that the format stands for three sets of `read`, `write`, and `execute` permissions for the `user`, the `group`, and `everyone` - respectively.

For example, changing `test.txt` to be *readable and writable and executable* by the `user`, we'll need to modify the bits in the file to be like `rwxr--r--`. In binary, it would look like:

```
111 100 100
```

Which in real numbers is:

```
7 4 4
```

When we execute the command to change permissions ( `chmod` ), we'll need to run:

```
chmod 744 /tmp/test/test.txt
```
