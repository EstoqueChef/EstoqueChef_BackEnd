
# 🍲 Sistema de Gestão de Estoque e Receitas

Backend para gerenciamento de estoque de insumos e planejamento de produções com base em receitas. Calcula automaticamente o que há em estoque, o que falta, e gera uma lista de compras.

---

## 🚀 Tecnologias Utilizadas

- **Python 3.13**
- **Poetry** e **Pipx** para gerenciamento de dependências
- **FastAPI** (API moderna e rápida)
- **SQLAlchemy** ou **Tortoise ORM** (a definir)
- **SQLite** (local) e **PostgreSQL** (produção)
- **Pydantic** (validação de dados)
- **Uvicorn** (servidor ASGI)
- **Pytest** (testes automatizados)

---

## ⚙️ Instalação

```sh
pip install --user pipx
pipx ensurepath

pipx install poetry
poetry self add poetry-plugin-shell

poetry shell
poetry python install 3.13
poetry env use 3.13
poetry install
```

---

## ▶️ Execução da API

```sh
task run
```

---

## 🧠 Estrutura do Projeto

```plaintext
estoque-receitas-backend/
├── app/
│   ├── models/         # Modelos ORM
│   ├── schemas/        # Schemas Pydantic
│   ├── services/       # Regras de negócio
│   ├── api/            # Rotas REST
│   ├── core/           # Configurações e inicialização
│   └── main.py         # App FastAPI
├── repositories/       # Abstrações de acesso ao BD
├── tests/              # Testes Pytest
├── pyproject.toml
└── README.md
```

---

## 📐 Arquitetura

```plaintext
Clientes (Web/Mobile) ─► FastAPI (main.py)
                        └── api/ (rotas REST)
                            └── services/ (lógica de negócio)
                                └── repositories/ (acesso a dados)
                                    └── models/ (ORM)
                                        └── Banco de Dados (SQLite/PostgreSQL)
```

---

## 🧾 Funcionalidades

### Estoque e Insumos
- Cadastro de insumos (nome, unidade, quantidade, validade)
- Atualização manual do estoque
- Filtros e ordenação por nome e validade

### Receitas
- Cadastro de receitas (nome, descrição)
- Relacionamento com insumos e quantidades

### Planejamento de Produção
- Planejamento com múltiplas receitas e quantidades
- Cálculo de insumos totais
- Comparação com estoque

### Lista de Compras
- Geração automática da lista de insumos faltantes

### Validade
- Destaque de insumos com validade próxima (< 7 dias)
- Listagem de vencidos e quase vencendo

### API RESTful
- CRUD completo para insumos, receitas, planejamentos e compras
- Documentação automática com OpenAPI

### Testes
- Cobertura com Pytest para todas as funcionalidades principais

---

## 🗃️ Modelos Principais

```plaintext
[Insumo]
- id
- nome
- unidade (kg, g, L, un)
- quantidade_disponivel
- data_validade

[Receita]
- id
- nome
- descricao

[ReceitaInsumo]
- receita_id → Receita
- insumo_id → Insumo
- quantidade_utilizada

[PlanejamentoProducao]
- id
- data
- receitas: lista (receita_id, quantidade_desejada)

[ListaCompra]
- planejamento_id → PlanejamentoProducao
- insumo_id
- quantidade_faltante
```

---

## ✅ TODO

- [ ] CRUD de insumos
- [ ] Filtros e ordenações por validade
- [ ] Cadastro e vínculo de receitas com insumos
- [ ] Planejamento de produção e cálculo de insumos
- [ ] Comparação com estoque e geração da lista de compras
- [ ] Controle de validade (alertas e relatórios)
- [ ] Testes automatizados com Pytest

---

## 📄 Licença

Projeto de código aberto. Sinta-se à vontade para contribuir!
