# Containerlab Networking Labs

Hands-on networking labs using Containerlab, Docker, and Linux to practice network configuration, troubleshooting, traffic analysis, and cybersecurity concepts.

## Lab index

| Lab | Focus | Status |
| --- | --- | --- |
| [01 — Two-Host Alpine Linux Network](lab-01-two-host-network/) | YAML troubleshooting, Linux interfaces, and ICMP verification | In Progress |

## Tools and approach

Containerlab deploys topologies defined in YAML. Docker runs the lab nodes, and Alpine Linux provides a lightweight environment for inspecting interfaces and testing connectivity. Packet capture with `tcpdump` will help verify where traffic actually flows.

Each numbered lab directory records the objective, environment, commands, troubleshooting, and observed results. Add the actual topology and sanitized evidence alongside each write-up as they become available. Future labs can build from host connectivity toward routing and traffic analysis in isolated networks.
