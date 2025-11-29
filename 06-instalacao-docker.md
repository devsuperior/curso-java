# Guia Rápido de Instalação e Verificação do Docker

## Windows (Docker Desktop)

1. **Baixar o instalador**

   * Acesse: https://docs.docker.com/desktop/setup/install/windows-install
   * Baixe a versão para Windows.

2. **Executar o instalador**

   * Clique duas vezes no arquivo `.exe`.
   * Mantenha as opções padrão.
   * O instalador solicitará habilitação do **WSL 2** caso ainda não esteja ativo.

3. **Finalizar instalação**

   * Reinicie o computador caso solicitado.
   * Abra o **Docker Desktop**.

4. **Confirmar instalação**
   Abra o **PowerShell** e execute:

```
 docker --version
```

Se a mensagem "Hello from Docker!" aparecer, está funcionando.

---

## Linux (Ubuntu)

1. **Atualizar pacotes**

```
 sudo apt update
```

2. **Instalar dependências**

```
 sudo apt install ca-certificates curl gnupg lsb-release
```

3. **Adicionar chave GPG oficial**

```
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker.gpg
```

4. **Adicionar repositório Docker**

```
 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. **Instalar o Docker Engine**

```
 sudo apt update
 sudo apt install docker-ce docker-ce-cli containerd.io
```

6. **Adicionar seu usuário ao grupo docker (opcional)**

```
 sudo usermod -aG docker $USER
```

(Saia e entre no sistema novamente.)

7. **Confirmar instalação**

```
 docker --version
```

---

## macOS (Docker Desktop)

1. **Baixar o instalador**

   * Acesse: https://docs.docker.com/desktop/setup/install/mac-install/
   * Baixe a versão para macOS (Intel ou Apple Silicon).

2. **Instalar**

   * Abra o arquivo `.dmg`.
   * Arraste o aplicativo **Docker.app** para a pasta Applications.

3. **Executar**

   * Abra o **Docker Desktop**.
   * Aguarde até que o ícone indique que o Docker está rodando.

4. **Confirmar instalação**
   Abra o Terminal e execute:

```
 docker --version
```

Se a execução do container apresentar a mensagem de sucesso, a instalação está concluída.

