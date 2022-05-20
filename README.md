# ansible-logstash-pipeline
Logstash pipeline for processing Ansible logs

[![CI](https://github.com/netways/ansible-logstash-pipeline/workflows/Logstash%20Syntax/badge.svg?event=push)](https://github.com/netways/ansible-logstash-pipeline/actions?query=workflow%3A%22Logstash+Syntax%22)

Minimalist pipeline to parse Ansible logs on managed hosts

Note, that Ansible uses it's module as part of the process name. So make the condition to route into this pipeline a regex check: `[process][name] =~ "ansible"`.

## Inputs and Outputs ##

If you use files called `input.conf` and `output.conf` they will not collide with this rules, even when you want to pull new versions.

### Examples ###

Here's an example for an `input.conf`

```
input {
  redis {
    host => "localhost"
    data_type => "list"
    key => "netways-ansible-input"
  }
}
```

and one for `output.conf`.

```
output {
  redis {
    host => "localhost"
    data_type => "list"
    key => "netways-ansible-output"
  }
}
```
