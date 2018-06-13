## How to: Git Basics

### Create a new Repository in an Existing Directory
create a new directory, open it and perform a 

    git init
    
to create a new git repository

### Checkout a Repository
create a working copy of a local repository by running 

    git clone /path/to/repository
    
when using a remote server, you use the command

    git clone username@host:/path/to/repository

### Workflow
a local repository consists of three 'trees' maintained by git. The first is the **Working Directory** which holds the actual files. The second one is the **Index** which acts as a staging area and finally the **Head** which points to the last commit. 

### Add & Commit
you can propose changes (adding it to **Index**) using

    git add <filename> 
    git add *
    
to actually commit these changes use

    git commit -m 'commit message: what's that commit about?'
    
now the file is committed to the **Head**, but not in the remote repository yet.

### Pushing Changes
changes are now in the **Head** of your local working copy. To send those chnages to your remote repository, execute

    git push origin master
    
**note:** change *master* to whatever branch you want to push your changes to.

### Branching
branches are used to develop features isolated from each other. The *master* branch is the 'default' branch when you create a repository. Use other branches for development and merge them back to the master branch uppn completion. 

create a new branch named 'feature_x' and switch to it using

    git checkout -b feature_x
    
switch back to master using

    git checkout master
    
delete the branch again using

    git branch -d feature_x
    
a branch is not available to others unless you push the branch to your remote repository
    
    git push origin <branch>
    
### Update & Merge
to update your local repository to the newest commit, execute in your working directory
    
    cd path/to/working-directory
    git pull
    
this will *fetch* and *merge* remote changes.

to merge another branch into your active branch (e.g. master), use

    git merge <branch>
    
in both cases git tries to auto-merge changes. This is not always possible and may results in **conflicts**. Merging those conflicts manually by editing the files shown by git. After changing, you need to mark them as merges with

    git add <file name>
    
before merging changes, you can also preview them by using

    git diff <source_branch> <target_branch>
    
### Upstream and Origin
working with an upstream project through a *fork* of that project requires your working repository to know how to reach two remotes. By cloning your fork of the repository, your fork starts out as the only remote for that clone to work with. This remote uses the default name of **origin**. You will be able to pull and fetch from **origin** to your working repository. You won't be able to push to the original from which you forked.

you can pull (or fetch then merge) from the original repository by configuring it as an additional remote. This convention is to call this remote **upstream**. 

to add the original repository as the remote named **upstream** in your working repository, use 

    git remote add upstream username@host:/path/to/repository
    
you can then issure, for example 

    git pull upstream
    
to bring upstream changes into your repository.

