## How to fix “chown: invalid group:” if the user does not exist on the running system?

* I want to fix permissions on another disk with chown. Set the permissions to a user which does not exist on the system which is currently running.

* Use the numerical UID/GID instead of the user/group name.
    * You can find the UID/GID on the system the disk belongs to by using
* `id some_username`
* `ls -ln some_file`
    * where some_file is a file that belongs to user you are looking for

* so basiccly ;
    * `sudo chown -R $USER:$USER .` does not WORK.
    * `sudo chown -R 1001:1001 .` doest work