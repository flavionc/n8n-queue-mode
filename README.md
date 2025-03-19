# n8n-queue-mode

<img src="https://upload.wikimedia.org/wikipedia/commons/5/53/N8n-logo-new.svg" width="100" height="50" alt="n8n Logo"> | <img width="50" height="50" src="https://www.postgresql.org/media/img/about/press/elephant.png" alt="PostgreSQL Logo">  | <img width="90" height="50" src="https://upload.wikimedia.org/wikipedia/commons/6/64/Logo-redis.svg" alt="Redis Logo">
:---: | :---: | :---:


## Descrição

Configuração para realizar o deploy do n8n em Docker no modo Fila, utilizando PostgreSQL como banco de dados, Redis para gerenciamento de fila e múltiplos workers.

## Pré-requisitos

- Docker
- Docker Compose
- Arquivo `.env` configurado

## Configuração

### Arquivos

- `compose.yaml`: Definição dos serviços Docker
- `.env.example`: Modelo de configurações de ambiente
- `scripts/`: Scripts de inicialização do banco de dados

### Serviços

1. **PostgreSQL**: Banco de dados principal
2. **Redis**: Gerenciamento de fila
3. **n8n**: Serviço principal
4. **n8n-worker-1 e n8n-worker-2**: Workers para processamento distribuído

## Configuração de Ambiente

Copie `.env.example` para `.env` e ajuste as variáveis:

```
POSTGRES_USER=
POSTGRES_PASSWORD=
POSTGRES_DB=
POSTGRES_NON_ROOT_USER=
POSTGRES_NON_ROOT_PASSWORD=
N8N_ENCRYPTION_KEY=
N8N_HOST=
N8N_PROTOCOL=
N8N_RUNNERS_ENABLED=
NODE_ENV=
GENERIC_TIMEZONE=
```

## Inicialização

```bash
docker-compose up -d
```

## Características

- Modo fila habilitado
- Autenticação básica ativada
- Dois workers para processamento distribuído
- Volumes persistentes para dados

## Segurança

- Variáveis de ambiente separadas
- Rede Docker isolada
- Healthchecks para serviços