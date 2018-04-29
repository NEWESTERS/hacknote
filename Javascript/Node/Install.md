# Установка Node.js через NVM
Для установки [Node.js](https://nodejs.org) используем **NVM** (Node Version Manager), т.к. это наиболее удобная программа для установки и контроля версий **Node**:
```
sudo apt-get update
sudo apt-get install build-essential libssl-dev
```
Скачиваем скрипт **install_nvm.sh** и запускаем:
```
curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh -o install_nvm.sh

bash install_nvm.sh
```
Для получения доступа к функционалу **NVM**, вам необходимо перелогиниться в системе, либо вы можете использовать команду `source` для того, чтобы применить изменения не прерывая текущую сессию:
```
source ~/.profile
```
Чтобы узнать, какие версии **Node** доступны для установки, наберите:
```
nvm ls-remote
```
Чтобы узнать, какие версии **Node** установлены и доступны, наберите:
```
nvm ls
```
Установка **Node** версии `<version>`
```
nvm install <version>
```



