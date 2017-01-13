
[![BuildStatus](https://travis-ci.org/indix/ansible-postfix.svg?branch=master)](https://travis-ci.org/indix/ansible-postfix)


For postfix role having gather_facts is mandatory since there are few configs which rely on ansible_fqdn.


#### Examples

A simple example that doesn't use SASL relaying:
```yaml
---
- hosts: all
  roles:
    - postfix
  vars:
    postfix_aliases:
    - { user: root, alias: you@yourdomain.org }
```

Provide the relay host name if you want to enable relaying:
```yaml
---
- hosts: all
  roles:
    - postfix
  vars:
    postfix_aliases:
    - { user: root, alias: you@yourdomain.org }
    postfix_relayhost: mail.yourdomain.org
```

For AWS SES support:
```yaml
---
- hosts: all
  roles:
    - postfix
  vars:
    postfix_aliases:
    - { user: root, alias: sesverified@yourdomain.org }
    postfix_relayhost: email-smtp.us-east-1.amazonaws.com
    postfix_relaytls: true
    # AWS IAM SES credentials (not access key):
    postfix_sasl_user: AKIXXXXXXXXXXXXXXXXX
    postfix_sasl_password: ASDFXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```
