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
- [Only Ctrl01] Establish SSH from local to GIT (instead of use https)
- [Only Ctrl01] Create Veth Internal by service
- Network Topology:
- Home Wi-Fi
               192.168.1.0/24
                      |
           +----------+----------+
           |                     |
        ctrl01                 comp01
   192.168.1.101          192.168.1.102
       wlp3s0                 wlp3s0
           |                     |
           +------ GENEVE -------+
                 UDP 6081

        ctrl01 / Network Node
                 |
        veth-ext-host
          172.20.0.1
                 |
            veth pair
                 |
         veth-ext-ovs
            no IPv4
                 |
              br-ex
                 |
        External Network
         172.20.0.0/24
                 |
           Tenant Router
                 |
          Tenant Network
                 |
                VM
- Multinode Configuration:
  + Check etc/kolla and copy template inventory multinode
  + Edit Inventory Multinode
  + Select Kolla VIP 192.168.1.250
  + Configure Global.yaml
  + Generate Password
  + Install Ansible dependencies
  + Run Kolla bootstrap
  + Run Prechecks
  + kolla-ansible pull


