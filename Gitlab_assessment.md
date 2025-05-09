# GitLab-Associate-Support-Engineer-Assessment

# Question #1

## *Write a Ruby or Bash script that will print usernames of all users on a Linux system together with their home directories. Here's some example output:*

```
gitlab:/home/gitlab
nobody:/nonexistent
.
.
```

---

# Step by Step

**How to List Usernames and Home Directories in Linux (WSL on Windows)**

## 1. Open the Terminal

> Ctrl + alt + T for Linux users
> (*On Windows using WSL, hit the Windows key and type Ubuntu*)

---

## Step 2: Create the Script with nano

> nano list\_users.sh

![Opening nano](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/open_nano_s.png)

> When Nano opens you will see it has a menu.

![Nano opened menu](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/nano_opened_s.png)

---

## Step 3: Add the Script Content

Copy and paste or write this script into nano:

```bash
#!/bin/bash
awk -F: '{ print $1 ":" $6 }' /etc/passwd
```

![Script in nano](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/script_written_s.png)

This selects the two fields we are interested in: \$1 *(username)* and \$6 *(home directory)*.

---

## Step 4: Save and Exit nano

> * Ctrl + O  press Enter to save
> * Ctrl + X to exit

---

## Step 5: Make the Script Executable

To run the script, you must make it executable. Otherwise, you'll get a "permission denied" error.

```bash
chmod +x list_users.sh
```

![Making executable](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/running_chmod_s.png)

---

## Step 6: Run the Script

```bash
./list_users.sh
```

![Script output](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/script_output_s.png)

---

# Question #2

## *We have sent you an image named `git_history.v3.png` showing a Git commit graph. What sequence of Git commands could have produced the commit graph depicted in the image?*

![Example of commit history](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/git_history.v3_s.png)

---

💡 **Note:**
In most of my day-to-day projects, I work with Git and GitHub through the VS Code interface. I often use pull requests to merge branches and review code, which typically triggers checks or formatting tools if they're configured in the repo.

