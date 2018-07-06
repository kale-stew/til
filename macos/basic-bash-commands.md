# Bash Commands for Everyday Use

As a Mac user, when I'm not using zsh, I find myself using bash commands to navigate my files. These are handy bash commands I type regularly.

## Working with Files

Create a new file

```sh
touch README.md
```

Find a file

```sh
# look for a file name containing "blue" and "dog"
locate -i *blue**dog*
```

Rename a file

```sh
mv old-file-name new-file-name
```

Copy a file

```sh
cp original-file new-file
```

Remove a file

```sh
rm garbage-file
```

## Working with Directories

Create a new directory

```sh
mkdir fancy-new-project
```

Read the contents of a directory

```sh
ls my-app
```

Change current directory

```sh
# go forwards
cd path/to/my-project

# or backwards
cd ..
```

You can use `mv` to

1. Rename a directory, given `new-dir-name` does not already exist

    ```sh
    mv old-dir-name new-dir-name
    ```

2. Move contents of a directory (given `existing-new-project` exists)

    ```sh
    mv old-project existing-new-project
    ```

Similarly, you can use `cp` to

1. Create a named duplicate, given `fancy-new-dir` does not already exist

    ```sh
    cp -r old-project fancy-new-dir
    ```

2. Move contents of a directory (given `existing-project` exists)

    ```sh
    cp -r complete-app existing-project
    ```

Remove a directory

```sh
# given empty-project contains no files
rmdir empty-project

# removes trash-app and any files it contains
rm -r trash-app
```

## Working with Files _and_ Directories

Make a copy of a file in an existing directory `my-new-app`

```sh
cp new-file my-new-app
```

Move a file into an existing directory `fancy-project`

```sh
mv my-file fancy-project
```
