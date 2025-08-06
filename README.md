# Liquibase Checks Disable Action

⚠️ **VERSION SUPPORT NOTICE**: This action will continue to be supported for Liquibase 4.x. Starting with Liquibase 5.x, it will no longer be supported. 

**Migration to [`liquibase/setup-liquibase`](https://github.com/liquibase/setup-liquibase)**: Available for Liquibase versions 4.32.0 and above. If you're using an older version, upgrade your Liquibase version first.

## Migration Guide

### Current Approach (Liquibase 4.x)
```yaml
- uses: liquibase-github-actions/checks-disable@v4.33.0
  with:
    # your parameters here
```

### Recommended Approach (Liquibase 4.32.0+)
```yaml
- uses: liquibase/setup-liquibase@v1
  with:
    version: '4.33.0'  # Requires 4.32.0 or higher
    edition: 'oss'
- run: liquibase checks-disable # add your parameters as CLI flags
```

### Migration Steps
1. **Check your Liquibase version**: Ensure you're using 4.32.0 or higher
2. **If using older version**: Update to 4.32.0+ first using the current micro actions
3. **Then migrate**: Switch to setup-liquibase action

---

Official GitHub Action to run Liquibase Checks Disable in your GitHub Action Workflow. For more information on how checks disable works visit the [Official Liquibase Documentation](https://docs.liquibase.com/commands/home.html).
## Checks Disable
Disable an enabled check for current configuration
## Usage
```yaml
steps:
- uses: actions/checkout@v3
- uses: liquibase-github-actions/checks-disable@v4.33.0
  with:
    # Comma separated list of names of checks to disable
    # string
    # Required
    checkName: ""

    # Automatically enable new policy checks in liquibase.checks.conf file when they are available. Options: [true|false]
    # bool
    # Optional
    autoEnableNewChecks: ""

    # Allows automatic backup and updating of liquibase.checks.conf file when new policy checks are available, or for file format changes. Options: [on|off]
    # bool
    # Optional
    autoUpdate: ""

    # Relative or fully qualified path to a configuration file for checks execution
    # string
    # Optional
    checksSettingsFile: ""

```

### Secrets
It is a good practice to protect your database credentials with [GitHub Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets)

## Optional Liquibase Global Inputs
The liquibase checks disable action accepts all valid liquibase global options as optional parameters. A full list is available in the official [Liquibase Documentation](https://docs.liquibase.com/parameters/command-parameters.html).

### Example
```yaml
steps:
  - uses: actions/checkout@v3
  - uses: liquibase-github-actions/checks-disable@v4.33.0
    with:
      checkName: ""
      headless: true
      licenseKey: ${{ secrets.LIQUIBASE_LICENSE_KEY }}
      logLevel: INFO
```

## Feedback and Issues
This action is automatically generated. Please submit all feedback and issues with the [generator repository](https://github.com/liquibase/github-action-generator/issues).
