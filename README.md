# ansible-lint-minimal
Minimal reproduction
```console
docker run --rm -it docker.io/library/python:3.11-slim-bullseye bash
```

Inside the contain run:

```console
apt update && apt install -y git
pip install pre-commit
git clone https://github.com/gone-for-coding/ansible-lint-minimal.git && cd ansible-lint-minimal
pre-commit run ansible-lint -a -v
```

Which fails

```console
Receiving objects: 100% (5/5), done.
[INFO] Initializing environment for https://github.com/ansible/ansible-lint.
[INFO] Initializing environment for https://github.com/ansible/ansible-lint:.,ansible-core>=2.13.3.
[INFO] Installing environment for https://github.com/ansible/ansible-lint.
[INFO] Once installed this environment will be reused.
[INFO] This may take a few minutes...
Ansible-lint.............................................................Failed
- hook id: ansible-lint
- duration: 5.38s
- exit code: 2

INFO     Identified /ansible-lint-minimal as project root due .git directory.
INFO     Running ansible-galaxy collection install -v -r requirements.yml
INFO     Set ANSIBLE_LIBRARY=/root/.cache/ansible-compat/214250/modules:/root/.ansible/plugins/modules:/usr/share/ansible/plugins/modules
INFO     Set ANSIBLE_ROLES_PATH=/root/.cache/ansible-compat/214250/roles:/root/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles
INFO     Discovered files to lint using: git -c safe.directory=/ansible-lint-minimal ls-files --cached --others --exclude-standard -z
INFO     Excluded removed files using: git -c safe.directory=/ansible-lint-minimal ls-files --deleted -z
INFO     Executing syntax check on playbook playbook_win.yml (0.41s)
WARNING  Listing 1 violation(s) that are fatal
syntax-check[specific]: couldn't resolve module/action 'ansible.windows.win_regedit'. This often indicates a misspelling, missing collection, or incorrect module path.
playbook_win.yml:8:7


                  Rule Violation Summary
 count tag                    profile rule associated tags
     1 syntax-check[specific] min     core, unskippable

Failed after : 1 failure(s), 0 warning(s) on 3 files.
```
