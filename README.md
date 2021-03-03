# Application monitoring with New Relic

[New Relic](http://newrelic.com/) is an application performance monitoring tool (amongst other things).

**To use with ArchivesSpace you must:**

- Signup for an account at newrelic (there is a free tier and paid plans)
- Edit `config.rb` to:
  - activate the `newrelic` plugin
  - add the New Relic license key
  - add an application name to identify the ArchivesSpace instance in the New Relic dashboard

For example, in config.rb:

```ruby
## You may have other plugins
AppConfig[:plugins] = ['local', 'newrelic']

AppConfig[:newrelic_key] = "enteryourkeyhere"
AppConfig[:newrelic_app_name] = "ArchivesSpace"
```

- Install the New Relic agent library by initializing the plugin:

```bash
## For Linux/OSX
$ scripts/initialize-plugin.sh newrelic

## For Windows
% scripts\initialize-plugin.bat newrelic
```

- Start, or restart ArchivesSpace to pick up the configuration.

Within a few minutes the application should be visible in the New Relic dashboard with data being collected.

For advanced configuration the New Relic agent can be configured very conveniently using
[environment variables](https://docs.newrelic.com/docs/agents/ruby-agent/configuration/ruby-agent-configuration).

For example:

- `NEW_RELIC_BROWSER_MONITORING_AUTO_INSTRUMENT=true`
- `NEW_RELIC_LOG_LEVEL=debug`

This allows you to configure the agent without having to directly modify `newrelic.yml`.
