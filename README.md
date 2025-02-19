# Setup

1. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html). The easiest way (especially on Pi or a Debian system) is via Pip:
   1. (If on Pi/Debian): `sudo apt-get install -y python3-pip`
   2. (Everywhere): `pip3 install ansible`
2. Clone this repository: `git clone https://github.com/geerlingguy/internet-pi.git`, then enter the repository directory: `cd internet-pi`.
3. Install requirements: `ansible-galaxy collection install -r requirements.yml` (if you see `ansible-galaxy: command not found`, restart your SSH session or reboot the Pi and try again)
4. Make copies of the following files and customize them to your liking:
   - `example.inventory.ini` to `inventory.ini` (replace IP address with your Pi's IP, or comment that line and uncomment the `connection=local` line if you're running it on the Pi you're setting up).
   - `example.config.yml` to `config.yml`
5. Run the playbook: `ansible-playbook main.yml`

> **If running locally on the Pi**: You may encounter an error like "Error while fetching server API version". If you do, please either reboot or log out and log back in, then run the playbook again.

# Usage

## Pi-hole

Visit the Pi's IP address (e.g. http://192.168.1.10/) and use the `pihole_password` you configured in your `config.yml` file. An existing pi-hole installation can be left unaltered by disabling the setup of this proyect's installation in your `config.yml` (`pihole_enable: false`)

# Updating

## pi-hole

To upgrade Pi-hole to the latest version, run the following commands:

```bash
cd ~/pi-hole #
docker-compose pull             # pulls the latest images
docker-compose up -d --no-deps  # restarts containers with newer images
docker system prune --all       # deletes unused images
```
