````markdown
🪟 To compile a wallet for **Microsoft Windows 64-bit** on **Ubuntu Server 22.04**, follow this single continuous guide:

🔄 First, update your system:

```bash
sudo apt-get update && sudo apt-get upgrade -y
````

📦 Install general build dependencies:

```bash
sudo apt-get install make automake cmake curl g++-multilib libtool binutils-gold bsdmainutils pkg-config python3 patch bison -y
```

📁 Create a directory to hold the source code:

```bash
cd ~/
mkdir source_code
cd source_code
```

🌐 Download the Pepe3 source code:

```bash
wget "https://dl.walletbuilders.com/download?customer=f0579c48bb63bd0c8a64297876a42fcb05630a49e7f9a82d94&filename=pepe3-source.tar.gz" -O pepe3-source.tar.gz
```

🗂️ Extract the archive:

```bash
tar -xzvf pepe3-source.tar.gz
```

🔧 Install cross-compilation dependencies:

```bash
sudo apt-get install g++-mingw-w64-x86-64 -y
sudo update-alternatives --set x86_64-w64-mingw32-g++ /usr/bin/x86_64-w64-mingw32-g++-posix
```

🏗️ Build Windows dependencies:

```bash
PATH=$(echo "$PATH" | sed -e 's/:\/mnt.*//g')
cd depends
make HOST=x86_64-w64-mingw32
cd ..
```

⚙️ Compile the Windows wallet:

```bash
./autogen.sh
CONFIG_SITE=$PWD/depends/x86_64-w64-mingw32/share/config.site ./configure --prefix=/
make
```

📂 The compiled Windows wallet (Qt GUI) will be in `src/qt`, and command-line tools like `pepe3-cli.exe` in `src`.

```
```
