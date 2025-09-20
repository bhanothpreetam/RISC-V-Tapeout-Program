---

````md
# Week 0 – Tools Installation

**Dates:** YYYY-MM-DD → YYYY-MM-DD  
**Outcome:** All required tools installed and verified on Ubuntu

---

## Yosys

### 1. Commands Run
```bash
sudo apt-get update
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt-get install build-essential clang bison flex \
  libreadline-dev gawk tcl-dev libffi-dev git \
  graphviz xdot pkg-config python3 libboost-system-dev \
  libboost-python-dev libboost-filesystem-dev zlib1g-dev
git submodule update --init --recursive
make -j"$(nproc)"
sudo make install
````

### 2. Verification Screenshot

![yosys-version](./assets/yosys-version.png)

### 3. Problems Faced

* **Error:** `E: Unable to locate package zlib1g-d`
  **Fix:** Corrected package name → `zlib1g-dev`
* **Error:** `make: *** No rule to make target 'config-gcc'`
  **Fix:** Skipped `make config-gcc`; used `make && sudo make install`
* **Error:** `Initialize the submodule: Run 'git submodule update --init'`
  **Fix:** Ran `git submodule update --init --recursive`

---

## Icarus Verilog

### 1. Commands Run

```bash
sudo apt-get update
sudo apt-get install iverilog
iverilog -V
```

### 2. Verification Screenshot

![iverilog-version](./assets/iverilog-version.png)

### 3. Problems Faced

*No issues encountered*

---

## GTKWave

### 1. Commands Run

```bash
sudo apt-get update
sudo apt-get install gtkwave
gtkwave --version
```

### 2. Verification Screenshot

![gtkwave-version](./assets/gtkwave-version.png)
![gtkwave](./assets/gtkwave.png)

### 3. Problems Faced

* **Warning:** `Gtk-Message: Failed to load module "canberra-gtk-module"`
  **Fix:**

  ```bash
  sudo apt-get install libcanberra-gtk-module libcanberra-gtk3-module
  ```

---

## ngspice

### 1. Commands Run

```bash
# download from SourceForge
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release && cd release
../configure --with-x --with-readline=yes --disable-debug
make
sudo make install
ngspice -v
```

### 2. Verification Screenshot

![ngspice-version](./assets/ngspice-version.png)

### 3. Problems Faced

*(fill if any)*

---

## Magic

### 1. Commands Run

```bash
sudo apt-get install m4 tcsh csh libx11-dev tcl-dev tk-dev \
  libcairo2-dev mesa-common-dev libglu1-mesa-dev libncurses-dev
git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
sudo make install
magic -v
```

### 2. Verification Screenshot

![magic-version](./assets/magic-version.png)

### 3. Problems Faced

*(fill if any)*

---

## OpenLANE

### 1. Commands Run

```bash
sudo apt-get update && sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git \
  apt-transport-https ca-certificates curl software-properties-common

# Docker setup
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o \
  /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io

# Test Docker
docker run hello-world

# Clone OpenLANE
cd $HOME
git clone https://github.com/The-OpenROAD-Project/OpenLane
cd OpenLane
make
make test
```

### 2. Verification Screenshot

![openlane-test](./assets/openlane-test.png)
![openlane-help](./assets/openlane-help.png)

### 3. Problems Faced

*(fill if any)*

---

# ✅ Summary

* Yosys, Icarus Verilog, GTKWave, ngspice, Magic, and OpenLANE successfully installed.
* Documented all errors and fixes.
* Verification screenshots saved in `WEEK-00/assets/`.

```

---
