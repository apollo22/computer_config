# Job scheduling

I use systemd timers for job scheduling for the following reasons:
  - They are better integrated in the systemd confiugration (use of systemctl)
    - Enable / Disable
    - Execute service anytime
  - Dependency is easier (dependency to other services)
  - Logs are integrated (journald)
