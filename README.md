🚀 Gensyn RL-Swarm Setup Guide



A easy guide for Gensyn RL-Swarm on Ubuntu.

Requirements for VPS :-

* Min 20 GB RAM
* RTX 3090/4090 GPU ( Optional )

---



 1. Install Required Dependencies

```bash

sudo apt update \&\& sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof
python3 --version
curl -fsSL https://deb.nodesource.com/setup\_20.x | sudo -E bash -
sudo apt update \&\& sudo apt install -y nodejs
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list > /dev/null
sudo apt update \&\& sudo apt install -y yarn
node -v
npm -v
yarn -v

```



---



 2. Clone the RL-Swarm Repository

```bash
git clone https://github.com/gensyn-ai/rl-swarm.git
```

---

 3. Create a Screen Session


```bash

screen -S gensyn

```



---



 4. Set Up Environment & Install Frontend Dependencies

```bash
cd rl-swarm python3 -m venv .venv
source .venv/bin/activate
cd modal-login
yarn install
yarn upgrade \&\& yarn add next@latest \&\& yarn add viem@latest
cd ..

```



---



 5. Update Repository Before Running

```bash
git switch main git reset --hard
git clean -fd git pull origin main

```



---



 6. Start RL-Swarm



```bash

./run\_rl\_swarm.sh

```



---



 7. Login (Cloudflared Tunnel)
    After successfully running the run cmnd.

    Ctrl A + D
    
    then run the below cammand

```bash

 cloudflared tunnel --url http://localhost:3000

```
If above tunnel wont work then use below cmd 

```bash
curl -fsSL https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64 -o cloudflared
chmod +x cloudflared
sudo mv cloudflared /usr/local/bin

cloudflared tunnel --url http://localhost:3000
```

---


 To cheak your node is running or not



```bash

screen -r gensyn

```



---



Guide By


X:(Twitter): @vickyjanjalkar 
https://x.com/vickyjanjalkar



---






