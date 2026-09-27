## Graylog Client Configuration

---

## Objective
Configure **dev-app**, **stage-web**, and **dev-performance** servers to forward system logs to the central Graylog server. This task strengthens monitoring and logging expertise by enabling centralized log aggregation.

---

## Summary
Opened the required UDP port for Graylog, created a dedicated rsyslog configuration file on each server, restarted rsyslog, and verified successful log ingestion through the Graylog web interface. All three servers were confirmed to be sending logs to Graylog.

---

## Completed Tasks

### 1. Configure Graylog Client on dev-app

#### Logged Into dev-app

- ssh mrice@10.X.XX.172 
- hostname 
- whoami

<p>
<img src="https://github.com/user-attachments/assets/c863712d-e54c-4e5e-9156-75e008ac00a9" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/faded05c-9c2a-4df2-b42f-bd893b3e60c6" width="150"/>
<p>

#### Opened Firewall Port for Graylog

- sudo firewall-cmd --zone=public --add-port=5140/udp --permanent 
- sudo firewall-cmd --reload 
- sudo firewall-cmd --list-ports

<p>
<img src="https://github.com/user-attachments/assets/56c0acc2-feea-4cf4-96fc-8bed8930d58e" width="275"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/b5f1a71a-46b7-41c5-8db1-ec941e03fa50" width="225"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/725e0582-9d85-469c-9a3e-5ff22b8a8003" width="225"/>
<p>

#### Created Graylog rsyslog Configuration

- sudo vi /etc/rsyslog.d/90-graylog.conf

<img src="https://github.com/user-attachments/assets/27b9b4ad-679b-4b33-81e1-7aaafef7808e" width="275"/>

### Added:

- ** @10.X.XX.51:5140;RSYSLOG_SyslogProtocol23Format

<img src="https://github.com/user-attachments/assets/6ec6d051-6ed0-4dbb-af47-1b01c7835b93" width="250"/>

- :wq


#### Restarted rsyslog

- sudo systemctl restart rsyslog

<img src="https://github.com/user-attachments/assets/8adf7df6-2e4d-4fee-8ebc-0fe9eba56341" width="275"/>

#### Verified Logs in Graylog

- Logged into Graylog web UI:

<img src="https://github.com/user-attachments/assets/2364b141-d246-4a71-83b4-b950e959f26d" width="200"/>

***Confirmed logs from **dev-app** were visible.***

<img src="https://github.com/user-attachments/assets/ac923f20-741b-40c0-8438-2e6fcbd44974" width="300"/>

---


## 2. Configure Graylog Client on stage-web

#### Logged Into stage-web

- ssh mrice@<stage-web-IP> 
- hostname 
- whoami

<p>
<img src="https://github.com/user-attachments/assets/11821492-0402-47d6-a59b-724128a513a8" width="275"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/3e9072cf-f633-43b1-b221-130028fe087a" width="125"/>
<p>

#### Opened Firewall Port

- sudo firewall-cmd --zone=public --add-port=5140/udp --permanent 
- sudo firewall-cmd --reload 
- sudo firewall-cmd --list-ports

<p>
<img src="https://github.com/user-attachments/assets/8d426e55-8403-4abc-bb36-fd21ef93adbc" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/84faa092-dc3d-4bcd-af9c-af80e42605e8" width="200"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/775298ee-cd9a-46d1-b282-fd655811ea7d" width="200"/>
<p>

#### Created Graylog rsyslog Configuration

- sudo vi /etc/rsyslog.d/90-graylog.conf

<img src="https://github.com/user-attachments/assets/87141375-5c80-4298-b197-370ef50c5adf" width="300"/>

#### Added:

- ** @10.X.XX.51:5140;RSYSLOG_SyslogProtocol23Format

<img src="https://github.com/user-attachments/assets/47c8a8b2-5920-4a96-925f-c65ce48226e7" width="225"/>

#### Restarted rsyslog:

- sudo systemctl restart rsyslog

<img src="https://github.com/user-attachments/assets/f9f2f2fb-08d3-4d1a-bbd5-3a7f2bc5e136" width="250"/>

#### Verified Logs in Graylog

***Logs from **stage-web** were visible in Graylog.***

<img src="https://github.com/user-attachments/assets/5ac77d4f-98c9-4b36-b687-af78c2b17552" width="300"/>

---

## 3. Configure Graylog Client on dev-performance

#### Logged Into dev-performance

- ssh mrice@<dev-performance-IP> 
- hostname 
- whoami


#### Opened Firewall Port

- sudo firewall-cmd --zone=public --add-port=5140/udp --permanent 
- sudo firewall-cmd --reload 
- sudo firewall-cmd --list-ports

<p>
<img src="https://github.com/user-attachments/assets/c100f2a2-740a-41e0-8dea-609195bbda24" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/6d139677-54bd-44b6-bf26-6ef781f753e7" width="150"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/cf2ff258-edf0-43b3-8d2f-a6ad124af1d9" width="250"/>
<p>

#### Created Graylog rsyslog Configuration

- sudo vi /etc/rsyslog.d/90-graylog.conf

<img src="https://github.com/user-attachments/assets/9fe2b395-9993-461c-82fa-2a5ddbe0d774" width="250"/>

#### Added:

- ** @10.1.30.51:5140;RSYSLOG_SyslogProtocol23Format

<img src="https://github.com/user-attachments/assets/a95ebb9c-95e8-4571-8d26-3eb5809ac440" width="250"/>

#### Restarted rsyslog:

- sudo systemctl restart rsyslog

<img src="https://github.com/user-attachments/assets/ff5dbd14-3c2f-4372-9f8d-a04ab61d1db8" width="250"/>

#### Verified Logs in Graylog

***Logs from **dev-performance** were visible in Graylog.***

<img src="https://github.com/user-attachments/assets/d01e04bb-818b-4bf6-b666-9ee5a3eb5cbf" width="300"/>

---

## Result
Successfully configured **dev-app**, **stage-web**, and **dev-performance** servers as Graylog clients. All three servers are forwarding logs to the Graylog server at **10.X.XX.51**, and log entries were confirmed through the Graylog web interface.

