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

# ✅ TODO - Sistema de Gestão de Estoque e Receitas

## 📦 Cadastro de insumos/ingredientes no estoque
- [ ] Criar modelo de dados para insumos
- [ ] Incluir campo de unidade e quantidade
- [ ] Adicionar campo opcional `data_validade`
- [ ] Criar endpoints de CRUD (`POST`, `GET`, `PUT`, `DELETE`)

## 📊 Atualização e visualização do estoque
- [ ] Listar todos os insumos com filtros por nome e validade
- [ ] Implementar ordenação por data de validade
- [ ] Atualizar quantidade do estoque manualmente

## 🍲 Cadastro de receitas
- [ ] Criar modelo de receita (nome, descrição)
- [ ] Relacionar receitas com múltiplos insumos e quantidades
- [ ] CRUD completo para receitas

## 🧾 Planejamento de produção
- [ ] Criar endpoint para selecionar receitas e definir quantidades desejadas
- [ ] Armazenar planejamentos ou processar de forma transitória

## 🧮 Cálculos automáticos
- [ ] Calcular insumos totais necessários com base no planejamento
- [ ] Comparar com estoque atual
- [ ] Gerar lista do que precisa ser comprado

## ⏰ Controle de validade dos insumos
- [ ] Destacar insumos com validade próxima (ex: < 7 dias)
- [ ] Criar endpoint para listar insumos vencidos ou quase vencendo
- [ ] (Opcional) Criar alerta automático ou relatório

## 🔗 API REST
- [ ] Implementar endpoints REST para todas as entidades
- [ ] Garantir estrutura RESTful (rotas, métodos, status codes)
- [ ] Documentar com OpenAPI (FastAPI faz isso por padrão em `/docs`)

## 🧪 Testes automatizados
- [ ] Criar testes com `pytest` para:
  - [ ] Cadastro e consulta de insumos
  - [ ] Cadastro e uso de receitas
  - [ ] Planejamento e cálculo de produção
  - [ ] Comparação de estoque
  - [ ] Geração da lista de compras
  - [ ] Validade de insumos

