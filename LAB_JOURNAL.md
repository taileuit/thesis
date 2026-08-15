9/8/2026:
- Install Ubuntu Server 24.04
- Config Network:
  + Manaul IP Config by yaml and edit hosts
  + Install chrony, openssh-server, docker
  + [Only Ctrl01] Create SSH key and copy from ctrl01 to comp01
- Create Local Repo (thesis) and git init
15/8/2026:
- [Only Ctrl01] Insall Kolla Ansible:
  + Instal python3-dev libffi-dev gcc libssl-dev python3-venv
  + Create VirtualEnv /opt/kolla/venv
  + Grant "tai" account to own /opt/kolla/venv (sudo chown -R tai:tai /opt/kolla-venv)
  + Install pip
- Establish SSH from local to GIT (instead of use https)
- Multinode Configuration


