
```markdown
# Projeto Base com Docker, PHP, MySQL, Traefik, phpMyAdmin e Redis

Este é um projeto básico configurado para facilitar o desenvolvimento com Docker. Ele inclui serviços essenciais como PHP, MySQL, Traefik (para roteamento), phpMyAdmin (para gerenciamento do banco de dados) e Redis (para cache). A aplicação principal fica na pasta `src`, e todos os serviços são configurados usando o Docker Compose.

> **Nota**: Este é um projeto "cru", ou seja, ele não inclui nenhuma aplicação pré-configurada. Ele serve apenas como base para ser usado em projetos PHP com suporte a banco de dados, cache e roteamento.

---

## Pré-requisitos

- Docker instalado e funcionando no seu sistema.
- Conhecimento básico de Docker e Docker Compose.

---

## Estrutura do Projeto

```
/projeto
  /docker
    /php         # Configuração do PHP
    /mysql       # Configuração do MySQL
    /traefik     # Configuração do Traefik
      /config
        traefik.yml          # Configuração estática do Traefik
        traefik_dynamic.yml  # Configuração dinâmica do Traefik
      /letsencrypt           # Certificados SSL/TLS
  /src                       # Código-fonte da aplicação
  /logs                      # Logs dos serviços
  docker-compose.yml         # Arquivo principal do Docker Compose
```

Os arquivos da sua aplicação devem ser colocados na pasta `src`. Esta é uma configuração "crua" para ser usada como base em projetos PHP com suporte a banco de dados, cache e roteamento.

---

## Configuração Inicial

### 1. Clonar o Projeto
Clone este repositório ou copie os arquivos para o seu diretório de trabalho.

```bash
git clone <URL_DO_REPOSITORIO>
cd <DIRETORIO_DO_PROJETO>
```

### 2. Configurar o Arquivo `hosts`

Para que os domínios locais (`app.local`, `phpmyadmin.local`, etc.) funcionem corretamente, você precisa adicionar entradas no arquivo `hosts` do seu sistema.

#### **Linux/MacOS**
Abra o arquivo `/etc/hosts` com permissões de superusuário:

```bash
sudo nano /etc/hosts
```

Adicione as seguintes linhas ao final do arquivo:

```
127.0.0.1 app.local
127.0.0.1 phpmyadmin.local
127.0.0.1 portainer.local
```

#### **Windows**
Abra o arquivo `C:\Windows\System32\drivers\etc\hosts` com permissões de administrador:
- Clique com o botão direito no Bloco de Notas e selecione "Executar como administrador".
- Abra o arquivo `hosts` através do menu "Arquivo > Abrir".

Adicione as seguintes linhas ao final do arquivo:

```
127.0.0.1 app.local
127.0.0.1 phpmyadmin.local
127.0.0.1 portainer.local
```

---

### 3. Iniciar os Serviços

Execute o seguinte comando para iniciar todos os serviços:

```bash
docker-compose up -d
```

Isso iniciará os containers do PHP, MySQL, Traefik, phpMyAdmin, Redis e Portainer.

---

## Acessar os Serviços

Após iniciar os containers, você pode acessar os serviços usando os seguintes URLs:

- **Aplicação Principal**: [http://app.local](http://app.local)
- **phpMyAdmin**: [http://phpmyadmin.local](http://phpmyadmin.local)
- **Portainer**: [http://portainer.local](http://portainer.local)
- **Traefik Dashboard**: [http://localhost:8081](http://localhost:8081)

> **Nota**: Se você estiver usando HTTPS (`https://app.local`), o navegador pode exibir um aviso de segurança porque os certificados são autoassinados. Isso é normal para ambientes de desenvolvimento.

---

## Detalhes dos Serviços

### 1. **Aplicação Principal**
- O código da aplicação deve ser colocado na pasta `src`.
- O servidor Nginx está configurado para servir os arquivos dessa pasta.

### 2. **MySQL**
- O MySQL está configurado com as seguintes credenciais padrão:
  - **Host**: `db`
  - **Usuário**: `user`
  - **Senha**: `password`
  - **Banco de Dados**: `app_base`

### 3. **phpMyAdmin**
- Use o phpMyAdmin para gerenciar o banco de dados MySQL.
- As credenciais são as mesmas do MySQL.

### 4. **Redis**
- O Redis está disponível para uso como cache ou fila.
- Host: `redis`

### 5. **Portainer**
- O Portainer fornece uma interface gráfica para gerenciar os containers Docker.
- Acesse em: [http://portainer.local](http://portainer.local)

### 6. **Traefik**
- O Traefik é usado para roteamento e gerenciamento de certificados SSL/TLS.
- O dashboard do Traefik pode ser acessado em: [http://localhost:8081](http://localhost:8081)

---

## Parar os Serviços

Para parar todos os serviços, execute:

```bash
docker-compose down
```

---

## Observações

- Este é um projeto "cru", destinado a ser usado como base para outros projetos.
- Certifique-se de ajustar as configurações conforme necessário para atender às suas necessidades específicas.
- Para depurar problemas, verifique os logs dos containers usando:

```bash
docker logs <NOME_DO_CONTAINER>
```

Exemplo:

```bash
docker logs traefik
```

---
```

---
