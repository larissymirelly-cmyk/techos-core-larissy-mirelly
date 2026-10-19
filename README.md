# TechOS Core - Sprint Express

## 1. USER STORIES (INVEST)
- **US01:** "Como técnico, quero abrir uma Ordem de Serviço para registrar um conserto."
  - **C.A.01:** Deve validar o ID do cliente.
  - **C.A.02:** O status inicial deve ser sempre 'ABERTA'.
- **US02:** "Como cliente, quero visualizar o status do meu equipamento."

## 2. REQUISITOS NÃO-FUNCIONAIS (RNF)
- **RNF01 (Segurança):** Sanitização de inputs contra XSS/OWASP no cadastro.
- **RNF02 (Desempenho):** Tempo de resposta na criação de chamados < 2s.

## 3. DIAGRAMA DE CLASSES (Mermaid)

```mermaid
classDiagram
    class Usuario {
        <<abstract>>
        #int id
        #string nome
        #string email
        +getId()
        +getNome()
        +getEmail()
    }

    class Cliente {
        -string telefone
        +getTelefone()
    }

    class Tecnico {
        -string especialidade
        +getEspecialidade()
    }

    class OrdemServico {
        -int id
        -Cliente cliente
        -Tecnico tecnico
        -string status
        -string descricao
        +getStatus()
    }

    Usuario <|-- Cliente
    Usuario <|-- Tecnico
    OrdemServico --> Cliente
    OrdemServico --> Tecnico
