# LAB JOURNAL

## 09/08/2026

- [x] **Install Ubuntu Server 24.04**
  - Nodes: `ctrl01`, `comp01`
  - **Result:** Both nodes operational.

- [x] **Configure management network**
  - `ctrl01`: `192.168.1.101`
  - `comp01`: `192.168.1.102`
  - Gateway: `192.168.1.1`
  - Interface: `wlp3s0`
  - **Result:** Network connectivity between nodes working.

- [x] **Configure `/etc/hosts`**
  - **Result:** Hostname resolution working.

- [x] **Install base packages**
  - Chrony
  - OpenSSH Server
  - Docker
  - **Result:** Required services operational.

- [x] **Configure passwordless SSH**
  - Connection: `ctrl01 -> comp01`
  - **Result:** Passwordless SSH working.

- [x] **Initialize thesis repository**
  - Repository: `thesis`
  - **Result:** Local Git repository ready.

---

## 15/08/2026

- [x] **Install Kolla-Ansible**
  - Virtual environment: `/opt/kolla-venv`
  - **Result:** Kolla-Ansible environment ready.

- [x] **Configure Git SSH authentication**
  - **Result:** Git SSH access working.

- [x] **Create external veth pair**
  - `veth-ext-host`: `172.20.0.1/24`
  - `veth-ext-ovs`: no IPv4
  - **Result:** External veth pair operational.

- [x] **Configure IP forwarding and NAT**
  - Network: `172.20.0.0/24`
  - Outbound interface: `wlp3s0`
  - **Result:** External forwarding and NAT ready.

- [x] **Configure Kolla-Ansible multinode inventory**
  - `ctrl01`: Controller / Network Gateway
  - `comp01`: Compute
  - **Result:** Ansible connectivity verified.

- [x] **Configure Kolla networking**
  - VIP: `192.168.1.250`
  - Management interface: `wlp3s0`
  - External interface: `veth-ext-ovs`
  - Neutron plugin: `OVN`
  - Provider mapping: `physnet1 -> br-ex`
  - **Result:** Multinode configuration ready.

- [x] **Run Kolla bootstrap and prechecks**
  - **Result:** Prechecks completed with `0 failed`.

- [x] **Deploy OpenStack**
  - Pulled required container images.
  - Deployed using Kolla-Ansible.
  - Ran post-deploy.
  - **Result:** Multinode OpenStack deployment successful.

- [x] **Verify Open vSwitch / OVN**
  - `br-int`: `ctrl01`, `comp01`
  - `br-ex`: `ctrl01`
  - `veth-ext-ovs -> br-ex`
  - `physnet1 -> br-ex`
  - **Result:** OVS/OVN networking operational.

- [x] **Verify Geneve overlay**
  - `ctrl01`: `192.168.1.101`
  - `comp01`: `192.168.1.102`
  - **Result:** Geneve tunnel operational.

- [x] **Verify OVN Gateway Chassis**
  - Gateway node: `ctrl01`
  - **Result:** OVN external gateway operational.

- [x] **Install and configure OpenStack CLI**
  - Version: `10.2.1`
  - Cloud: `kolla-admin`
  - **Result:** Keystone authentication successful.

- [x] **Verify OpenStack services**
  - Keystone
  - Glance
  - Nova
  - Neutron
  - Placement
  - Heat
  - **Result:** OpenStack control plane operational.

- [x] **Verify Nova Compute and hypervisor**
  - Compute node: `comp01`
  - `nova-compute`: `enabled / up`
  - Hypervisor: `QEMU`
  - Host IP: `192.168.1.102`
  - **Result:** Compute node operational.

- [x] **Verify OVN agents**
  - OVN Controller
  - OVN Metadata
  - **Result:** OVN agents `UP`.

- [x] **Create external provider network**
  - Network: `external-net`
  - Type: `flat`
  - Physical network: `physnet1`
  - Subnet: `172.20.0.0/24`
  - Gateway: `172.20.0.1`
  - Floating IP pool: `172.20.0.100-172.20.0.200`
  - **Result:** External provider network `ACTIVE`.

- [x] **Create tenant private network**
  - Network: `private-net`
  - Subnet: `10.10.10.0/24`
  - Gateway: `10.10.10.1`
  - DHCP: Enabled
  - DNS: `8.8.8.8`
  - **Result:** Private network and subnet created successfully.

- [x] **Create OVN tenant router**
  - Router: `tenant-router`
  - Internal: `private-net` (`10.10.10.0/24`)
  - External: `external-net` (`172.20.0.0/24`)
  - External gateway IP: `172.20.0.114`
  - SNAT: Enabled
  - **Result:** Router `ACTIVE`; private and external networks connected successfully.

### Next
- [ ] Upload VM image and create flavor.
- [ ] Create SSH keypair and configure security group.
- [ ] Launch test VM on `comp01`.
- [ ] Allocate and associate Floating IP.
- [ ] Test VM ping, SSH, DNS, and Internet connectivity.
- [ ] Perform end-to-end OpenStack validation.
