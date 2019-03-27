---
title: Default ports for website projects
description: The local ports used when running our applications locally
---

Each of [our website projects](https://github.com/canonical-websites/) is configured to run on a different port by default.
This port should be defined in a `.env` file within the project codebase, and
should be between 8001 and 8999, excluding more [commonly used ports](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers) like `8008`.

This is so that team members can easily run multiple projects at the same time without getting port conflicts.

## Defaults

| Port | Project                                                                                           |
| ---- | ------------------------------------------------------------------------------------------------- |
| 8001 | [www.ubuntu.com](https://github.com/canonical-websites/www.ubuntu.com)                            |
| 8002 | [www.canonical.com](https://github.com/canonical-websites/www.canonical.com)                      |
| 8003 | [partners.ubuntu.com](https://github.com/canonical-websites/partners.ubuntu.com)                  |
| 8004 | [snapcraft.io](https://github.com/canonical-websites/snapcraft.io)                                |
| 8005 | [conjure-up.io](https://github.com/canonical-websites/conjure-up.io)                              |
| 8006 | [maas.io](https://github.com/canonical-websites/maas.io)                                          |
| 8007 | [docs.ubuntu.com](https://github.com/canonical-websites/docs.ubuntu.com)                          |
| 8008 | RESERVED: [Alternative HTTP port](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers) |
| 8009 | [cloud-init.io](https://github.com/canonical-websites/cloud-init.io)                              |
| 8010 | [cn.ubuntu.com](https://github.com/canonical-websites/cn.ubuntu.com)                              |
| 8011 | [design.ubuntu.com](https://github.com/canonical-websites/design.ubuntu.com)                      |
| 8012 | [jp.ubuntu.com](https://github.com/canonical-websites/jp.ubuntu.com)                              |
| 8013 | [tour.ubuntu.com](https://github.com/canonical-websites/tour.ubuntu.com)                          |
| 8014 | [vanillaframework.io](https://github.com/canonical-websites/vanillaframework.io/)                 |
| 8015 | [developer.ubuntu.com](https://github.com/canonical-websites/developer.ubuntu.com/)               |
| 8016 | [tutorials.ubuntu.com](https://github.com/canonical-websites/tutorials.ubuntu.com/)               |
| 8017 | [assets.ubuntu.com](https://github.com/canonical-websites/assets.ubuntu.com/)                     |
| 8018 | [manager.assets.ubuntu.com](https://github.com/canonical-websites/manager.assets.ubuntu.com/)     |
| 8019 | [community.ubuntu.com](https://github.com/canonical-websites/community.ubuntu.com/)               |
| 8020 | [usn.ubuntu.com](https://github.com/canonical-websites/usn.ubuntu.com/)                           |
| 8021 | RESERVED: Possible use [by iTunes Radio streams](https://support.apple.com/en-za/HT202944)        |
| 8022 | [usn.ubuntu.com](https://launchpad.net/usn.ubuntu.com)                                            |
| 8023 | [insights.ubuntu.com](https://github.com/canonical-websites/insights.ubuntu.com/)                 |
| 8024 | [netplan.io](https://github.com/canonical-websites/netplan.io/)                                   |
| 8025 | [360](https://github.com/ubuntudesign/360/)                                                       |
| 8026 | [multipass.io](https://github.com/canonical-websites/multipass.io)                                |
| 8027 | [microk8s.io](https://github.com/canonical-websites/microk8s.io)                                  |
| 8028 | [mir-server.io](https://github.com/canonical-websites/mir-server.io)                              |
| 8029 | [jaas.ai](https://github.com/canonical-websites/jaas.ai)                                          |
| 8030 | [docs.snapcraft.io](https://github.com/canonical-websites/docs.snapcraft.io)                      |
| 8031 | [landscape.canonical.com](https://github.com/canonical-websites/landscape.canonical.com)          |
| 8032 | [juju-gui](https://github.com/juju/juju-gui)                                                      |
| 8099 | [demoservice](https://github.com/canonical-webteam/demoservice)                                   |
| 8101 | [vanilla-framework](https://github.com/vanilla-framework/vanilla-framework)                       |
| 8102 | [vanilla-framework-react](https://github.com/vanilla-framework/vanilla-framework-react)           |
| 8201 | [phone-docs](https://github.com/canonical-docs/phone-docs/)                                       |
| 8202 | [snappy-docs](https://github.com/canonical-docs/snappy-docs)                                      |
| 8203 | [maas-docs](https://github.com/canonicalltd/maas-docs)                                            |
| 8204 | [conjure-up-docs](https://github.com/canonical-docs/conjure-up-docs)                              |
| 8205 | [juju-docs](https://github.com/juju/docs)                                                         |
| 8206 | [security-certs-docs](https://github.com/CanonicalLtd/security-certs-docs)                        |
| 8207 | [ubuntu-core-docs](https://github.com/CanonicalLtd/ubuntu-core-docs)                              |

## Why use a fixed port

We could have chosen to solve the problem of port clashes by having the local development
tooling choose a random open port, instead of defining a specific one.

There are a few benefits to the local development application having a predictable port:

- Port clashes will remind developers that a specific project is already running locally
- Developers can reliably bookmark their locally running version of specific projects, and so quickly check if a project is currently running
- The port can reliably be mentioned in READMEs and pull request instructions
- Any inter-linking dependent services can work together more easily if they know which local ports to connect to

However, it should be possible to choose to run any project on a different port through the standard `./run` tooling:

```bash
./run serve --port 8999
```
