# CVE-2024-3094 Vulnerability Mitigation Ansible Playbook Script

This repository contains Ansible playbooks designed to identify and mitigate the CVE-2024-3094 vulnerability in systems using `xz-utils`. The vulnerability check playbook scans your hosts for vulnerable versions of `xz-utils`, and the fix playbook attempts to upgrade or downgrade `xz-utils` to a secure version, depending on the outcome of the upgrade attempt.

## Why This Project?

While my main shell script is good for checking if you have little number of systems but   when you need to scale up operations across many servers, it is not a suitable idea. Manually running shell scripts on a large number of servers is time-consuming and prone to human error. This script is created additionally to leverage Ansible's automation capabilities for a more efficient, reliable, and scalable approach to identifying and mitigating the CVE-2024-3094 vulnerability.

Ansible allows us to automate the detection and remediation processes across all servers in our inventory with a single command, reducing the potential for mistakes and greatly simplifying the management of large infrastructures.

## Caution

Before opting to automatically fix detected vulnerabilities with the provided Ansible playbooks, users are strongly advised to **carefully research** and **understand the implications** of the changes being made. While the playbooks are designed to safely upgrade or downgrade `xz-utils` to a non-vulnerable version, it is crucial to:

- **Test the playbooks** in a controlled environment before deploying them in production.
- **Review the changes** that will be made to each server, ensuring they will not disrupt your operations or conflict with specific system requirements.
- **Consider the dependencies** and the potential impact on other applications or services running on your servers.

Automating system changes can significantly enhance efficiency and consistency, but it also requires diligence to ensure that the automation does not inadvertently introduce new issues.


## Getting Started

These instructions will guide you through the setup and execution of the Ansible playbooks to mitigate the CVE-2024-3094 vulnerability across your infrastructure.

### Prerequisites

- Ansible installed on your control machine.
- SSH access and sudo privileges on the target hosts.

### Setup

1. Clone this repository to your control machine:


2. Navigate to the cloned directory:


`cd CVE-2024-3094-mitigation`


3. Make the setup script executable: 


`chmod +x setup_and_run_ansible_cve_fix.sh`


### Running the Playbooks

1. Execute the setup script and follow the prompts to configure the paths and options:` 

`
./setup_and_run_ansible_cve_fix.sh `

You will be asked to:

- Specify the path to your initial Ansible hosts file.
- Choose where to save the list of impacted hosts.
- Decide whether to automatically run the fix playbook on impacted hosts.
- Specify the path to save the final remediation report.

2. Depending on your choice during the setup, the script will either:
- Directly run the playbooks to check for and fix the vulnerability.
- Provide you with the commands to manually run the playbooks.

### Manual Execution

If you chose not to automatically run the fix playbook, you can manually execute the playbooks as follows:

1. To check for vulnerable hosts:
`
ansible-playbook -i path/to/your/hosts.ini check_vulnerability.yml `


 2. To fix the vulnerable hosts and generate a report:

`ansible-playbook -i path/to/impacted_hosts.ini fix_vulnerable_hosts.yml`

 ### Report

After running the fix playbook, a report will be generated at the specified path, detailing the outcome for each host and suggesting further actions, if necessary.

## Contributing

Contributions to this project are welcome. Please consider forking the repository and submitting a pull request with your enhancements.

## License

This project is licensed under the MIT License


## Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.`
