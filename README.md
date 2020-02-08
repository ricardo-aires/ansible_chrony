# chrony Setup

Role that setup the [chrony](https://chrony.tuxfamily.org) service using the security guidelines established by the [CIS Benchmark for RHEL 7](http://cisecurity.org) over the **2.2.1 Time Synchronization** section.

## Requirements

This role was created using [Ansible 2.9](https://docs.ansible.com/ansible/2.9/) for macOS and tested using the [centos/7](https://app.vagrantup.com/centos/boxes/7) boxes for [Vagrant v.2.2.6](https://www.vagrantup.com/docs/index.html) with [VirtualBox](https://www.virtualbox.org/) as a Provider.

The [Ansible modules](https://docs.ansible.com/ansible/2.9/modules/modules_by_category.html) used in the role are:

- [yum](https://docs.ansible.com/ansible/2.9/modules/yum_module.html#yum-module) - requires Python 2 and `yum` (for Python 3 see [dnf](https://docs.ansible.com/ansible/2.9/modules/dnf_module.html#dnf-module));
- [template](https://docs.ansible.com/ansible/2.9/modules/template_module.html#template-module)
- [copy](https://docs.ansible.com/ansible/2.9/modules/copy_module.html#copy-module)
- [service](https://docs.ansible.com/ansible/2.9/modules/service_module.html#service-module)

## Role Variables

The only variable to be used is a list named `chrony_ntp_servers` that should hold the pool to be used. By default the next public ones are set:

```yaml
chrony_ntp_servers:
  - 0.centos.pool.ntp.org
  - 1.centos.pool.ntp.org
  - 2.centos.pool.ntp.org
  - 3.centos.pool.ntp.org
```

> The list should be replaced by the ones of the organisation/environment and the `chrony.conf` template tweak to match requirements.

## Dependencies

This role doesn't have any dependencies.

## Example Playbook

A working example using Vagrant and Virtual Box is setup under [tests](./tests/).
