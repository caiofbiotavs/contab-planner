# Contab Planner — Deploy

Este repositório contém a infraestrutura necessária para realizar o deploy em produção do sistema **Contab Planner**, utilizando a stack oficial contêinerizada (Next.js, FastAPI, Redis, Celery).

## 🚀 Requisitos

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## ⚙️ Configuração Inicial

1. Faça o clone deste repositório na sua VPS ou máquina de produção:
   ```bash
   git clone <url-deste-repositorio>
   cd contab-planner-deploy
   ```

2. Crie o arquivo de variáveis de ambiente com base no exemplo:
   ```bash
   cp .env.example .env
   ```

3. Abra o arquivo `.env` e preencha com as suas credenciais do **Supabase** e chaves de segurança. (Utilize `openssl rand -hex 32` no seu terminal para gerar chaves fortes para `SESSION_SECRET` e `PROXY_SECRET`).

## 🚢 Subindo a Aplicação

Para iniciar o sistema de forma limpa em background, basta executar:

```bash
docker compose up -d
```

### Serviços Inicializados:
- **Frontend (Next.js)** na porta `3000`
- **Backend (FastAPI)** na porta `8000` (exposto apenas internamente)
- **Redis** e **Celery** (Workers/Beat para tarefas em segundo plano)

## 🔄 Atualizando o Sistema

Sempre que houver uma nova versão, para atualizar basta baixar as novas imagens e reiniciar os containers:

```bash
docker compose pull
docker compose up -d
```