#### Visualizing the above mentiond concepts:
<img src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiIHN0YW5kYWxvbmU9Im5vIj8+Cjwh%0D%0ARE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4wLy9FTiIgImh0dHA6Ly93d3cu%0D%0AdzMub3JnL1RSLzIwMDEvUFItU1ZHLTIwMDEwNzE5L0RURC9zdmcxMC5kdGQiPgo8c3ZnIHhtbG5z%0D%0APSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMu%0D%0Ab3JnLzE5OTkveGxpbmsiIHdpZHRoPSIyOWNtIiBoZWlnaHQ9IjE5Y20iIHZpZXdCb3g9Ii0yNzAg%0D%0AMzkgNTc4IDM2MiI+CiAgPGc+CiAgICA8Zz4KICAgICAgPGVsbGlwc2Ugc3R5bGU9ImZpbGw6ICNm%0D%0AZmZmZmYiIGN4PSIxOS4zNjY3IiBjeT0iMzQ0LjY2NyIgcng9Ijg4LjU2NzMiIHJ5PSI1NS4wMzM2%0D%0AIi8+CiAgICAgIDxlbGxpcHNlIHN0eWxlPSJmaWxsOiBub25lOyBmaWxsLW9wYWNpdHk6MDsgc3Ry%0D%0Ab2tlLXdpZHRoOiAyOyBzdHJva2U6ICMwMDAwMDAiIGN4PSIxOS4zNjY3IiBjeT0iMzQ0LjY2NyIg%0D%0Acng9Ijg4LjU2NzMiIHJ5PSI1NS4wMzM2Ii8+CiAgICAgIDx0ZXh0IGZvbnQtc2l6ZT0iMTIuNzk5%0D%0AOCIgc3R5bGU9ImZpbGw6ICMwMDAwMDA7dGV4dC1hbmNob3I6bWlkZGxlO2ZvbnQtZmFtaWx5OnNh%0D%0AbnMtc2VyaWY7Zm9udC1zdHlsZTpub3JtYWw7Zm9udC13ZWlnaHQ6bm9ybWFsIiB4PSIxOS4zNjY3%0D%0AIiB5PSIzNDguNTY3Ij4KICAgICAgICA8dHNwYW4geD0iMTkuMzY2NyIgeT0iMzQ4LjU2NyI+d29y%0D%0Aa2luZzwvdHNwYW4+CiAgICAgIDwvdGV4dD4KICAgIDwvZz4KICAgIDxnPgogICAgICA8ZWxsaXBz%0D%0AZSBzdHlsZT0iZmlsbDogI2ZmZmZmZiIgY3g9IjIxOC42MzQiIGN5PSI5NS4xOTIxIiByeD0iODgu%0D%0ANTY3MyIgcnk9IjU1LjAzMzYiLz4KICAgICAgPGVsbGlwc2Ugc3R5bGU9ImZpbGw6IG5vbmU7IGZp%0D%0AbGwtb3BhY2l0eTowOyBzdHJva2Utd2lkdGg6IDI7IHN0cm9rZTogIzAwMDAwMCIgY3g9IjIxOC42%0D%0AMzQiIGN5PSI5NS4xOTIxIiByeD0iODguNTY3MyIgcnk9IjU1LjAzMzYiLz4KICAgICAgPHRleHQg%0D%0AZm9udC1zaXplPSIxMi43OTk4IiBzdHlsZT0iZmlsbDogIzAwMDAwMDt0ZXh0LWFuY2hvcjptaWRk%0D%0AbGU7Zm9udC1mYW1pbHk6c2Fucy1zZXJpZjtmb250LXN0eWxlOm5vcm1hbDtmb250LXdlaWdodDpu%0D%0Ab3JtYWwiIHg9IjIxOC42MzQiIHk9IjgzLjA5MjEiPgogICAgICAgIDx0c3BhbiB4PSIyMTguNjM0%0D%0AIiB5PSI4My4wOTIxIj5mb3JrPC90c3Bhbj4KICAgICAgICA8dHNwYW4geD0iMjE4LjYzNCIgeT0i%0D%0AOTkuMDkyMSI+b3JpZ2luPC90c3Bhbj4KICAgICAgICA8dHNwYW4geD0iMjE4LjYzNCIgeT0iMTE1%0D%0ALjA5MiI+eW91cm5hbWUvaGZvc3M8L3RzcGFuPgogICAgICA8L3RleHQ+CiAgICA8L2c+CiAgICA8%0D%0AZz4KICAgICAgPGVsbGlwc2Ugc3R5bGU9ImZpbGw6ICNmZmZmZmYiIGN4PSItMTc5LjkwMSIgY3k9%0D%0AIjk3LjY2NyIgcng9Ijg4LjU2NzMiIHJ5PSI1NS4wMzM2Ii8+CiAgICAgIDxlbGxpcHNlIHN0eWxl%0D%0APSJmaWxsOiBub25lOyBmaWxsLW9wYWNpdHk6MDsgc3Ryb2tlLXdpZHRoOiAyOyBzdHJva2U6ICMw%0D%0AMDAwMDAiIGN4PSItMTc5LjkwMSIgY3k9Ijk3LjY2NyIgcng9Ijg4LjU2NzMiIHJ5PSI1NS4wMzM2%0D%0AIi8+CiAgICAgIDx0ZXh0IGZvbnQtc2l6ZT0iMTIuNzk5OCIgc3R5bGU9ImZpbGw6ICMwMDAwMDA7%0D%0AdGV4dC1hbmNob3I6bWlkZGxlO2ZvbnQtZmFtaWx5OnNhbnMtc2VyaWY7Zm9udC1zdHlsZTpub3Jt%0D%0AYWw7Zm9udC13ZWlnaHQ6bm9ybWFsIiB4PSItMTc5LjkwMSIgeT0iMTAxLjU2NyI+CiAgICAgICAg%0D%0APHRzcGFuIHg9Ii0xNzkuOTAxIiB5PSIxMDEuNTY3Ii8+CiAgICAgIDwvdGV4dD4KICAgIDwvZz4K%0D%0AICAgIDxnPgogICAgICA8bGluZSBzdHlsZT0iZmlsbDogbm9uZTsgZmlsbC1vcGFjaXR5OjA7IHN0%0D%0Acm9rZS13aWR0aDogMjsgc3Ryb2tlOiAjMDAwMDAwIiB4MT0iLTEyNy41OTUiIHkxPSIxNDYuNjI4%0D%0AIiB4Mj0iLTIwLjQ1NzUiIHkyPSIyODYuMTAxIi8+CiAgICAgIDxwb2x5Z29uIHN0eWxlPSJmaWxs%0D%0AOiAjMDAwMDAwIiBwb2ludHM9Ii0xNS44ODg3LDI5Mi4wNDkgLTI1Ljk0NTYsMjg3LjE2NSAtMjAu%0D%0ANDU3NSwyODYuMTAxIC0xOC4wMTUzLDI4MS4wNzMgIi8+CiAgICAgIDxwb2x5Z29uIHN0eWxlPSJm%0D%0AaWxsOiBub25lOyBmaWxsLW9wYWNpdHk6MDsgc3Ryb2tlLXdpZHRoOiAyOyBzdHJva2U6ICMwMDAw%0D%0AMDAiIHBvaW50cz0iLTE1Ljg4ODcsMjkyLjA0OSAtMjUuOTQ1NiwyODcuMTY1IC0yMC40NTc1LDI4%0D%0ANi4xMDEgLTE4LjAxNTMsMjgxLjA3MyAiLz4KICAgIDwvZz4KICAgIDxnPgogICAgICA8bGluZSBz%0D%0AdHlsZT0iZmlsbDogbm9uZTsgZmlsbC1vcGFjaXR5OjA7IHN0cm9rZS13aWR0aDogMjsgc3Ryb2tl%0D%0AOiAjMDAwMDAwIiB4MT0iMTg0Ljc0MSIgeTE9IjE0Ni4wMzciIHgyPSI3MS42ODQ2IiB5Mj0iMjkw%0D%0ALjA0OCIvPgogICAgICA8cG9seWdvbiBzdHlsZT0iZmlsbDogIzAwMDAwMCIgcG9pbnRzPSI2Ny4w%0D%0ANTMzLDI5NS45NDcgNjkuMjk1NCwyODQuOTk0IDcxLjY4NDYsMjkwLjA0OCA3Ny4xNjEyLDI5MS4x%0D%0ANjkgIi8+CiAgICAgIDxwb2x5Z29uIHN0eWxlPSJmaWxsOiBub25lOyBmaWxsLW9wYWNpdHk6MDsg%0D%0Ac3Ryb2tlLXdpZHRoOiAyOyBzdHJva2U6ICMwMDAwMDAiIHBvaW50cz0iNjcuMDUzMywyOTUuOTQ3%0D%0AIDY5LjI5NTQsMjg0Ljk5NCA3MS42ODQ2LDI5MC4wNDggNzcuMTYxMiwyOTEuMTY5ICIvPgogICAg%0D%0APC9nPgogICAgPGc+CiAgICAgIDxsaW5lIHN0eWxlPSJmaWxsOiBub25lOyBmaWxsLW9wYWNpdHk6%0D%0AMDsgc3Ryb2tlLXdpZHRoOiAyOyBzdHJva2U6ICMwMDAwMDAiIHgxPSItODkuMzMxMyIgeTE9Ijkw%0D%0ALjY2NyIgeDI9IjEyMC4zMzMiIHkyPSI5NC45OTEzIi8+CiAgICAgIDxwb2x5Z29uIHN0eWxlPSJm%0D%0AaWxsOiAjMDAwMDAwIiBwb2ludHM9IjEyNy44MzEsOTUuMTQ2IDExNy43Myw5OS45Mzg3IDEyMC4z%0D%0AMzMsOTQuOTkxMyAxMTcuOTM2LDg5Ljk0MDggIi8+CiAgICAgIDxwb2x5Z29uIHN0eWxlPSJmaWxs%0D%0AOiBub25lOyBmaWxsLW9wYWNpdHk6MDsgc3Ryb2tlLXdpZHRoOiAyOyBzdHJva2U6ICMwMDAwMDAi%0D%0AIHBvaW50cz0iMTI3LjgzMSw5NS4xNDYgMTE3LjczLDk5LjkzODcgMTIwLjMzMyw5NC45OTEzIDEx%0D%0ANy45MzYsODkuOTQwOCAiLz4KICAgIDwvZz4KICAgIDxnPgogICAgICA8bGluZSBzdHlsZT0iZmls%0D%0AbDogbm9uZTsgZmlsbC1vcGFjaXR5OjA7IHN0cm9rZS13aWR0aDogMjsgc3Ryb2tlOiAjMDAwMDAw%0D%0AIiB4MT0iODEuOTkzMiIgeTE9IjMwNS43NTIiIHgyPSIxOTcuMjA4IiB5Mj0iMTYzLjIiLz4KICAg%0D%0AICAgPHBvbHlnb24gc3R5bGU9ImZpbGw6ICMwMDAwMDAiIHBvaW50cz0iMjAxLjkyMiwxNTcuMzY3%0D%0AIDE5OS41MjUsMTY4LjI4NyAxOTcuMjA4LDE2My4yIDE5MS43NDgsMTYyLjAwMSAiLz4KICAgICAg%0D%0APHBvbHlnb24gc3R5bGU9ImZpbGw6IG5vbmU7IGZpbGwtb3BhY2l0eTowOyBzdHJva2Utd2lkdGg6%0D%0AIDI7IHN0cm9rZTogIzAwMDAwMCIgcG9pbnRzPSIyMDEuOTIyLDE1Ny4zNjcgMTk5LjUyNSwxNjgu%0D%0AMjg3IDE5Ny4yMDgsMTYzLjIgMTkxLjc0OCwxNjIuMDAxICIvPgogICAgPC9nPgogICAgPGc+CiAg%0D%0AICAgIDxsaW5lIHN0eWxlPSJmaWxsOiBub25lOyBmaWxsLW9wYWNpdHk6MDsgc3Ryb2tlLXdpZHRo%0D%0AOiAyOyBzdHJva2U6ICMwMDAwMDAiIHgxPSIxMjYuMDY1IiB5MT0iMTA3LjY2NyIgeDI9Ii04My41%0D%0AOTUyIiB5Mj0iMTA3LjY2NyIvPgogICAgICA8cG9seWdvbiBzdHlsZT0iZmlsbDogIzAwMDAwMCIg%0D%0AcG9pbnRzPSItOTEuMDk1MiwxMDcuNjY3IC04MS4wOTUyLDEwMi42NjcgLTgzLjU5NTIsMTA3LjY2%0D%0ANyAtODEuMDk1MiwxMTIuNjY3ICIvPgogICAgICA8cG9seWdvbiBzdHlsZT0iZmlsbDogbm9uZTsg%0D%0AZmlsbC1vcGFjaXR5OjA7IHN0cm9rZS13aWR0aDogMjsgc3Ryb2tlOiAjMDAwMDAwIiBwb2ludHM9%0D%0AIi05MS4wOTUyLDEwNy42NjcgLTgxLjA5NTIsMTAyLjY2NyAtODMuNTk1MiwxMDcuNjY3IC04MS4w%0D%0AOTUyLDExMi42NjcgIi8+CiAgICA8L2c+CiAgICA8dGV4dCBmb250LXNpemU9IjEyLjc5OTgiIHN0%0D%0AeWxlPSJmaWxsOiAjMDAwMDAwO3RleHQtYW5jaG9yOnN0YXJ0O2ZvbnQtZmFtaWx5OnNhbnMtc2Vy%0D%0AaWY7Zm9udC1zdHlsZTpub3JtYWw7Zm9udC13ZWlnaHQ6bm9ybWFsIiB4PSIxLjY2NjY3IiB5PSI2%0D%0AMy4zMzMzIj4KICAgICAgPHRzcGFuIHg9IjEuNjY2NjciIHk9IjYzLjMzMzMiPmZvcms8L3RzcGFu%0D%0APgogICAgPC90ZXh0PgogICAgPHRleHQgZm9udC1zaXplPSIxMi43OTk4IiBzdHlsZT0iZmlsbDog%0D%0AIzAwMDAwMDt0ZXh0LWFuY2hvcjpzdGFydDtmb250LWZhbWlseTpzYW5zLXNlcmlmO2ZvbnQtc3R5%0D%0AbGU6bm9ybWFsO2ZvbnQtd2VpZ2h0Om5vcm1hbCIgeD0iLTE0LjMzMzMiIHk9IjEzMi4zMzMiPgog%0D%0AICAgICA8dHNwYW4geD0iLTE0LjMzMzMiIHk9IjEzMi4zMzMiPnB1bGwgcmVxdWVzdDwvdHNwYW4+%0D%0ACiAgICA8L3RleHQ+CiAgICA8dGV4dCBmb250LXNpemU9IjEyLjc5OTgiIHN0eWxlPSJmaWxsOiAj%0D%0AMDAwMDAwO3RleHQtYW5jaG9yOnN0YXJ0O2ZvbnQtZmFtaWx5OnNhbnMtc2VyaWY7Zm9udC1zdHls%0D%0AZTpub3JtYWw7Zm9udC13ZWlnaHQ6bm9ybWFsIiB4PSI2Ny42NjY3IiB5PSIyMDIuMzMzIj4KICAg%0D%0AICAgPHRzcGFuIHg9IjY3LjY2NjciIHk9IjIwMi4zMzMiPmNsb25lPC90c3Bhbj4KICAgICAgPHRz%0D%0AcGFuIHg9IjY3LjY2NjciIHk9IjIxOC4zMzMiPmZldGNoPC90c3Bhbj4KICAgICAgPHRzcGFuIHg9%0D%0AIjY3LjY2NjciIHk9IjIzNC4zMzMiPnB1bGw8L3RzcGFuPgogICAgPC90ZXh0PgogICAgPHRleHQg%0D%0AZm9udC1zaXplPSIxMi43OTk4IiBzdHlsZT0iZmlsbDogIzAwMDAwMDt0ZXh0LWFuY2hvcjpzdGFy%0D%0AdDtmb250LWZhbWlseTpzYW5zLXNlcmlmO2ZvbnQtc3R5bGU6bm9ybWFsO2ZvbnQtd2VpZ2h0Om5v%0D%0Acm1hbCIgeD0iMTUzLjY2NyIgeT0iMjI3LjMzMyI+CiAgICAgIDx0c3BhbiB4PSIxNTMuNjY3IiB5%0D%0APSIyMjcuMzMzIi8+CiAgICA8L3RleHQ+CiAgICA8dGV4dCBmb250LXNpemU9IjEyLjc5OTgiIHN0%0D%0AeWxlPSJmaWxsOiAjMDAwMDAwO3RleHQtYW5jaG9yOnN0YXJ0O2ZvbnQtZmFtaWx5OnNhbnMtc2Vy%0D%0AaWY7Zm9udC1zdHlsZTpub3JtYWw7Zm9udC13ZWlnaHQ6bm9ybWFsIiB4PSIxNDguNjY3IiB5PSIy%0D%0ANDIuMzMzIj4KICAgICAgPHRzcGFuIHg9IjE0OC42NjciIHk9IjI0Mi4zMzMiPnB1c2g8L3RzcGFu%0D%0APgogICAgPC90ZXh0PgogICAgPHRleHQgZm9udC1zaXplPSIxMi43OTk4IiBzdHlsZT0iZmlsbDog%0D%0AIzAwMDAwMDt0ZXh0LWFuY2hvcjpzdGFydDtmb250LWZhbWlseTpzYW5zLXNlcmlmO2ZvbnQtc3R5%0D%0AbGU6bm9ybWFsO2ZvbnQtd2VpZ2h0Om5vcm1hbCIgeD0iLTEyNS4zMzMiIHk9IjIxMy4zMzMiPgog%0D%0AICAgICA8dHNwYW4geD0iLTEyNS4zMzMiIHk9IjIxMy4zMzMiPmZldGNoPC90c3Bhbj4KICAgICAg%0D%0APHRzcGFuIHg9Ii0xMjUuMzMzIiB5PSIyMjkuMzMzIj5wdWxsPC90c3Bhbj4KICAgIDwvdGV4dD4K%0D%0AICAgIDx0ZXh0IGZvbnQtc2l6ZT0iMTIuNzk5OCIgc3R5bGU9ImZpbGw6ICMwMDAwMDA7dGV4dC1h%0D%0AbmNob3I6c3RhcnQ7Zm9udC1mYW1pbHk6c2Fucy1zZXJpZjtmb250LXN0eWxlOm5vcm1hbDtmb250%0D%0ALXdlaWdodDpub3JtYWwiIHg9Ii0yMDguOTAxIiB5PSI5OC42NjciPgogICAgICA8dHNwYW4geD0i%0D%0ALTIwOC45MDEiIHk9Ijk4LjY2NyI+dXBzdHJlYW08L3RzcGFuPgogICAgICA8dHNwYW4geD0iLTIw%0D%0AOC45MDEiIHk9IjExNC42NjciPnJpdGpvZS9oZm9zczwvdHNwYW4+CiAgICA8L3RleHQ+CiAgICA8%0D%0AdGV4dCBmb250LXNpemU9IjEyLjc5OTgiIHN0eWxlPSJmaWxsOiAjMDAwMDAwO3RleHQtYW5jaG9y%0D%0AOnN0YXJ0O2ZvbnQtZmFtaWx5OnNhbnMtc2VyaWY7Zm9udC1zdHlsZTpub3JtYWw7Zm9udC13ZWln%0D%0AaHQ6bm9ybWFsIiB4PSIyMTguNjM0IiB5PSI5NS4xOTIxIj4KICAgICAgPHRzcGFuIHg9IjIxOC42%0D%0AMzQiIHk9Ijk1LjE5MjEiLz4KICAgIDwvdGV4dD4KICA8L2c+Cjwvc3ZnPgo=" width="70%">

### Log
in its simplest form, you can view a repository history using 

    git log
    
or see only the commits of a certain author by using

    git log --author=jonas
    
to look at more possible parameters use

    git log --help
    
### Replace local Changes
in case anything went wrong you can replace local changes using the command

    git checkout -- <filename>

that will replace the changes in your working tree with the last content in **Head**. Changes already added to the **Index** will be kept. 

if you instead want to drop all your local changes and commits, *fetch* the latest history from the server and point your local master branch at it with

    git fetch origin
    git reset --hard origin/master
    

   
    


