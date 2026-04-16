# 🛡️ Global Cyber Summit - Anti-Bot Security System

Este repositório contém a solução técnica para o **Checkpoint 2** da disciplina *Mastering Relational and Non Relational Databases*. O objetivo é proteger o processo de inscrição do Global Cyber Summit contra ataques massivos de botnets.

---

## 👥 Integrantes
* **Raphael Gomes Mancera** - RM562279
* **Guilherme De Andrade Martini** - RM566087
* **Turma:** 2TDSPX

---

## 🚀 O Desafio
Atuar como Engenheiro de Segurança do SOC para identificar e punir registros fraudulentos. A solução foca em:
1. **Identificação:** Localizar e-mails malformados ou de domínios temporários (`fake.com`, `temp-mail`).
2. **Punição:** Redução severa de **15 pontos** no `TRUST_SCORE`.
3. **Auditoria:** Registro obrigatório de todas as ações de cancelamento para compliance.

---

## 🛠️ Arquitetura da Solução

### 1. Banco de Dados Relacional (Oracle SQL)
Utilizamos SQL para garantir a consistência **ACID** nas transações de punição e auditoria. 
- **Tabelas:** `INSCRICOES` e `LOG_AUDITORIA`.
- **Lógica:** Implementação de queries de varredura em tempo real que cruzam dados de status `PENDING` com padrões de e-mail suspeitos.

### 2. Banco de Dados Não Relacional (Proposta NoSQL)
Para garantir a escalabilidade exigida por um evento global, propomos o uso de **MongoDB** para o armazenamento dos logs de auditoria.
* **Por que NoSQL?** Logs de segurança geram grande volume de dados não estruturados. O MongoDB permite escrita de alta performance e buscas flexíveis por padrões de ataque sem onerar o banco transacional principal.

### 3. Frontend (Deploy Vercel)
Desenvolvemos um Dashboard de Segurança que simula o acionamento da força-tarefa de emergência, permitindo ao operador do SOC iniciar a varredura anti-bot com um clique.

---

## 📂 Estrutura do Repositório
* `/database`: Contém o script `setup.sql` com a criação de tabelas, sequences e as queries de negócio.
* `/app`: Código fonte da interface enviada para o Vercel.
* `README.md`: Documentação do projeto.

---

## 🔧 Como Executar
1. Execute o script contido em `database.sql` no seu ambiente Oracle SQL.
2. Certifique-se de criar a `SEQUENCE SEQ_LOG` para o funcionamento dos IDs de auditoria.
3. Para visualizar a interface, acesse o link do deploy no Vercel.

---

## 💻 Tecnologias
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![Vercel](https://img.shields.io/badge/vercel-%23000000.svg?style=for-the-badge&logo=vercel&logoColor=white)
