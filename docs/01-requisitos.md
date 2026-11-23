# 1. Documento de Requisitos – SmartStock

## 1.1 Objetivo do sistema
Disponibilizar uma plataforma web que auxilie empresas no gerenciamento de seus estoques, permitindo o controle de produtos, movimentações, relatórios e indicadores operacionais, com integração futura com Inteligência Artificial para automatizar processos e apoiar a tomada de decisão.

## 1.2 Problema que será resolvido
Muitas empresas controlam o estoque em planilhas soltas ou de forma manual. Isso gera:
- Falta de visibilidade em tempo real dos níveis de estoque;
- Rupturas (produto em falta) e excesso de compras;
- Dificuldade em rastrear entradas e saídas;
- Ausência de alertas de reposição e de relatórios gerenciais confiáveis.

O SmartStock centraliza essas informações e antecipa problemas por meio de alertas automáticos.

## 1.3 Público-alvo
- **Gestores e donos de pequenas e médias empresas** (comércio, distribuidoras, varejo) que precisam de visão geral do estoque.
- **Responsáveis por estoque e almoxarifado**, que registram entradas e saídas no dia a dia.
- **Equipe de compras**, que precisa saber quando e o que repor.

## 1.4 Funcionalidades do sistema

### Funcionalidades mínimas
| ID | Funcionalidade | Descrição |
|---|---|---|
| RF01 | Login | Autenticação de usuários por e-mail e senha. |
| RF02 | Cadastro de produtos | Cadastrar produto com nome, categoria, quantidade, estoque mínimo, preço e data de cadastro. |
| RF03 | Consulta de produtos | Listar e buscar produtos por nome, ID ou categoria. |
| RF04 | Atualização de produtos | Editar os dados de um produto existente. |
| RF05 | Exclusão de produtos | Remover produto cadastrado (com confirmação). |
| RF06 | Controle de entrada | Registrar entrada de estoque, atualizando a quantidade. |
| RF07 | Controle de saída | Registrar saída de estoque, atualizando a quantidade. |
| RF08 | Dashboard | Exibir indicadores: total de produtos, itens abaixo do mínimo, entradas e saídas do mês. |
| RF09 | Relatórios de estoque | Gerar relatórios de posição de estoque e movimentações por período. |
| RF10 | Controle de estoque mínimo | Definir estoque mínimo por produto e destacar itens abaixo dele. |
| RF11 | Alertas de reposição | Notificar quando um produto atingir ou ficar abaixo do estoque mínimo. |
| RF12 | Configurações | Gerenciar dados da empresa, notificações e integrações. |
| RF13 | Integração com IA (futura) | Permitir consultas em linguagem natural e automações via agente de IA. |

### Requisitos não funcionais
| ID | Requisito |
|---|---|
| RNF01 | Interface responsiva, utilizável em desktop e tablet. |
| RNF02 | Senhas armazenadas com hash seguro (bcrypt). |
| RNF03 | Acesso restrito às telas por autenticação (JWT). |
| RNF04 | Tempo de resposta da listagem de produtos inferior a 2 segundos. |
| RNF05 | Seguir boas práticas de UX/UI: hierarquia visual, feedback de ações e mensagens de erro claras. |
| RNF06 | Código versionado no GitHub com documentação organizada. |

## 1.5 Benefícios da solução
- **Visibilidade:** saldo de estoque atualizado em tempo real.
- **Redução de rupturas:** alertas antes que o produto acabe.
- **Menos capital parado:** compras baseadas em dados, evitando excesso.
- **Rastreabilidade:** histórico completo de entradas e saídas.
- **Decisão mais rápida:** dashboard e relatórios prontos para consulta.
- **Escalabilidade:** base preparada para integrar IA e automações (N8N).
