# Subir MySQL e phpMyAdmin com Docker

## Passos

1. Salve o script abaixo em uma pasta, por exemplo `c:\dev-mysql`, em um arquivo com nome `docker-compose.yml`.

2. Abra um terminal (caso Windows: PowerShell modo Administrador), acesse a pasta `c:\dev-mysql` e execute o comando:

```bash
docker compose up -d
```

3. Confira se os containers subiram corretamente, ou no Docker Desktop, ou digitando o comando:

```bash
docker ps
```

4. Para acessar o MySQL pelo phpMyAdmin, acesse o endereço `http://localhost:8888` e faça o login com usuário `root` e senha `1234567`.

## Script Docker Compose para copiar

```yaml
services:
  # ====================================================================================================================
  # MYSQL SERVER (8.x)
  # ====================================================================================================================
  mysql-docker:
    image: mysql:8.0
    container_name: dev-mysql
    environment:
      MYSQL_ROOT_PASSWORD: 1234567
      MYSQL_DATABASE: mydatabase
      # opcional: criar um usuário específico
      MYSQL_USER: developer
      MYSQL_PASSWORD: 1234567
    ports:
      - "3306:3306"
    command: ["--default-authentication-plugin=mysql_native_password"]
    volumes:
      - ./.data/mysql8/data:/var/lib/mysql
    networks:
      - dev-network
    healthcheck:
      test: ["CMD-SHELL", "mysqladmin ping -h localhost -p1234567 || exit 1"]
      interval: 10s
      timeout: 5s
      retries: 5

  # ====================================================================================================================
  # PHPMYADMIN
  # ====================================================================================================================
  phpmyadmin-docker:
    image: phpmyadmin/phpmyadmin
    container_name: dev-phpmyadmin
    environment:
      PMA_HOST: mysql-docker
      PMA_PORT: 3306
      # opcional: login automático no root
      # PMA_USER: root
      # PMA_PASSWORD: 1234567
    ports:
      - "8888:80"
    depends_on:
      - mysql-docker
    networks:
      - dev-network

# ======================================================================================================================
# REDE
# ======================================================================================================================
networks:
  dev-network:
    driver: bridge
```

