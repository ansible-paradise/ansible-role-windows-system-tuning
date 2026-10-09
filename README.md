# ansible-role-windows-system-tuning

[![CI](https://github.com/ansible-paradise/ansible-role-windows-system-tuning/actions/workflows/ci.yml/badge.svg)](https://github.com/ansible-paradise/ansible-role-windows-system-tuning/actions)

Ansible role to disable Windows Defender, Windows Firewall, telemetry, and resource-heavy background services on Windows virtual machines (KVM/Proxmox, Hyper-V) and dedicated trading hosts.

Designed specifically for low-latency workloads such as MetaTrader 4 / MetaTrader 5, eliminating disk I/O freezes caused by antivirus scanning, random reboots from Windows Update, and CPU starvation from background indexing.

## Requirements

- Windows Target: Windows 10, Windows 11, Windows Server 2016, 2019, 2022, 2025
- Ansible >= 2.15
- Collection: `ansible.windows` >= 2.0.0

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `windows_system_tuning_enabled` | `true` | Master toggle for the role |
| `windows_system_tuning_disable_defender` | `true` | Disables Windows Defender Antivirus, Real-Time Monitoring, and Cloud reporting |
| `windows_system_tuning_disable_firewall` | `true` | Disables Windows Firewall on Domain, Private, and Public profiles |
| `windows_system_tuning_disable_services` | `true` | Stops and disables resource-heavy background services |
| `windows_system_tuning_services_to_disable` | `[...]` | List of services to disable (`WSearch`, `SysMain`, `DiagTrack`, `WerSvc`, etc.) |
| `windows_system_tuning_prevent_auto_reboots` | `true` | Configures Windows Update policies to prevent forced reboots with active users |
| `windows_system_tuning_disable_hibernation` | `true` | Runs `powercfg /h off` to reclaim disk space and prevent sleep latency |
| `windows_system_tuning_disable_telemetry_tasks` | `true` | Disables Customer Experience (CEIP) and telemetry scheduled tasks |
| `windows_system_tuning_telemetry_tasks` | `[...]` | List of scheduled task paths to disable |

## Example Playbook

```yaml
---
- name: Tune Windows Trading Hosts
  hosts: windows_vms
  roles:
    - role: ansible-paradise.windows_system_tuning
    - role: ansible-paradise.windows_rdp_performance
```

Or install via Git in `requirements.yml`:

```yaml
---
roles:
  - name: ansible-paradise.windows_system_tuning
    src: git+https://github.com/ansible-paradise/ansible-role-windows-system-tuning.git
    version: main
```

## License

[MIT](LICENSE)

## Author

Maintained by [ansible-paradise](https://github.com/ansible-paradise).
