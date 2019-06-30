# dream config for arch linux

## for graphipcs card nvidia

## for cpu intel

---

### nvidia

---

#### docker run nvidia setup

---

#### nvidia vync setup

---

### intel

---

#### microcode update

---

#### undervolt

* `systemctl list-units | egrep -i 'undervolt'`
  * 2 services added to system to make it work
    * UNIT | LOAD | ACTIVE | SUB | JOB DESCRIPTION |
        ---|---|---|---|---|
        undervolt.service | loaded | activating | start | start undervolt |
        undervolt.timer | loaded | active | running | Apply undervolt settings

* install log summery

    time | command
    ---|---|
    12 | pip install undervolt
    24 | undervolt -r
    28 | vim /etc/systemd/system/undervolt.service
    30 | systemctl start undervolt
    37 | vim /etc/systemd/system/undervolt.timer
    38 | systemctl enable undervolt.timer
    39 | systemctl start undervolt.timer

* first install undervolt via refer : `pip`
* then create a new service in
  * `vim /etc/systemd/system/undervolt.service`

        ```service
        [Unit]
        Description=undervolt

        [Service]
        Type=oneshot
        # If you have installed undervolt globally (via sudo pip install):
        # ExecStart=undervolt -v --core -150 --cache -150 --temp 97
        # If you want to run from source:
        ExecStart=/etc/under/undervolt.py -v --core -150 --cache -150 --temp 97
        ```
  * then start it  
  * `systemctl start undervolt`
* then create a new timer for it in
  * `vim /etc/systemd/system/undervolt.service`

        ```timer
        [Unit]
        Description=undervolt

        [Service]
        Type=oneshot
        # If you have installed undervolt globally (via sudo pip install):
        # ExecStart=undervolt -v --core -150 --cache -150 --temp 97
        # If you want to run from source:
        ExecStart=/etc/under/undervolt.py -v --core -150 --cache -150 --temp 97
        ```
  * eanble it
    * `systemctl enable undervolt.timer`
  * start it
    * `systemctl start undervolt.timer`
* read values under root
  * `undervolt -r`

---
