# Changelog

## [2.0.0] - 2024-04-28

### Added

- Add Zookeeper SSL and Zookeeper Quorum SSL support.
- `zookeeper_admin_rate_limiter_interval_in_ms`, `zookeeper_admin_snapshot_enabled`, `zookeeper_admin_restore_enabled` and `zookeeper_admin_need_client_auth` arguments added.

### Changed

- Default Zookeeper version bump to `3.8.4`
- **Breaking:** The name of the systemd unit has been changed from `zookeeper-server` to `zookeeper`.
- **Breaking:** The `zookeeper_service_restart_on_config_change` argument name has been changed to `zookeeper_service_restart_on_change` and its default value is now `false`.
- **Breaking:** The `zookeeper_leader_port` argument has been renamed to `zookeeper_quorum_port`.
- **Breaking:** The `zookeeper_election_port` argument has been renamed to `zookeeper_leader_election_port`.

### Removed

- **Breaking:** Drop RedHat 7 platform compatibility.

## [1.0.1] - 2022-10-28

### Fixed

- Install the `procps-ng` package required by `zkServer.sh`.

## [1.0.0] - 2022-01-20

Initial release.

[1.0.0]: https://github.com/dborisov/ansible-role-zookeeper/releases/tag/1.0.0
[1.0.1]: https://github.com/dborisov/ansible-role-zookeeper/releases/tag/1.0.1
[2.0.0]: https://github.com/dborisov/ansible-role-zookeeper/releases/tag/2.0.0
