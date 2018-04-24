# Установка node js через nvm

Для установки node js используем nvm (node version manager) , тк это более удобная программа для установки и контроля версий node


```
sudo apt-get update
sudo apt-get install build-essential libssl-dev
```
Скачиваем скрипт install_nvm.sh и запускаем

```
curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh -o install_nvm.sh

bash install_nvm.sh
```

Для получения доступа к функционалу nvm, вам необходимо перелогиниться в системе, 
либо вы можете использовать команду source для того, чтобы применить изменения не прерывая текущую сессию:

```
source ~/.profile
```

Чтобы узнать, какие версии Node.js доступны для установки, наберите:

```
nvm ls-remote
```

Чтобы узнать, какие версии Node.js установлены и доступны, наберите:

```
nvm ls
```

Для установки node какой либо версии 
(установит версию 7.9.0)

```
nvm install 7.9.0
```



Для для использования node какой либо версии 
(использует версию 6.0.0)

```
nvm use 6.0.0

```
