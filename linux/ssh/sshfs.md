# Mount a remote file system by sshfs tool
## Introduce
SSH is a very powerful thing. You could resolve a lot of issues by the SSH.  I trying show how to mount a remote file system to your workstation or server. 
Sometimes we faced with a situation when we want to edit remote files of puppet or website. 
Often a remote server has not necessary tools like Geppetto or sublime.  I know only several IDE that could connect to a remote server and works with a file system of the server. In my case it is not available therefore I use sshfs tool.
## How to mount from a console
1.Create directory where will be a remote file system.
```bash
mkdir /home/alexander/puppet
```
2.Put the line user_allow_other to fuse.conf
```bash
echo 'user_allow_other'>>/etc/fuse.conf
```
3.Run sshfs with appropriate arguments
```bash
sshfs -o allow_other puppet:/etc/puppet labs/code/environments/alexander /home/alexander/puppet
```
