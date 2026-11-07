# Lab 01 — Two-Host Alpine Linux Network

**Date:** November 7, 2026  
**Status:** In Progress

## Objective

Deploy two Alpine Linux hosts, inspect their interfaces, and verify connectivity over a dedicated lab link separately from management network reachability.

## Environment

Ubuntu Server with Docker and Containerlab, using Alpine Linux containers named `host1` and `host2`. The topology used in the session was named `lab.clab.yaml`. The actual YAML is needed to reproduce the deployment.

## Commands recorded during the session

From the Ubuntu Server shell:

```sh
sudo containerlab deploy -t lab.clab.yaml
sudo docker exec -it clab-working-lab-host1 sh
```

From `host1`, the session pinged `172.20.20.2`. The destination was recorded. The exact flags, if any, were not recorded.

## Troubleshooting

The initial deployment encountered YAML syntax and link endpoint-format errors. The session corrected the YAML and the link endpoint format (`node:interface)), then deployed the topology successfully.

## Observations and results

| Check | Observation |
| --- | --- |
| Deployment | Both Alpine containers reached Running state. |
| Shell access | Opened an interactive shell on `host1` using `docker exec`. |
| ICMP | The ping to `172.20.20.2` received seven replies with 0% packet loss. |
| `host1` `eth0` | Observed IPv4 address `172.20.20.3/24`, consistent with the management network. |
| `host1` `eth1` | Observed an IPv6 link-local address and no configured IPv4 address. |

The successful ping establishes reachability to `172.20.20.2`. It likely used the management network via `eth0`. The egress interface, destination identity, and connectivity over the dedicated `eth1` link still need verification.

## Next week

- [ ] Verify that the dedicated link connects `host1` and `host2` and inspect both endpoints.
- [ ] Configure IPv4 addresses on both `eth1` interfaces using a subnet separate from management.
- [ ] Test ICMP to the peer's dedicated IPv4 address and verify the egress interface.
- [ ] Capture and analyze traffic on `eth1` with `tcpdump` during the ICMP test.
- [ ] Add the actual Containerlab YAML topology used for the lab.
- [ ] Complete the write-up with verified commands, observations, and results.
