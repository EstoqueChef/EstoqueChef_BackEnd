
# ✅ TODO - Sistema de Gestão de Estoque e Receitas (Backend)

## 🧩 Funcionalidades Detalhadas

### 📦 Estoque e Insumos
- [ ] **CRUD de Insumos**
  - `POST /insumos/` - Criar novo insumo
  - `GET /insumos/` - Listar insumos (com filtros)
  - `GET /insumos/{id}` - Buscar insumo por ID
  - `PUT /insumos/{id}` - Atualizar insumo
  - `DELETE /insumos/{id}` - Remover insumo

- [ ] **Filtros e Ordenações**
  - Filtro por nome (`?nome=arroz`)
  - Filtro por validade próxima (`?validade_proxima=true`)
  - Ordenar por validade (`?ordenar_por=validade`)

- [ ] **Atualização Manual de Quantidade**
  - `PATCH /insumos/{id}/atualizar_quantidade/` - Incrementar ou decrementar quantidade

---

### 🍲 Receitas
- [ ] **CRUD de Receitas**
  - `POST /receitas/` - Criar receita
  - `GET /receitas/` - Listar receitas
  - `GET /receitas/{id}` - Detalhar receita
  - `PUT /receitas/{id}` - Atualizar receita
  - `DELETE /receitas/{id}` - Remover receita

- [ ] **Relacionar Insumos com Receita**
  - `POST /receitas/{id}/insumos/` - Adicionar insumo e quantidade à receita
  - `GET /receitas/{id}/insumos/` - Listar insumos da receita
  - `DELETE /receitas/{id}/insumos/{insumo_id}` - Remover insumo de receita

---

### 🧾 Planejamento de Produção
- [ ] **Planejar Produção**
  - `POST /planejamentos/` - Criar planejamento (lista de receitas + quantidades)
  - `GET /planejamentos/` - Listar planejamentos
  - `GET /planejamentos/{id}` - Detalhar planejamento

- [ ] **Cálculo Automático de Insumos**
  - Backend calcula total de insumos necessários baseado nas receitas e quantidades
  - Endpoint interno ou embutido no planejamento

- [ ] **Comparar com Estoque**
  - `GET /planejamentos/{id}/comparar_estoque/` - Ver insumos disponíveis x necessários

---

### 🛒 Lista de Compras
- [ ] **Geração da Lista de Compras**
  - `GET /planejamentos/{id}/lista_compras/` - Gera lista de insumos faltantes
  - `POST /lista_compras/` - (opcional) Persistir lista de compras
  - `GET /lista_compras/` - Listar listas geradas
  - `DELETE /lista_compras/{id}` - Remover lista

---

### ⏰ Validade de Insumos
- [ ] **Insumos com Validade Próxima**
  - `GET /insumos/validade_proxima/` - Listar insumos com validade em até 7 dias

- [ ] **Insumos Vencidos**
  - `GET /insumos/vencidos/` - Listar insumos com validade anterior à data atual

- [ ] (Futuro) **Alertas Automáticos**
  - Tarefa agendada (FastAPI + Celery ou apscheduler)

---

### 🔗 API RESTful
- Todas as rotas seguem o padrão RESTful
- `OpenAPI docs` disponível em `/docs` e `/redoc` via FastAPI

---

### 🧪 Testes Automatizados
- [ ] Usar `pytest` e `httpx` (ou `pytest-asyncio` se async)
- Testes cobrindo:
  - [ ] CRUD de insumos
  - [ ] Validade (vencidos/próximos)
  - [ ] CRUD de receitas e vínculo com insumos
  - [ ] Planejamento de produção e cálculos
  - [ ] Lista de compras gerada corretamente

---

## 🗃️ Modelos Principais

### `Insumo`
- id: int
- nome: str
- unidade: str (kg, g, L, un)
- quantidade_disponivel: float
- data_validade: date (opcional)

### `Receita`
- id: int
- nome: str
- descricao: str

### `ReceitaInsumo` (pivot table)
- receita_id → Receita
- insumo_id → Insumo
- quantidade_utilizada: float

### `PlanejamentoProducao`
- id: int
- data: date
- receitas: list[dict] (receita_id, quantidade_desejada)

### `ListaCompra`
- planejamento_id → PlanejamentoProducao
- insumo_id → Insumo
- quantidade_faltante: float

---

## 📄 Licença
Projeto de código aberto. Sinta-se à vontade para contribuir!
