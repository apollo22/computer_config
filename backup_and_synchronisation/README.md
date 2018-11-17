# Backup
I have several types of backups:
  - full system
  - configuration
    - systems (per system)
    - profiles (per profile)
  - documents

All backups I do are incremental, but the frequency and conservation length of backups depends on the kind of backups.

  ## Full system
  Full system backups are backups of the full system. They are unversionned incremental backups.

  ## Configuration
  The configuration files are first version-controlled and then backed up incrementally in case someone overwrites some modifications.
  There are configuration files per system, per program and per profile.

  ## Documents
  Documents backup vary depending on the kind of files. Text files are version controlled.

# Backup Workflow
  - [TODO] Cron to backup
  - [TODO] On logout: backup

  ## Backup Strategy

    # On login
    - [TODO] Synchronise services (if not on metered connection or on anonymisation network)

  ### Periodically


  ### On logout

# Backup Infrastructure

- Github
