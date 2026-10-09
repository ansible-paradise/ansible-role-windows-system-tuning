# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-10-09

### Added
- Initial release of `windows_system_tuning` role for Ansible Paradise.
- Support for disabling Windows Defender Antivirus, Real-Time Protection and MAPS/Spynet reporting.
- Support for disabling Windows Firewall across Domain, Private and Public profiles.
- Support for stopping and disabling resource-hungry background services (`WSearch`, `SysMain`, `DiagTrack`, `WerSvc`, `dmwappushservice`, `DoSvc`, `MapsBroker`).
- Support for preventing automatic Windows Update reboots while users are logged on (`NoAutoRebootWithLoggedOnUsers = 1`, `NoAutoUpdate = 1`).
- Support for disabling hibernation (`powercfg /h off`) to free disk space and prevent sleep latency.
- Support for disabling Customer Experience Improvement Program (CEIP) and telemetry scheduled tasks.
