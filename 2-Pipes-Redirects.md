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

And if we're changing `test.txt` to be *readable and executable* by the `user` and `group`, we'll need to modify the bits in the file to be like: `r-xr--r--`. In binary, it would look like:

```
101 101 100
```

Which in real numbers is:

```
5 5 4
```

When we execute the command to change permissions ( `chmod` ), we'll need to run:

```
chmod 554 /tmp/test/test.txt
```

## Redirects

### Redirecting standard output

The output of commands can be redirected to a file. To do so, simply use the `>` character like so:

```
ls > /tmp/banana.txt
```

To see the contents of the file, you can use the `cat` command, like so:

```
cat /tmp/banana.txt
```

Note that the `>` character *overwrites* the contents of the destination file. If you were to run a redirection to the same file, the contents would be replaced. For example:

```
echo BANANA > /tmp/banana.txt
cat /tmp/banana.txt
```

To append output to the end of the file, simply use `>>` instead of `>`. For example:

```
echo BANANA > /tmp/banana.txt
echo BANANA >> /tmp/banana.txt
echo BANANA >> /tmp/banana.txt
```

Would make the `banana.txt` file contain:

```
BANANA
BANANA
BANANA
```

### Standard output

Note that it is possible to redirect files to commands as well. For example, if you created a file that contained a list of fruits like so:

```
echo apple > fruit.txt
echo guava >> fruit.txt
echo banana >> fruit.txt
echo grapes >> fruit.txt
```

You can redirect the file to a command, like so:

```
sort < fruit.txt
```

You can also redirect the output of the previous redirection like so:

```
sort < fruit.txt > sortedfruit.txt
```

### Pipes

You can use pipes ( `|` ) to redirect output to commands as well. For example, you can pipe the output of `ls` to `sort` like so:

```
ls / | sort
```

This should give you an alphabetized list. You can also run an equivalent of the standard input redirection that you previously ran, by outputting the contents of the file using `cat`:

```
cat fruit.txt | sort
``` 

### Exercise

Try to create a newline-separated file like so:

```
echo banana > fruit.txt
echo banana >> fruit.txt
echo banana >> fruit.txt
echo banana >> fruit.txt
echo apple >> fruit.txt
echo apple >> fruit.txt
echo grapes >> fruit.txt
echo guavas >> fruit.txt
echo dates >> fruit.txt
```

This should create a file that looks like this:

```
$ cat fruit.txt 
banana
banana
banana
banana
apple
apple
grapes
guavas
dates
```

How would you use pipes ( `|` ) to run this command through `sort` and `uniq`, so that it's alphabetized and deduplicated?
