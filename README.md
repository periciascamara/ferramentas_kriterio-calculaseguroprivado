🏥 Calculadora de Invalidez (IAIF e SUSEP)
> **Ferramenta web para cálculo de indenização por invalidez permanente com base nas tabelas IAIF e SUSEP.**  
> Desenvolvida no ecossistema **Perícias Câmara / Veridicus I.A.**  
> 🤖 *Este web app foi desenvolvido na plataforma [claude.ai](https://claude.ai)*
---
📋 Sobre o Projeto
Este web app faz parte do ecossistema de ferramentas Kriterio para médicos peritos judiciais. Ele permite calcular de forma precisa e padronizada o valor de indenização por invalidez permanente, com base nas tabelas **IAIF** e **SUSEP**.

O aplicativo é entregue como um único arquivo `.html` — sem servidor, sem dependências externas, funciona diretamente no navegador em qualquer computador.

> **Versão atual:** **v1.3.0**
---
🗂️ Estrutura do Repositório
```
ferramentas_kriterio-calculaseguroprivado/
├── index.html                          → Web app principal (IAIF + SUSEP)
└── seguroprivado/
    ├── index.html                      → Versão alternativa do web app
    ├── prd.md                          → Documento de Requisitos do Produto
    ├── Calculadora Interativa de Indenização por Invalidez com Tabela SUSEP.md
    ├── Diretrizes de Indenização por Invalidez Permanente da SUSEP.md
    └── Guia de Implementação do Algoritmo de Avaliação de Invalidez IAIF.md
```
---
✅ Funcionalidades
Funcionalidade	Descrição
📝 Cadastro do Avaliado	Nome, data de nascimento, CPF, contato
👨‍⚕️ Cadastro do Aplicador	Nome do perito, CRM, instituição, data/local
🧮 Avaliação IAIF + SUSEP	Cálculo completo de invalidez com tabela oficial
👁️ Avaliar perda da acuidade visual	Registro e classificação de perda visual como parte da avaliação pericial
💪 Sinalizar alteração específica do ombro	Campo dedicado para marcar e descrever alterações específicas do ombro (ex.: limitação, dor, instabilidade)
📄 Gerar Relatório LaTeX	Download automático do relatório `.tex`
📊 Exportar CSV	Exportação de todos os registros
📋 Copiar para Clipboard	Cópia da avaliação em texto estruturado
🎲 Simular Dados	Preenchimento automático com dados fictícios para teste
🗑️ Apagar Todos os Dados	Limpeza completa com confirmação
💾 Persistência Local	Dados salvos via `localStorage` no navegador
---
🎨 Padrão Visual
Paleta: azul-marinho `#1a237e` · dourado `#ffc107` · fundo escuro `#0f172a`
Tipografia: `Segoe UI`, Tahoma, Geneva, Verdana — mínimo `14px`
Layout: responsivo (mobile-first), glassmorphism
Versionamento: SemVer visível no header e footer (`vMAJOR.MINOR.PATCH`)
---
🧾 Changelog (resumo)
- **v1.3.0 (23 abr 2026)**
  - Inclusão da funcionalidade de **avaliar perda da acuidade visual**.
  - Inclusão de **sinalização de alteração específica do ombro**.
---
🔗 Contato
Canal	Link
🔗 LinkedIn	linkedin.com/in/gcamara
✉️ E-mail	contatos@editoraviva.art.br
🌐 Site	periciascamara.editoraviva.art.br
---
📐 Padrão de Desenvolvimento (PRD)
Este projeto segue o Padrão de Desenvolvimento de Web Apps Single-File do ecossistema Perícias Câmara / Veridicus I.A. Os principais requisitos são:

Arquivo Único
Todo HTML, CSS e JavaScript em um único arquivo `.html`
Sem dependências externas — funciona 100% offline
Nome de arquivo segue: `app-nome-do-projeto-vX.Y.Z.html`

Versionamento Semântico
Padrão SemVer (`MAJOR.MINOR.PATCH`)
Versão visível na interface (header e/ou footer)
Changelog resumido incluído no próprio arquivo

Botões de Ação (Barra de Ações)
🟢 Verde — Salvar / Gerar
🔵 Azul — Exportar / Copiar
🟡 Dourado — Simular Dados
🔴 Vermelho — Apagar Tudo

Estrutura Obrigatória da Página
Header (logo + versão + contatos)
Seção Cadastro do Aplicador (colapsável)
Seção Cadastro do Avaliado (colapsável)
Seção de Avaliação / Questionário
Barra de Ações
Tabela/Lista de Registros Salvos
Footer (versão + créditos + contatos)

Funções JavaScript Obrigatórias
```javascript
salvarRegistro()
gerarRelatorioLatex()
exportarCSV()
copiarParaClipboard()
simularDados()
apagarTodosDados()
```
---
☑️ Checklist de Entrega (Definition of Done)
[x] Arquivo único `.html` — sem dependências externas
[x] Versão visível na interface (header e/ou footer)
[x] Nome do arquivo segue o padrão `app-nome-vX.Y.Z.html`
[x] Cadastro do Usuário funcional
[x] Cadastro do Aplicador funcional
[x] Botões de contato (LinkedIn, e-mail, site) presentes e funcionais
[x] Botão Gerar LaTeX — download + alert de confirmação
[x] Botão Exportar CSV — download + alert de confirmação
[x] Botão Copiar para Clipboard — cópia + alert de confirmação
[x] Botão Simular Dados — preenchimento automático + alert
[x] Botão Apagar Todos os Dados — confirm + limpeza + alert
[x] Layout responsivo e funcional em Chrome, Firefox, Edge e Safari
[x] Dados persistidos em localStorage
[x] Changelog / histórico de versão incluído no arquivo
---
🚀 Como Usar
Baixe o arquivo `index.html`
Abra no seu navegador (Chrome, Firefox, Edge ou Safari)
Preencha os dados do aplicador e do avaliado
Calcule a invalidez com base na tabela SUSEP / algoritmo IAIF
Exporte o resultado em LaTeX, CSV ou copie para o clipboard
> Nenhuma instalação necessária. Funciona offline.
---
📄 Documentação Técnica
`prd.md` — Documento de Requisitos do Produto (v1.0.0 — 5 abr 2026)
`Calculadora Interativa de Indenização por Invalidez com Tabela SUSEP.md`
`Diretrizes de Indenização por Invalidez Permanente da SUSEP.md`
`Guia de Implementação do Algoritmo de Avaliação de Invalidez IAIF.md`
---
🤖 Desenvolvimento
Este web app foi desenvolvido na plataforma claude.ai — assistente de IA da Anthropic.
Documento elaborado pelo sistema Veridicus I.A. — Perícias Câmara.  
PRD versão v1.0.0 — 5 de abril de 2026.
