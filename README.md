# ansible-101
A development-only test ansible repo that installs pyenv on 16.04.5 Ubuntu remote DigitalOcean VM. The Ubuntu remote box is configured with SSH via the DigitalOcean dashboard with public keys from Susan's work mac laptop. This ansible playbook is intended for Susan's learning and development only.

## Usage

Log in directly with

```
ssh root@104.248.68.192
```

This should print a "Hello World" to terminal on both the remote Ubuntu box and on localhost:

`ansible-playbook hello.yml`

```
PLAY [all] *****************************************************************************************

TASK [Gathering Facts] *****************************************************************************
ok: [104.248.68.192]
ok: [127.0.0.1]

TASK [debug] ***************************************************************************************
ok: [104.248.68.192] => {
    "msg": "Hello World!"
}
ok: [127.0.0.1] => {
    "msg": "Hello World!"
}

PLAY RECAP *****************************************************************************************
104.248.68.192             : ok=2    changed=0    unreachable=0    failed=0
127.0.0.1                  : ok=2    changed=0    unreachable=0    failed=0
```

You can selectively TEST run parts of the .yml with `--tags`:

`ansible-playbook webservers.yml --check --tags pyenv_use_2_7_9`

You can selectively TEST run parts of the .yml with `--tags` with the most verbose output:

`ansible-playbook -vvv webservers.yml --check --tags pyenv_use_2_7_9`

You can selectively run parts of the .yml for real:

`ansible-playbook webservers.yml --tags pyenv_use_2_7_9`

The output of the last command is

```
PLAY [webservers] **********************************************************************************

TASK [Gathering Facts] *****************************************************************************
ok: [104.248.68.192]

TASK [Use python 2.7.9 globally in every new virtualenv.] ******************************************
changed: [104.248.68.192]

PLAY RECAP *****************************************************************************************
104.248.68.192             : ok=2    changed=1    unreachable=0    failed=0
```
