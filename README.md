# sensu-collator
Collates Sensu Checks

## Purpose
Allows you to view the results of sensu checks from many different sensu servers together in a concise format.
Can be run from the command line or as a cron job to then raise alerts.

## Alerting
sensu-collator can be used to raise alerts via alerting tools such as:
- pushover
- pushbullet
- pagerduty

## Screenshots

## Usage
Arguments are not a requirement to run the tool, by default sensu-collator will read the config from ~/sensu-collator/config.yml and display results

| Arg | Arg Long | Description | Example |
|:----|:-------------|:--------------|:------|
| -e | --environment | limit output to a specific environment | -e production |
| -d | --dontalert | don't raise alerts | --dontalert |
| -f | --config | use a different config file, default is ~/sensu-collator/config.yml | -f /etc/sensu-collator.yml |
| -a | --all | display all types of sensu alerts | --all |         
| -w | --warning | display only warning, critical and unknown sensu alerts | --warning |
| -c | --critical | display only critical and unknown alerts | --critical |
| -u | --unknown | dispay only unknown sensu alerts | -u |
| -p | --pretty | colorize and make the output pretty | --pretty |
|    | --csv | display output in csv format | --csv |

### Examples
Display critical (or worse) results from the production sensu server in csv format
```sensu-collator -e production --critical --csv```

## Configuration File


## Displaying Results
Sensu classifies alerts like so:
```
0  = ok
1  = warning
2  = critical
3+ = unknown
```
Sensu-collator displays results of the specified severity and worse.  Meaning if you use --warning you will be shown warning, critical and unknown results

## Cronjob Example
