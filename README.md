# PipelineArthur

API Flask com três rotas JSON. A rota `/` retorna uma saudação e `/alunos?nome=an` retorna os nomes que contêm o trecho pesquisado. A rota `/saude` retorna `{"status": "ok"}`.

## Execução local

Use Python 3.12 e um ambiente virtual.

```bash
python -m pip install -r requirements.txt
python -m pytest -v
python app.py
```

## GitHub Actions

Em pull requests para `main`, o workflow executa pytest, CodeQL, detect-secrets e revisão de dependências. Em pushes para `main`, o job de staging depende de pytest, CodeQL e detect-secrets. Ele gera o artefato `app-staging` e registra um deploy simulado.

No repositório público, habilite Dependency graph, Dependabot alerts, Dependabot security updates, secret scanning e push protection. Mantenha desativada a configuração padrão do CodeQL para usar a configuração do workflow.

Crie o environment `staging` com `APP_ENV=staging` e `STAGING_URL=https://example.com/staging`. A URL é ilustrativa. O deploy empacota a aplicação e disponibiliza o arquivo na execução do workflow.

O Dependabot verifica semanalmente as dependências do Python e as ações do GitHub.
