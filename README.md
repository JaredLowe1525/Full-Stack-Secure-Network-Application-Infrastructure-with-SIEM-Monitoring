# Full-Stack-Secure-Network-Application-Infrastructure-with-SIEM-Monitoring


By Jared Lowe – Senior IT / Cybersecurity Capstone

This project represents the culmination of my senior-level IT and cybersecurity experience, bringing together system administration, network engineering, security architecture, monitoring, and offensive/defensive operations in a fully functional, multi-network virtual lab. Over the course of the semester, I built a complete enterprise-style environment from the ground up—featuring segmented networks, hardened systems, a live Ruby on Rails application, a PostgreSQL database backend, DNS filtering, and an operational SIEM powered by Elasticsearch, Logstash, and Kibana.

The final environment not only works as a secure and production-like infrastructure, but also provides a realistic platform for threat detection, log analysis, and controlled penetration testing. This project strengthened my ability to design, implement, break, defend, and document a complex IT system—skills directly applicable to real-world IT, SOC, and cybersecurity engineering roles.

Project Overview

The lab was built using VMware Workstation with multiple virtual networks (WAN, LAN, DMZ, and custom segments). pfSense served as the central firewall and routing layer, enforcing segmentation, NAT policies, DNS rules, and traffic filtering. On the internal networks, I deployed Ubuntu servers, Windows clients, a Pi-hole DNS filtering system, a Rails application server, and a PostgreSQL backend configured for remote logging and authentication monitoring.

To mimic enterprise SOC workflows, all systems shipped logs into a centralized Elastic SIEM. Filebeat and Winlogbeat were used to forward logs to Elasticsearch, where they were indexed, analyzed, and visualized through Kibana dashboards. This allowed me to track authentication events, system behavior, DNS filtering patterns, enumeration activity, and potential attack indicators in real time.

Offensive Testing & Security Analysis

Once the environment was fully configured, I performed structured penetration tests to evaluate detection capability and identify defensive improvements. Tools such as Nmap, Hydra, ffuf, enum4linux, dig, and custom scripts were used to test the environment’s resilience.

These controlled attacks revealed several critical insights:

Enumeration tools create distinct, easily recognizable log spikes, reinforcing the importance of SIEM monitoring and baseline traffic analysis.

Authentication attacks against PostgreSQL and Rails created immediate alerts, demonstrating correct log ingestion and rule configuration.

DNS flood attempts were trackable through Pi-hole logs, proving the value of DNS filtering in identifying malware-like behaviors.

SMB scans and port sweeps were captured by Filebeat agents, highlighting opportunities for further segmentation and intrusion detection.

Each attack reinforced how attackers leave patterns—and how defenders must learn to interpret them.

Defensive Improvements & Architecture Hardening

The findings from the offensive testing guided a series of recommendations for improving system resilience. These included:

Strengthening pfSense firewall rules with deny-by-default segmentation.

Implementing VLAN-based isolation for users, servers, and administrative systems.

Enforcing SSH key authentication and disabling password logins on Linux servers.

Adding Fail2Ban, Suricata IDS/IPS, and stricter syslog auditing.

Hardening Windows systems with Sysmon, SMBv1 removal, and RDP authentication requirements.

Restricting PostgreSQL to accept only encrypted connections from the Rails application.

Developing enhanced SIEM dashboards with automated alerting triggers for abnormal behavior.

These defenses reflect real-world cybersecurity principles: assume breach, minimize attack surface, and maximize detection.

Lessons Learned

This project was a deep dive into how real IT ecosystems operate. I learned how every component—networking, systems, applications, and security—interacts with the others. Even small misconfigurations, such as interface errors in pfSense or incorrect routing, had large cascading effects. Troubleshooting these issues taught me patience, attention to detail, and the value of thorough documentation.

Most importantly, the SIEM portion of the project demonstrated that visibility is everything. Once logs were centralized, attacker behavior became obvious. This reinforced what SOC analysts rely on: knowing what “normal” looks like so they can immediately spot “abnormal.”

Conclusion

Building this environment from scratch gave me real hands-on experience with modern enterprise infrastructure, offensive security techniques, and defensive engineering practices. The combination of Rails development, database management, network segmentation, DNS filtering, and SIEM integration provided a complete view of how organizations design and protect critical systems.

This project strengthened my confidence as an IT professional and gave me practical skills that translate directly into cybersecurity analyst, network administrator, and system engineering roles. It also built a foundation for future projects—such as expanding my SIEM, experimenting with IDS/IPS, or automating detection workflows.
