# LAB || ADVANCED GIT METHODS

## Description

This lab is about practicing advanced git methods. Some of them you already know, some of them you will learn today.

VS code has a tool to work with git. But in this lab we are going to use the terminal.

## Iteration 1 | Create a new branch

Create a new branch called `landing-page`.

```bash
git checkout -b landing-page
```

The checkout -b command creates a new branch and switches to it. Check that you are now in the correct branch.

```bash
git branch
```

This should display a list of branches. The one with the asterisk is the one you are currently in (should be landing-page).

## Iteration 2 | Create a new file

Create a new file called `index.html` and add the following content:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Landing Page</title>
  </head>
  <body>
    <h1>Welcome to our landing page</h1>
  </body>
</html>
```

Easy right? Just copy and paste the code above into a new file called `index.html`.

## Iteration 3 | Add and commit

When we are done by creating the file, we need to add it to the staging area. Staging area is like a the carton box where you put all the things you want to send to your friend. In this case, the friend is the repository 😎.

```bash
git add index.html
```

The command `git add` adds the file to the staging area. We can also add all the files at once by using the command `git add .`.

```bash
git add .
```

Now we need to commit the changes. Commit is like adding a note to the box. You can write a message to describe what you are sending.

```bash
git commit -m "Add index.html"
```

It's good to have a clear message to know what you did in that commit. The `-m` flag is used to add a message.

Nothing complicated, right? Let's move on.

## Iteration 4 | Push the branch

Now we need to push the branch to the repository. This is like sending the box to your friend (the repository).

```bash
git push origin landing-page
```

The `origin` is the name of the remote repository (in this case, this lab cloned from github). The `landing-page` is the name of the branch.

## Iteration 5 | Generating a conflict
We are going to create a conflict. We are going to change the `index.html` file also in the `main` branch. Remember what we said in class? Don't modify the same file in different branches or don't work in the same branch more than one person. 

Switch to the `main` branch.

```bash
git checkout main
```

Create a new file called `index.html` and add the following content:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Home</title>
  </head>
  <body>
    <h1>Welcome to our home page</h1>
  </body>
</html>
```

Add and commit the changes.

## Iteration 6 | Merge the branches
We are being naughty 🙈 and we are going to merge the branches.
Let's merge the `landing-page` branch into the `main` branch.

```bash
git merge landing-page
```

We can merge directly from the terminal. If there is a conflict, we need to solve it. We can open the file in VS code and solve the conflict.

Check the Source Control tab in VS code. You will see the file with the conflict. You can choose to keep the changes from the `main` branch or the `landing-page` branch.

![Source control](/screenshots/01.png)

In this screenshot there is a merging conflict with the readme file. 
In your case it will be the `index.html` file.

To solve the conflict, you need to remove the conflict markers `<<<<<<<`, `=======`, `>>>>>>>` and keep the changes you want.

After solving the conflict, you need to add and commit the changes.

```bash
git add index.html
git commit -m "Solve conflict"
git push origin main
```

Now the `main` branch has the latest changes.

## Iteration 7 | Delete the branch
How do we delete a branch that we don't need anymore? We can do it from the terminal.

```bash
git branch -d landing-page
```

The `-d` flag is used to delete the branch. 

## Iteration 8 | Update the changes on github

Now we need to update the changes on github so it doesn't have the `landing-page` branch anymore.

```bash 
git push origin --delete landing-page
```

This command deletes the branch from the remote repository. Crazy right? 😜
You can also delete the branch from the github interface.

## Iteration 9 | Go back in time
Yes, we can go back in time. We can go back to a previous commit. We can do this by using the `git log` command.

```bash
git log
```

The log is going to display a list of commits. Each commit has a hash. We can use the hash to go back to a previous commit.
Example of what we can see in the log:
```bash
commit 1a2b3c4d5e6f7g8h9i0j1k2l3m4n5o6p7q8r9s0t
Author: John Doe <
Date:   Mon Jan 1 00:00:00 2021 +0100

    Add index.html
```


