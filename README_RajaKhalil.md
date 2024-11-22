
# Projeto Toshiro Shibakita

Este é um projeto de microserviços com Docker utilizando MySQL, PHP, e Nginx. O objetivo é construir um ambiente de desenvolvimento com contêineres Docker para facilitar o gerenciamento e execução de serviços.

## 🚀 Como Rodar o Projeto

### Pré-requisitos
Antes de rodar o projeto, você precisa ter as seguintes ferramentas instaladas:

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Passos para Iniciar

1. **Clone o repositório:**
   ```
   git clone https://github.com/seuusuario/toshiro-shibakita.git
   cd toshiro-shibakita
   ```

2. **Certifique-se de que o Docker está em execução.**

3. **Inicie os contêineres com o Docker Compose:**
   ```
   docker-compose up --build
   ```

4. **Acesse o MySQL (caso tenha acesso à senha ou se esteja configurado para acesso direto):**
   ```
   docker exec -it mysql-container mysql -u root -p
   ```
   (Quando solicitado, insira a senha configurada para o MySQL)

5. **Acesse o PHP e Nginx através dos contêineres.**

### Como Parar os Contêineres

Quando terminar, você pode parar os contêineres com o comando:

```
docker-compose down
```

---

## ⚠️ Possíveis Problemas e Soluções

### 1. **Erro de Portas (Port 3306 já está em uso)**
Se ao iniciar o contêiner do MySQL você receber um erro dizendo que a porta `3306` já está em uso, isso pode ocorrer se você já estiver executando outro serviço que esteja usando essa porta.

**Solução:**
- Tente parar o serviço que está usando a porta `3306` ou mude a porta no arquivo `docker-compose.yml`:

```yaml
services:
  mysql:
    ports:
      - "3307:3306"
```

Isso mapeia a porta 3307 do host para a 3306 do contêiner.

### 2. **Erro de Permissões**
Se você estiver recebendo erros de "acesso negado" ou problemas ao tentar acessar o MySQL, isso pode estar relacionado a permissões de acesso ou configuração de rede.

**Solução:**
- Verifique as configurações do MySQL e das permissões de rede, ajustando as variáveis de ambiente conforme necessário.
- Se necessário, ajuste as permissões ou tente rodar o contêiner com privilégios elevados (usando `sudo`, por exemplo).

### 3. **Avisos de Obsolescência no Docker Compose**
Se você receber um aviso sobre a versão obsoleta no arquivo `docker-compose.yml`, isso pode ser causado pela versão usada. Recentemente, as versões `version` em `docker-compose.yml` não são mais necessárias.

**Solução:**
- Remova a linha `version` do arquivo `docker-compose.yml`.

---

## 📄 Estrutura do Projeto

```
toshiro-shibakita/
│
├── docker-compose.yml        # Arquivo de configuração do Docker Compose
├── nginx.conf                # Configuração do servidor Nginx
└── Dockerfile                # Arquivo de construção do contêiner Nginx
```

---

## 📝 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para mais detalhes.
