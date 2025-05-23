# Documentação do Sistema

## I. Visão Geral do Sistema
### Objetivo:
O sistema **MSafe** foi idealizado para modernizar o processo de controle de vendas, estoque e cadastro de clientes em lojas de materiais de construção. Substitui cadernos físicos por um sistema digital simples, permitindo que os funcionários façam registros, consultas e atualizações de maneira mais eficiente, reduzindo erros humanos e aumentando a produtividade.

---

## II. Requisitos do Sistema
### Requisitos Funcionais (RF)
- **RF01:** O sistema deve permitir o cadastro de clientes com nome, telefone e CPF.
- **RF02:** O sistema deve permitir o cadastro de materiais com nome, preço e quantidade em estoque.
- **RF03:** O sistema deve permitir o registro de vendas vinculadas a clientes e materiais.
- **RF04:** O sistema deve atualizar o estoque automaticamente após cada venda.
- **RF05:** O sistema deve permitir consultas rápidas de clientes pelo nome ou CPF.
- **RF06:** O sistema deve permitir a geração de relatórios de vendas e estoque.
- **RF07:** O sistema deve ter autenticação por e-mail e senha para acesso administrativo.
- **RF08:** O sistema deve permitir a recuperação de senha via e-mail.

### Requisitos Não Funcionais (RNF)
- **RNF01:** O sistema deve ser responsivo e funcionar bem em computadores e tablets.
- **RNF02:** As buscas devem retornar resultados em até 2 segundos.
- **RNF03:** As senhas dos usuários devem ser armazenadas com criptografia segura.
- **RNF04:** O sistema deve funcionar offline, com banco de dados local (SQLite).

---

# Casos de Uso — Sistema MSafe

## I. Acesso e Navegação Inicial
### Caso de Uso 1: Acesso Inicial
**Ator:** Funcionário  
**Descrição:** O sistema apresenta as principais funcionalidades após o login.  
**Fluxo Principal:**
1. O usuário acessa a tela de login.
2. O sistema valida as credenciais.
3. O sistema apresenta o menu principal com acesso a cadastro, vendas e relatórios.  
**Pós-condição:** Usuário autenticado pode operar o sistema.

---

## II. Operações com Cliente e Materiais
### Caso de Uso 2: Cadastro de Cliente
**Ator:** Funcionário  
**Descrição:** Cadastro de novos clientes.  
**Fluxo Principal:**
1. O usuário acessa "Cadastro de Cliente".
2. Preenche os dados (nome, telefone, CPF).
3. O sistema valida o CPF e salva o cliente.
**Pós-condição:** Cliente salvo na base de dados.

### Caso de Uso 3: Cadastro de Material
**Ator:** Funcionário  
**Descrição:** Registro de materiais disponíveis para venda.  
**Fluxo Principal:**
1. O usuário acessa "Cadastro de Material".
2. Preenche os dados do material.
3. O sistema salva no estoque.
**Pós-condição:** Material salvo no banco de dados.

### Caso de Uso 4: Registro de Venda
**Ator:** Funcionário  
**Descrição:** Registro de uma venda realizada.  
**Pré-condição:** Cliente e materiais cadastrados.  
**Fluxo Principal:**
1. O usuário seleciona o cliente.
2. Escolhe materiais e quantidades.
3. O sistema calcula o total e atualiza o estoque.
**Pós-condição:** Venda registrada, estoque atualizado.

---

## III. Autenticação e Recuperação
### Caso de Uso 5: Login
**Ator:** Funcionário  
**Descrição:** Acesso ao sistema.  
**Fluxo Principal:**
1. Usuário informa e-mail e senha.
2. O sistema valida as credenciais e permite o acesso.

### Caso de Uso 6: Recuperar Senha
**Ator:** Funcionário  
**Descrição:** Recuperar acesso ao sistema.  
**Fluxo Principal:**
1. Usuário informa e-mail na tela de recuperação.
2. O sistema envia link de redefinição.
3. Usuário cria nova senha com validação.

---

## IV. Arquitetura do Sistema
### Componentes Principais:
- **Frontend:** HTML, CSS, JavaScript (Vanilla ou framework leve)
- **Backend:** Node.js com Express
- **Banco de Dados:** SQLite local
- **Autenticação:** JWT (JSON Web Token)

### Fluxo de Dados:
1. O usuário realiza login.
2. Requisição é enviada ao backend para validação.
3. O backend interage com o banco e retorna os dados.
4. O frontend apresenta os dados formatados ao usuário.

---

## V. Estrutura do Banco de Dados
### Tabelas Principais:
- **clientes** (id, nome, telefone, cpf)
- **materiais** (id, nome, preco, quantidade)
- **vendas** (id, id_cliente, data, total)
- **itens_venda** (id_venda, id_material, quantidade, preco_unitario)

**Relacionamentos:**
- 1 cliente → N vendas  
- 1 venda → N itens de venda

---

## VI. Regras de Negócio
- **RN01:** Não pode haver dois clientes com o mesmo CPF.
- **RN02:** Não pode ser registrada uma venda com material sem estoque.
- **RN03:** O sistema atualiza o estoque automaticamente após uma venda.

---

## VII. Tecnologias Utilizadas
- **Frontend:** HTML, CSS, JavaScript
- **Backend:** Node.js, Express
- **Banco de Dados:** SQLite
- **Autenticação:** JWT

---

## VIII. Testes
- **Testes Unitários:** Validação de CPF, cálculo de total da venda
- **Testes de Integração:** Cadastro completo de cliente, venda e atualização do estoque
- **Testes Funcionais:** Usuário conseguindo realizar uma venda completa com cliente e materiais cadastrados

---

## IX. Plano de Lançamento
1. Desenvolvimento do MVP com cadastro e vendas
2. Testes com usuários reais em loja parceira
3. Ajustes com base no feedback
4. Lançamento beta
5. Correções finais e lançamento oficial
