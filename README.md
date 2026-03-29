# BJJRecords

Monorepo do **BJJ Training App** — diário de treinos de Jiu-Jitsu Brasileiro.

| Pasta | Conteúdo |
|--------|-----------|
| `backend/BJJRecords.Api` | API ASP.NET Core (.NET 8) + Entity Framework Core + PostgreSQL |
| `mobile/` | App Flutter (a ser criado com `flutter create`) |

## Pré-requisitos (Linux)

- [.NET SDK 8](https://dotnet.microsoft.com/download) — o arquivo `global.json` aponta para a versão 8.0.x usada no projeto. Se o `dotnet` não estiver no `PATH` (por exemplo após instalar em `~/.dotnet`), execute: `export PATH="$HOME/.dotnet:$PATH"` ou adicione essa linha ao seu `~/.bashrc`.
- [Docker](https://docs.docker.com/engine/install/) (opcional, para subir o PostgreSQL localmente)
- Flutter (quando for iniciar o mobile)

## Banco de dados com Docker

Na raiz do repositório:

```bash
docker compose up -d
```

Credenciais de desenvolvimento (alinhadas a `appsettings.Development.json`):

- Host: `localhost`, porta `5432`
- Banco: `bjjrecords`
- Usuário / senha: `bjjrecords` / `bjjrecords_dev`

## Executar a API

```bash
cd backend/BJJRecords.Api
dotnet restore
dotnet run
```

- HTTP: `http://localhost:5080`
- Swagger (ambiente Development): `http://localhost:5080/swagger`
- Health: `http://localhost:5080/health`

Em produção, defina a connection string com a variável de ambiente `ConnectionStrings__DefaultConnection` (não commitar segredos).

## Solução .NET

```bash
dotnet restore BJJRecords.sln
dotnet build BJJRecords.sln
```

## Próximos passos sugeridos

- `dotnet ef migrations add InitialCreate` após definir entidades no `AppDbContext`
- Projeto Flutter em `mobile/` apontando para a API