For this question, I referred to the [IONOS Git Cheat Sheet](https://www.ionos.co.uk/digitalguide/websites/web-development/git-cheat-sheet/) to confirm the merge commands.

---

## Assumed Command Sequence:

```bash
git init
git add .
git commit -m "first commit"

git add .
git commit -m "second commit"

git checkout -b awesome-feature
# (Still on awesome-feature)

git checkout main
git add .
git commit -m "third commit"

git checkout awesome-feature
git add .
git commit -m "awesome feature"

git checkout main
git merge awesome-feature

git add .
git commit -m "fourth commit"
```

---

# Question #3

## *Write a brief blog post for GitLab that explains what Git is and what it can do for you.*

![Title banner with Git logo, GitLab logo, and author Tom Burns-T](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/blog_banner_s.png)

## Hey, I’m Tom 👋

I'm a developer who enjoys solving problems and making things that help others. I'm all about user-friendly experiences. Today, I'm writing a short blog post for [GitLab](https://gitlab.com) all about Git.

---

### What Is Git — What Does It Actually Do for You?

Git is a tool for something called version control. I remember the first time I heard that phrase. One vague word led to another. Let's break it down.

---

## What is Version Control?

Version control is a way of tracking and managing changes in coding projects.

> Maybe you read books or play video games. You use a bookmark to save your place in a book. And if you’re a true 90's kid like me, you used a save point in a game.

Git lets you:

* Save your progress
* Go back to earlier versions
* Collaborate without stepping on each other’s toes

![Save point from FF7 and bookmarked books](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/save_point.png)

Imagine a team working on software. They don’t all edit the same code. Each person creates a **branch** to work on features separately.

Once a feature is ready, it's reviewed and **merged** into the stable main branch.

---

## Why It Matters

Mistakes happen. Something might work locally but cause a merge issue later. With Git, you can roll back to a working version and trace what changed and who did it.

![Rewind metaphor](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/rewind.png)

Git makes teamwork safer and more manageable.

---

## So What Does Git Do for You?

It gives you:

* Confidence to experiment
* A safety net when things go wrong
* A timeline of every step you and your team take

![Safety net metaphor](https://github.com/Tomuos/gitlab-associate-support-engineer-assessment/raw/main/images/safety_net.png)

So when I say *Git is a version control tool*, I hope it now means something more useful than it did the first time you heard it.

---

# Question #4

## *Tell us about a recent issue you debugged or a problem you solved. How did you go about debugging it? What tools did you use? What was the outcome?*

### ⭐ Situation:

I was building a Chrome extension called **Site Read**, designed to improve web readability for neurodiverse users. The main feature boldens the first half of each word to aid focus.

Initially, the extension stripped punctuation, which made paragraphs harder to read.

---

### 🎯 Task:

Preserve standard punctuation (.,!? etc.) while still applying bold formatting to the first half of each word.

---

### 🛠️ Action:

My original function handled only letters and numbers. I rewrote it to allow punctuation, and my mentor recommended exploring **RegEx**. I updated the function:

```js
function keepSpacing(word) {
  return word.replace(/[^\w\s.,!?'"\u201c\u201d\u2018\u2019—–-]/g, '');
}
module.exports = keepSpacing;
```

I also broke the project into modules and added unit tests for each part. This made the code easier to manage and verify.

---

### 🎉 Result:

The function now handles most written punctuation. The project is modular and easier to maintain. I have a working **Minimum Viable Product (MVP)** that I continue to improve as I test.

---

## 🔗 References

1. **WSL Installation Guide – Microsoft Docs**  
   https://learn.microsoft.com/en-us/windows/wsl/install

2. **How to Print All Usernames on a System – GitHub**  
   https://github.com/rio197/How_to_print_all_usernames_on_system/tree/main

3. **Linux File Permissions Explained – Warp.dev**  
   https://www.warp.dev/terminus/linux-file-permissions-explained

4. **`passwd` File Manual – man7.org**  
   https://man7.org/linux/man-pages/man5/passwd.5.html

5. **ExplainShell – Command Explanation Tool**  
   https://explainshell.com/

6. **Google Searches**  
   - “how to run Linux scripts on Windows”  
   - “how to print usernames and directories”  
   *(Used for initial setup and command discovery)*
   - Git cheat sheets 
   - How to make a step-by-step guide for non technical people.  
   
7. **Markdown reference site**
   - https://stackedit.io/app#

8. **ChatGPT – Prompted for Guidance**  
   - Prompted: *“I'm going through the assessment for GitLab. I will be citing this as my first use of AI but all I want you to do is list the questions.”*  
   *(Used to help structure task breakdown)*

   - Q1: 
      - I have found some informations on scripts for linux and eve this github with some code suggested can you point me to some sites or reference material that might cover this in more detail.

      - I don't like trusting random code I've found online is there anywhere I can test this or find out what this does similar to RegExr would be good. 

      - For non-technical people some of the wording used on ExplainShell would be too much and not actually helpful.

      - I've gone through the site explanations and I want to know how my explaination sounds do you think I should add a note for windows users? 
   
   - Q2:

      - This is how I see this image. I think these would be the git commands. Did I miss anything? 

   
   - Q3:
      - Can you check the that what I have written is simple for non technical, you can suggest ways to improve it but I don't want a rewrite.

      - What is good size for image for the blog I want to convert them all to a standard size.
      
      - What’s the best image size for a blog banner? 

   - Q4:
      - Is what I have written clear enough? I'm using the star method 
      
      - This ``` usually allow for a code block,What other Markdown code block styles are there?



9. **Peer Support – Linux Guidance**  
   A friend recommended the following resources:
   - [Linux File Permissions – Warp.dev](https://www.warp.dev/terminus/linux-file-permissions-explained)
   - [Package Management Basics – DigitalOcean](https://www.digitalocean.com/community/tutorials/package-management-basics-apt-yum-dnf-pkg)
   - [Process Management in Linux – DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-ps-kill-and-nice-to-manage-processes-in-linux)
   - [Basic Network Utilities – Dev.to](https://dev.to/sachindra149/basic-network-utilities-1e9l)

   Asked him to check my working out on Q2 to make sure I hadn't missed anything. 
   
 10.  **IONOS Git Cheat Sheet**  
   - (https://www.ionos.co.uk/digitalguide/websites/web-development/git-cheat-sheet/)
   *(Used to confirm Git command structure for commit graph task)*

11. **Youtube**
  
   - **Explaining Technical Information to Non-Technical People**
  (https://youtu.be/pGK2EuLXL7A?si=Xd06fb0r0_AfIjzS)

  - **How to write technical blog posts - talk by Quincy Larson**(https://youtu.be/YODPgBadj80?si=XIneIzcm8RXd8gyQ)
