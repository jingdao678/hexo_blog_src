---
title: 'git@github.com: Permission denied (publickey)'
date: 2018-12-08 15:15:06
tags:
---
#一次ubuntu下git不能提交hexo博客
root@linux:/home/ubuntu/new2018/blog# hexo d
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
INFO  Copying files from extend dirs...
On branch master
nothing to commit, working tree clean
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
FATAL Something's wrong. Maybe you can find the solution here: http://hexo.io/docs/troubleshooting.html
Error: git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

    at ChildProcess.<anonymous> (/home/ubuntu/new2018/blog/node_modules/hexo-util/lib/spawn.js:37:17)
    at ChildProcess.emit (events.js:182:13)
    at maybeClose (internal/child_process.js:962:16)
    at Process.ChildProcess._handle.onexit (internal/child_process.js:251:5)
root@linux:/home/ubuntu/new2018/blog# git config --global user.name "xx"
root@linux:/home/ubuntu/new2018/blog# git config --global user.name "xx"
root@linux:/home/ubuntu/new2018/blog# git config --global user.email "xx@qq.com"
root@linux:/home/ubuntu/new2018/blog# ssh-keygen -t rsa -C "xx@qq.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): 
/root/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:EvEGcdjX5B/pxWOL07tz+tLfgyrGWIOTba56Q6WFcOkY+I xx@qq.com
The key's randomart image is:
+---[RSA 2048]----+
|      ++.  o. .  |
|      .=. ...+ o |
|      . o.. = *oo|
|       o . o ++=o|
|      . S E  o+o |
|       .     *...|
|            @ .oo|
|           o =o*+|
|             oBO*|
+----[SHA256]-----+
root@linux:/home/ubuntu/new2018/blog#  cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAxxAABAQDTkTXF8hgh5IF95lw6zA8pdywfbkpERQoWq2FHnZ7OaGPdq6lU1riMMOWucVe2+EQyUJn3KxhQR7HjudXEdgV09ZhQUrt2skhDj0o+6mhfgUHkroAnMts8cmbd6ZDetyjEGfg+1whGgeqvmooTq9LSqe5Y4WrmFjPFzMXUvlM0kI5ooXlKeSn0mY6iSlJmZJFtOdXyNo1d4kZ4StRS+QylHVKmcmNvAzCOUqNHyRRmpKznW6FLrCAxfIEubpHeZrcOXaGnlZH6oXUF4tgahv4NZnEl4nqpnAFBJp9eX0w3BFgEgLZsUcN5zjvMUcCxVqKE9jEemsppUmWE39ydP9nKuna9 xx@qq.com
root@linux:/home/ubuntu/new2018/blog# ssh -T git@github.com
Hi jingdao678! You've successfully authenticated, but GitHub does not provide shell access.
root@linux:/home/ubuntu/new2018/blog# git remote -v
root@linux:/home/ubuntu/new2018/blog# hexo c
Usage: hexo <command>

Commands:
  clean     Remove generated files and cache.
  config    Get or set configurations.
  deploy    Deploy your website.
  generate  Generate static files.
  help      Get help on a command.
  init      Create a new Hexo folder.
  list      List the information of the site
  migrate   Migrate your site from other system to Hexo.
  new       Create a new post.
  publish   Moves a draft post from _drafts to _posts folder.
  render    Render files with renderer plugins.
  server    Start the server.
  version   Display version information.

Global Options:
  --config  Specify config file instead of using _config.yml
  --cwd     Specify the CWD
  --debug   Display all verbose messages in the terminal
  --draft   Display draft posts
  --safe    Disable all plugins and scripts
  --silent  Hide output on console

For more help, you can use 'hexo help [command]' for the detailed information
or you can check the docs: http://hexo.io/docs/
root@linux:/home/ubuntu/new2018/blog# hexo clean
INFO  Deleted database.
INFO  Deleted public folder.
root@linux:/home/ubuntu/new2018/blog# hexo g
INFO  Start processing
INFO  Files loaded in 235 ms
INFO  Generated: content.json
INFO  Generated: index.html
INFO  Generated: archives/index.html
INFO  Generated: fonts/default-skin.b257fa.svg
INFO  Generated: img/default-skin.png
INFO  Generated: fonts/iconfont.16acc2.ttf
INFO  Generated: fonts/tooltip.4004ff.svg
INFO  Generated: fonts/iconfont.8c627f.woff
INFO  Generated: fonts/iconfont.45d7ee.svg
INFO  Generated: img/preloader.gif
INFO  Generated: img/scrollbar_arrow.png
INFO  Generated: fonts/iconfont.b322fa.eot
INFO  Generated: archives/2018/11/index.html
INFO  Generated: archives/2018/12/index.html
INFO  Generated: archives/2018/index.html
INFO  Generated: assets/img/head.jpg
INFO  Generated: 2018/11/13/hexo-install/index.html
INFO  Generated: 2018/12/07/springcloud-docker-eclipse一些问题/index.html
INFO  Generated: 2018/11/13/hello-world/index.html
INFO  Generated: slider.e37972.js
INFO  Generated: main.0cf68a.css
INFO  Generated: main.0cf68a.js
INFO  Generated: mobile.992cbe.js
INFO  23 files generated in 278 ms
root@linux:/home/ubuntu/new2018/blog# hexo d
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
INFO  Copying files from extend dirs...
On branch master
nothing to commit, working tree clean
To github.com:jingdao678/jingdao678.github.io.git
 + 1c7cc18...973d321 HEAD -> master (forced update)
Branch 'master' set up to track remote branch 'master' from 'git@github.com:jingdao678/jingdao678.github.io.git'.
INFO  Deploy done: git
root@linux:/home/ubuntu/new2018/blog# 

