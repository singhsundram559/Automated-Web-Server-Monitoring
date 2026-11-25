# Project Test Cases

## 1. Ansible Connectivity Test
Command:
ansible webservers -m ping

Expected Result:
Successful connection with pong response.

Status: PASS

## 2. Nginx Installation and Deployment
Command:
ansible-playbook deploy.yml -K

Expected Result:
Nginx is installed and website files are deployed.

Status: PASS

## 3. Nginx Service Verification
Command:
sudo systemctl is-active nginx

Expected Result:
active

Status: PASS

## 4. Ansible Idempotency Test
Command:
ansible-playbook deploy.yml -K

Expected Result:
Second execution should report changed=0 when no configuration changes are required.

Observed Result:
ok=6, changed=0, failed=0

Status: PASS

## 5. Website HTTP Test
Command:
curl http://localhost

Expected Result:
Website HTML content is returned.

Status: PASS

## 6. Nginx Failure Detection
Procedure:
Stop Nginx using sudo systemctl stop nginx.

Expected Result:
Nagios reports the Nginx HTTP service as CRITICAL.

Observed Result:
Connection refused on port 80.

Status: PASS

## 7. Nginx Recovery Test
Procedure:
Start Nginx using sudo systemctl start nginx.

Expected Result:
Nagios reports the HTTP service as OK after its next monitoring check.

Observed Result:
HTTP/1.1 200 OK after recovery.

Status: PASS

## Testing Note
Results are based on the local Ubuntu WSL2 implementation.
