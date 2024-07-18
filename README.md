## System Requirements

| Component         | Requirement                       |
|:-----------------:|:---------------------------------:|
| **CPU**           | 4 CPU cores                       |
| **RAM**           | 16 GB RAM                         |
| **Disk**          | 50 GB disk                        |
| **OS** | Ubuntu 24.04  |

## Upgrading to Ubuntu 24.04
- Check your OS using this command
```bash
lsb_release -ds
```
- If you get `Ubuntu 24.04` in the output, you are good to go , if you get `Ubuntu 20.04` or lower version of Ubuntu, you need to upgrade to `Ubuntu 24.04`
- I can mention the steps to upgrade to Ubuntu 24.04 but if you running any node in current version, you might face other issues, so I am suggesting you to buy a new VPS with OS `Ubuntu 24.04`
## Opening 8000 and 9000 Port to Public
- Use these commands to emable Firewall
```bash
sudo ufw enable
```
- Allow port 8000 and 9000 by using this command
```bash
sudo ufw allow 8000
sudo ufw allow 9000
```
- Check status using below command
```bash
sudo ufw status
```
- You will see something like this

![pawelzmarlak-2024-07-18T08_32_42 566Z](https://github.com/user-attachments/assets/1cc75d9a-b126-4ad2-ab1d-52816234bf7d)

- Now use this command :
```bash
ss -tuln | grep -E '8000|9000'
```
- You will see both 8000 and 9000 port there

![pawelzmarlak-2024-07-18T08_37_49 332Z](https://github.com/user-attachments/assets/0119fafe-5c6d-4a14-b9d4-e3e904c00769)

- If it is showing only 8000 port, you need to create a screen session

```bash
sudo apt update
```
```bash
sudo apt install screen
```
```bash
screen -S PORT9000
```
```bash
sudo python3 -m http.server 9000
```
- Now detach from screen session using `Ctrl+A+D`

- Now again use this comamnd to check whether you can 8000 and 9000 port or not

```bash
ss -tuln | grep -E '8000|9000'
```
- If you see both 8000 and 9000 there, you are good to go

## Installation
- Use these commands one by one
```bash
sudo adduser hlnode
```
```bash
sudo usermod -aG sudo hlnode
```
```bash
su - hlnode
```
```bash
curl https://binaries.hyperliquid.xyz/Testnet/initial_peers.json > ~/initial_peers.json
```
```bash
echo '{"chain": "Testnet"}' > ~/visor.json
```
```bash
curl https://binaries.hyperliquid.xyz/Testnet/non_validator_config.json > ~/non_validator_config.json
```
```bash
curl https://binaries.hyperliquid.xyz/Testnet/hl-visor > ~/hl-visor
```
```bash
chmod a+x ~/hl-visor
```
```bash
~/hl-visor
```
