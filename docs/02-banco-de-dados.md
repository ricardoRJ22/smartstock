# 2. Modelagem do Banco de Dados – SmartStock

SGBD sugerido: **PostgreSQL**. Script completo em [schema.sql](schema.sql).

## 2.1 Tabela Produtos

| Campo | Tipo | Chave / Restrição | Descrição |
|---|---|---|---|
| id | SERIAL | PK | Identificador do produto |
| nome | VARCHAR(150) | NOT NULL | Nome do produto |
| categoria | VARCHAR(80) | NOT NULL | Categoria (ex.: Bebidas, Papelaria) |
| quantidade | INTEGER | NOT NULL, DEFAULT 0, CHECK >= 0 | Saldo atual em estoque |
| estoque_minimo | INTEGER | NOT NULL, DEFAULT 0, CHECK >= 0 | Quantidade mínima desejada |
| preco | NUMERIC(10,2) | NOT NULL, CHECK >= 0 | Preço unitário |
| data_cadastro | TIMESTAMP | NOT NULL, DEFAULT now() | Data de cadastro |

## 2.2 Tabela Movimentações

| Campo | Tipo | Chave / Restrição | Descrição |
|---|---|---|---|
| id | SERIAL | PK | Identificador da movimentação |
| produto_id | INTEGER | NOT NULL, FK → Produtos(id) | Produto movimentado |
| tipo | VARCHAR(7) | NOT NULL, CHECK IN ('ENTRADA','SAIDA') | Tipo da movimentação |
| quantidade | INTEGER | NOT NULL, CHECK > 0 | Quantidade movimentada |
| data | TIMESTAMP | NOT NULL, DEFAULT now() | Data/hora da movimentação |

## 2.3 Relacionamento

```
Produtos (1) ──────< (N) Movimentações
   id  ◄──────────────  produto_id
```

Um produto possui várias movimentações; cada movimentação pertence a exatamente um produto.

## 2.4 Regras de negócio
- Uma **ENTRADA** soma à `quantidade` do produto.
- Uma **SAÍDA** subtrai da `quantidade`; não pode deixar o saldo negativo.
- Exclusão de produto com movimentações deve ser bloqueada ou feita em modo lógico (campo `ativo`, a ser avaliado na Etapa 2 do Dia 8).
- Alerta de reposição é disparado quando `quantidade <= estoque_minimo`.
