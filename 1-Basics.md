## Exercises: Listing files, navigation

Open up **Finder > Applications > Utilities > Terminal**

List out the files and directories on where you are by typing:

```
ls
```

To see where you are on your machine, type:

```
pwd
```

Let's try making a directory. To do that, type:

```
mkdir newdirectory
```

This will create a directory called `newdirectory` - it's the parameter that follows the command. For example, if you want to create a directory called `mango`, you would type:

```
mkdir mango
```

To navigate to the directory, you can use the `cd` command - **change directory**. So:

```
cd newdirectory
```

Note that there's a few navigation shortcuts. For example the `~` prefix puts you in your home directory. So to go to your Desktop, type:

```
cd ~Desktop
ls
```

Once again, `ls` lists out the files and directories of where you're in. To create a new empty file called `apple`, simply type:

```
touch apple
```

To see if you actually made it, you can type:

```
ls
```

To create copies of directories and files, we can use the `cp` command. For example, to make a copy of `apple` called `banana`, we can simply type:

```
cp apple banana
ls
```

Now, you're not going to want to copy files all the time - sometimes you're going to need to move them or rename them. To rename `apple` to `pineapple`, simply type:

```
mv apple pineapple
```

Note that commands work across directories. For example, to make a directory called `fruitbasket` and put all the files inside that directory, simply type:

```
mkdir fruitbasket
mv pineapple banana fruitbasket/
ls fruitbasket/
```

## A Guided Tour

You can go to the very "top" of your machine's directories by typing:

```
cd /
```

To list out the top-level directories, simply use `ls` again. You should see something similar to this:

```
Applications
Library
Network
System
Users
Volumes
bin
cores
dev
etc
home
macOS_SDK
net
opt
private
sbin
tmp
usr
var
```

It's a lot, but don't worry. There's only a couple of directories that we care about - these ones:

```
bin
etc
home
sbin
tmp
usr
var
```

To briefly list it out:

**/bin/** contains the essential commands that we have in the system. All the commands we were typing earlier exist there.

**/etc/** contains system configuration. If you need to change something in your system, you're likely to go here.

**/sbin/** contains your system binaries. This is like **/bin/**, except a lot of the commands are Administrator-only.

**/tmp/** is for temporary files.

**/usr/** is where user-land data and binaries exist.

**/var/** is for *variable data*, or things that change a lot. This is where your logs and spool files will be in.

To list out the contents of each directory, simply type:

```
ls /bin/
```

## Exercise

#### Making directories

Create a file called `test.txt` in your Desktop using **TextEdit** or similar. How would you:

1.) *Create a directory called `/tmp/test/`*

2.) *Move the `test.txt` file inside the directory?*

3.) *Go to that directory?*
