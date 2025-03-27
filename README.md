# TestandoIPFS
Projeto testando IPFS no Ubuntu 24.04.2 pela primeira vez 

## 1. Instalar Dependências

Antes de instalar o IPFS, atualize seu sistema e instale as dependências necessárias:

  ```bash
    sudo apt update && sudo apt upgrade -y
    sudo apt install wget tar -y
  ```

## 2. Baixar e Instalar o Kubo (IPFS CLI)

<b>2.1 Obter a versão mais recente</b>
Verifique a última versão em [Kubo](https://dist.ipfs.tech/kubo) e substitua X.Y.Z pela versão atual.
  ```bash
    VERSION="X.Y.Z"  # Altere para a versão mais recente
    wget "https://dist.ipfs.tech/kubo/v${VERSION}/kubo_v${VERSION}_linux-amd64.tar.gz"
  ```

<b>2.2 Extrair e Instalar</b>
  ```bash
    tar -xvzf kubo_v${VERSION}_linux-amd64.tar.gz
    cd kubo
    sudo ./install.sh
  ```

<b>2.3 Verificar Instalação</b>
  ```bash
    ipfs --version
  ```
  Saída esperada: "ipfs version X.Y.Z"


## 3. Inicializar o Nó IPFS

<b>3.1 Inicializar o Repositório IPFS</b>
  ```bash
    ipfs init
  ```
Isso criará uma pasta .ipfs no seu diretório home (~/.ipfs).

<b>3.2 Iniciar o Daemon (Servidor IPFS)</b>
  ```bash
    ipfs daemon
  ```
Saída esperada:
  ```bash
    API server listening on /ip4/127.0.0.1/tcp/5001
    Gateway server listening on /ip4/127.0.0.1/tcp/8080
    WebUI: http://127.0.0.1:5001/webui
  ```

    
  ## 4. Testar o IPFS

  <b>4.1 Adicionar um Arquivo</b>
  Crie um arquivo de teste e adicione ao IPFS:
  ```bash
    echo "HELLO IPFS NO UBUNTU" > teste.txt
    ipfs add teste.txt
  ```
  Saída esperada:
  ```bash
    added QmXoypizjW3WknFiJnKLwHCnL72vedxjQkDDP1mXWo6uco teste.txt
  ```
  <i>(Esse "QmXo... é o CID gerado)</i>

 <b>4.2 Acessar o Arquivo via Gateway Local</b>
  Abra no navegador:
  ```bash
    [echo "HELLO IPFS NO UBUNTU" > teste.txt](http://localhost:8080/ipfs/QmXoypizjW3WknFiJnKLwHCnL72vedxjQkDDP1mXWo6uco)
  ```
  <i>(Substitua pelo CID gerado)</i>

<b>4.3 Verificar Peers Conectados</b>

  Abra no navegador:
  ```bash
    ipfs swarm peers
  ```


## 5. Parar o Daemon

Para encerrar o ipfs daemon, pressione Ctrl + C no terminal onde ele está rodando.


