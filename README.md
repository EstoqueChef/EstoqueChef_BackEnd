# 🍲 Sistema de Gestão de Estoque e Receitas

Backend do sistema que permite ao usuário gerenciar seu estoque de ingredientes/materiais, cadastrar receitas e planejar produções. O sistema calcula automaticamente o que há em estoque e o que precisa ser comprado com base nas receitas e suas quantidades desejadas.

---

## 🚀 Tecnologias Utilizadas

- **Python 3.13**
- **Poetry** para gerenciamento de dependências
- **Pipx** para gerenciamento de dependências
- **FastAPI** (API web rápida e moderna)
- **SQLAlchemy** ou **Tortoise ORM** (a definir)
- **SQLite** (para persistência local inicial)
- **Pydantic** (validação de dados)
- **Uvicorn** (servidor ASGI para desenvolvimento)

---

## Instalação

1. Instale o `pipx`:
   ```sh
   pip install --user pipx
   pipx ensurepath
   ```

2. Instale o `poetry`:
   ```sh
   pipx install poetry
   ```

3. Adicione o plugin de shell do `poetry`:
   ```sh
   poetry self add poetry-plugin-shell
   ```

4. Crie um ambiente virtual e ative-o:
   ```sh
   poetry shell
   ```

5. Certifique-se de que está utilizando a versão correta do Python:
   ```sh
   poetry python install 3.13
   poetry env use 3.13
   ```

6. Instale as dependências do projeto:
   ```sh
   poetry install
   ```

## Execução da API

Para rodar a API, utilize o seguinte comando:

```sh
task run
```

## 🧠 Estrutura do Projeto

```plaintext
estoque-receitas-backend/
├── app/
│   ├── models/           # Modelos do banco de dados (ORM)
│   ├── schemas/          # Schemas Pydantic (entrada e saída)
│   ├── services/         # Regras de negócio
│   ├── api/              # Rotas da API
│   ├── core/             # Configurações gerais (banco de dados, settings)
│   └── main.py           # Inicialização do FastAPI
├── tests/                # Testes automatizados
├── pyproject.toml        # Configuração do Poetry e dependências
└── README.md             # Este arquivo
```

# ✅ Funcionalidades Planejadas

## Funcionalidades

- **Cadastro de insumos/ingredientes no estoque**
  - Nome, unidade (kg, L, un, etc), quantidade disponível
  - **Data de validade (opcional)** para controle de perecíveis
- **Atualização e visualização do estoque**
  - Ver o que há disponível, filtrando por nome ou validade
- **Cadastro de receitas**
  - Lista de insumos com quantidades por unidade
- **Planejamento de produção**
  - Planejar a produção de múltiplas receitas
- **Cálculos automáticos**
  - Total de insumos necessários com base no planejamento
  - Comparação automática com o estoque
  - Geração da lista de compras com o que está faltando
- **Controle de validade dos insumos**
  - Insumos com validade próxima são destacados
  - Pode ser usado para evitar desperdício
- **API REST**
  - Endpoints para todas as funcionalidades (CRUD, cálculo, etc)
- **Testes automatizados**
  - Testes com `pytest` para garantir consistência do sistema

# 📝 TODO - Etapas de Desenvolvimento

## �️ Estrutura Inicial

- Criar projeto com poetry new
- Criar estrutura de diretórios app/ conforme acima
- Adicionar FastAPI, Uvicorn e ORM como dependências

## � Modelagem de Dados

- ItemEstoque (id, nome, unidade, quantidade atual)
- Receita (id, nome)
- IngredienteReceita (id, receita_id, item_id, quantidade)
- PlanejamentoReceita (id, receita_id, vezes)

## ⚙️ Lógica de Negócio

- Função para calcular insumos necessários baseado no planejamento
- Função para comparar com estoque e gerar lista de compras
- Função para atualizar o estoque após produção

## 🌐 API (Endpoints REST)

- GET/POST /estoque - listar, criar itens de estoque
- GET/POST /receitas - listar, criar receitas
- GET/POST /planejamento - definir quantas vezes fazer cada receita
- GET /analise - calcular insumos totais e o que falta comprar

## � Testes

- Configurar Pytest
- Testes unitários para os serviços de cálculo
- Testes de integração para a API

## 📚 Extras

- Documentação automática com Swagger (nativo no FastAPI)
- Adicionar CORS para integração futura com frontend
- Setup de .env para configs
