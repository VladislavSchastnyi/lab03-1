## Laboratory work III

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab03** и с лиценцией **MIT**
- [ ] 2. Ознакомиться со ссылками учебного материала
- [ ] 3. Выполнить инструкцию учебного материала
- [ ] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```ShellSession
$ export GITHUB_USERNAME=<имя_пользователя>
$ export GITHUB_EMAIL=<адрес_почтового_ящика>
$ alias edit=<nano|vi|vim|subl>
```

```ShellSession
$ cd ${GITHUB_USERNAME}/workspace
$ source scripts/activate
```

```ShellSession
$ mkdir projects/lab03 && cd projects/lab03
$ git init
Initialized empty Git repository in /home/ubuntu/workspace/VladislavSchastnyi/workspace/projects/lab03/.git/
$ git config --global user.name ${GITHUB_USERNAME}
$ git config --global user.email ${GITHUB_EMAIL}
$ git config -e --global
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03.git
$ git pull origin master
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/VladislavSchastnyi/lab03
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master
$ touch README.md
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        README.md

nothing added to commit but untracked files present (use "git add" to track)
$ git add README.md
$ git commit -m"added README.md"
[master d487e77] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
$ git push origin masterUsername for 'https://github.com': VladislavSchastnyi
Password for 'https://VladislavSchastnyi@github.com': 
Counting objects: 3, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 288 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/VladislavSchastnyi/lab03.git
   c21096d..d487e77  master -> master
```

Добавить на сервисе **GitHub** в репозитории **lab03** файл **.gitignore**
со следующем содержимом:

```ShellSession
*build*/
*install*/
*.swp
.idea/
```

```ShellSession
$ git pull origin master
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/VladislavSchastnyi/lab03
 * branch            master     -> FETCH_HEAD
   d487e77..f02fa2f  master     -> origin/master
Updating d487e77..f02fa2f
Fast-forward
 .gitignore | 4 ++++
 1 file changed, 4 insertions(+)
 create mode 100644 .gitignore
$ git log
commit f02fa2f8166f1132a7814f7a6b733fc99f0a39da (HEAD -> master, origin/master)
Author: VladislavSchastnyi <32384821+VladislavSchastnyi@users.noreply.github.com>
Date:   Thu Jun 7 22:58:30 2018 +0300

    Create  .gitignore

commit d487e770710b16699cd5086196c9a334b16c6d05
Author: VladislavSchastnyi <schastnyivladislav@gmail.com>
Date:   Thu Jun 7 19:56:30 2018 +0000

    added README.md

commit c21096d9087224a1746143c51c2a0fe931ecce10
Author: VladislavSchastnyi <32384821+VladislavSchastnyi@users.noreply.github.com>
Date:   Thu Jun 7 22:28:08 2018 +0300

    Initial commit
```

```ShellSession
$ mkdir sources
$ mkdir include
$ mkdir examples
$ cat > sources/print.cpp <<EOF
#include <print.hpp>

void print(const std::string& text, std::ostream& out) {
  out << text;
}

void print(const std::string& text, std::ofstream& out) {
  out << text;
}
EOF
```

```ShellSession
$ cat > include/print.hpp <<EOF
#include <string>
#include <fstream>
#include <iostream>

void print(const std::string& text, std::ostream& out = std::cout);
void print(const std::string& text, std::ofstream& out);
EOF
```

```ShellSession
$ cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv) {
  print("hello");
}
EOF
```

```ShellSession
$ cat > examples/example2.cpp <<EOF
#include <fstream>
#include <print.hpp>

int main(int argc, char** argv) {
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
```

```ShellSession
$ edit README.md
```

```ShellSession
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        examples/
        include/
        sources/

no changes added to commit (use "git add" and/or "git commit -a")
$ git add .
$ git commit -m"added sources"
[master 6cc48b6] added sources
 5 files changed, 28 insertions(+)
 create mode 100644 examples/example1.cpp
 create mode 100644 examples/example2.cpp
 create mode 100644 include/print.hpp
 create mode 100644 sources/print.cpp
$ git push origin master
Username for 'https://github.com': VladislavSchastnyi
Password for 'https://VladislavSchastnyi@github.com': 
Counting objects: 10, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (7/7), done.
Writing objects: 100% (10/10), 986 bytes | 0 bytes/s, done.
Total 10 (delta 0), reused 0 (delta 0)
To https://github.com/VladislavSchastnyi/lab03.git
   f02fa2f..6cc48b6  master -> master
```

## Report

```ShellSession
$ cd ~/workspace/labs/
$ export LAB_NUMBER=03
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER}.git tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m "lab${LAB_NUMBER}"
```

## Links

- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2017 Братья Вершинины
```
