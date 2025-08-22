### 3. Plataforma de Vendas de Produtos Artesanais
**Descrição:** Marketplace para venda de produtos artesanais.

**Requisitos Funcionais:**
1. Cadastro de vendedores e produtos.
2. Carrinho de compras.
3. Checkout e pagamento.
4. Avaliações de produtos.

**Requisitos Não Funcionais:**
- Suporte a múltiplos meios de pagamento.
- Design amigável e moderno.

**Histórias de Usuário:**
- **Como comprador**, quero adicionar produtos ao carrinho **para que** possa finalizar a compra.
  - **Critérios de Aceite:** Carrinho persistente; cálculos corretos de preço.

**Etapas/Sprints:**
- Sprint 1: Cadastro e listagem de produtos.
- Sprint 2: Carrinho e checkout.
- Sprint 3: Avaliações e melhorias.
------------------------------------------------------------------------

**Entidades:**

-   **Vendedor**
    -   `id` (PK)\
    -   `nome` (obrigatório)\
    -   `email` (único)\
    -   `telefone` (regex: `^\(\d{2}\)\s\d{4,5}-\d{4}$`)
-   **Produto**
    -   `id` (PK)\
    -   `vendedor_id` (FK → Vendedor)\
    -   `nome` (até 150 caracteres)\
    -   `descricao` (texto)\
    -   `preco` (decimal \> 0)\
    -   `estoque` (inteiro ≥ 0)
-   **Carrinho**
    -   `id` (PK)\
    -   `usuario_id` (FK)\
    -   `produto_id` (FK → Produto)\
    -   `quantidade` (inteiro ≥ 1, ≤ estoque disponível)
-   **Pedido**
    -   `id` (PK)\
    -   `usuario_id` (FK)\
    -   `total` (calculado)\
    -   `status` (enum: `PENDENTE`, `PAGO`, `CANCELADO`)
-   **Avaliacao**
    -   `id` (PK)\
    -   `produto_id` (FK → Produto)\
    -   `usuario_id` (FK)\
    -   `nota` (1 a 5)\
    -   `comentario` (opcional, até 500 caracteres)
