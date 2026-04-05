# PRD — Padrão de Desenvolvimento de Web Apps Single-File (HTML+JS+CSS)

## 1. Visão Geral do Produto

Este documento define o **padrão obrigatório** para a criação de aplicativos web (web apps) do ecossistema **Perícias Câmara / Veridicus I.A.** Todos os web apps devem ser entregues em **um único arquivo `.html`** contendo HTML, CSS e JavaScript embutidos, garantindo portabilidade total — basta abrir o arquivo em qualquer navegador, sem servidor, sem dependências externas.

---

## 2. Objetivos

- **Portabilidade absoluta:** um único arquivo `.html` que funciona offline em qualquer computador.
- **Padronização visual e funcional:** todos os web apps seguem o mesmo layout, identidade e conjunto mínimo de funcionalidades.
- **Rastreabilidade de versão:** cada build possui versionamento semântico visível na interface.
- **Exportação profissional:** relatórios em LaTeX, CSV e cópia para área de transferência.
- **Contato facilitado:** links permanentes para LinkedIn, e-mail e site institucional.

---

## 3. Requisitos Obrigatórios

### 3.1 Arquivo Único

- Todo o código HTML, CSS e JavaScript deve residir em **um só arquivo `.html`**.
- Nenhuma dependência externa (CDN, framework remoto) é permitida — tudo inline ou embutido.
- O arquivo deve ser nomeado seguindo o padrão: `app-nome-do-projeto-vX.Y.Z.html`.

### 3.2 Versionamento Semântico

- Utilizar o padrão **SemVer** (`MAJOR.MINOR.PATCH`).
- A versão atual deve ser exibida de forma visível no **rodapé** e/ou **cabeçalho** do web app (ex.: `v1.0.0`).
- Manter um **changelog resumido** dentro do próprio arquivo (comentário HTML ou seção colapsável "Histórico de Versões").
- A cada versão finalizada, gerar um novo arquivo com o número de versão atualizado no nome.

### 3.3 Botões de Contato (Fixos no Rodapé ou Barra Superior)

Todos os web apps devem exibir os seguintes botões/links de contato:

| **Canal** | **URL / Endereço** | **Ícone sugerido** |
| --- | --- | --- |
| LinkedIn | [https://linkedin.com/in/gcamara](https://linkedin.com/in/gcamara) | 🔗 |
| E-mail | [contatos@editoraviva.art.br](mailto:contatos@editoraviva.art.br) | ✉️ |
| Site | [https://periciascamara.editoraviva.art.br](https://periciascamara.editoraviva.art.br) | 🌐 |
- Os botões devem abrir em nova aba (`target="_blank"`).
- O e-mail deve usar `mailto:`.

---

## 4. Funcionalidades Obrigatórias

### 4.1 Cadastro do Usuário (Avaliado / Paciente)

Seção de formulário com no mínimo:

- Nome completo
- Data de nascimento
- CPF ou documento de identificação
- Telefone / e-mail
- Campos adicionais conforme o contexto do questionário ou avaliação

### 4.2 Cadastro do Aplicador (Perito / Profissional)

Seção de formulário com no mínimo:

- Nome completo do aplicador
- CRM / registro profissional
- Instituição / empresa
- Data e local da aplicação

### 4.3 Área de Avaliação / Questionário

- Layout funcional e responsivo para preenchimento dos itens de avaliação.
- Validação de campos obrigatórios antes de salvar.
- Armazenamento local dos registros via `localStorage` (persistência entre sessões no mesmo navegador).

### 4.4 Botão — Gerar Relatório LaTeX

- Gera o relatório completo do registro selecionado em formato **LaTeX** (`.tex`).
- Faz download automático do arquivo.
- Exibe `alert()` confirmando: *"Relatório LaTeX gerado com sucesso!"*

### 4.5 Botão — Exportar CSV

- Exporta todos os registros (ou o registro selecionado) em formato **CSV**.
- Faz download automático do arquivo.
- Exibe `alert()` confirmando: *"Arquivo CSV exportado com sucesso!"*

### 4.6 Botão — Copiar para Área de Transferência

- Copia toda a avaliação/registro atual para a **área de transferência** em formato texto estruturado.
- Exibe `alert()` confirmando: *"Avaliação copiada para a área de transferência!"*

### 4.7 Botão — Simular Dados

- Preenche automaticamente todos os campos do formulário com **dados fictícios realistas** para fins de teste e demonstração.
- Exibe `alert()` confirmando: *"Dados simulados inseridos com sucesso!"*

### 4.8 Botão — Apagar Todos os Dados

- Antes de executar, exibe `confirm()`: *"Tem certeza que deseja apagar TODOS os registros? Esta ação é irreversível."*
- Se confirmado, limpa `localStorage` e reseta todos os campos do formulário.
- Exibe `alert()` confirmando: *"Todos os dados foram apagados com sucesso."*

---

## 5. Requisitos de Interface (UI/UX)

### 5.1 Layout Geral

- Design **responsivo** (mobile-first recomendado, mas funcional em desktop).
- Paleta de cores consistente (sugestão: tons de azul-marinho `#1a237e`, branco `#ffffff`, cinza claro `#f5f5f5`, destaque dourado `#ffc107`).
- Tipografia legível: `font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif`.
- Tamanho mínimo de fonte para campos: `14px`.

### 5.2 Estrutura da Página

1. **Header** — Logo/título do app + versão + botões de contato.
2. **Seção Cadastro do Aplicador** — colapsável.
3. **Seção Cadastro do Usuário** — colapsável.
4. **Seção de Avaliação / Questionário** — área principal.
5. **Barra de Ações** — botões: Salvar, Gerar LaTeX, Exportar CSV, Copiar Clipboard, Simular Dados, Apagar Tudo.
6. **Tabela/Lista de Registros Salvos** — visualização dos registros em `localStorage`.
7. **Footer** — versão, créditos, botões de contato.

### 5.3 Botões

- Botões com **ícones + texto** descritivo.
- Cores diferenciadas por ação:
    - 🟢 Salvar / Gerar → verde
    - 🔵 Exportar / Copiar → azul
    - 🟡 Simular → amarelo/dourado
    - 🔴 Apagar → vermelho
- Feedback visual (hover, disabled state).

---

## 6. Estrutura de Código Recomendada

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Nome do App — vX.Y.Z</title>
  <style>
    /\* ══════ CSS COMPLETO AQUI ══════ \*/
  </style>
</head>
<body>

  <!-- HEADER -->
  <!-- SEÇÃO CADASTRO APLICADOR -->
  <!-- SEÇÃO CADASTRO USUÁRIO -->
  <!-- SEÇÃO AVALIAÇÃO -->
  <!-- BARRA DE AÇÕES -->
  <!-- TABELA DE REGISTROS -->
  <!-- FOOTER -->

  <script>
    /\* ══════ JAVASCRIPT COMPLETO AQUI ══════ \*/
    const APP_VERSION = 'X.Y.Z';

    // Funções obrigatórias:
    // salvarRegistro()
    // gerarRelatorioLatex()
    // exportarCSV()
    // copiarParaClipboard()
    // simularDados()
    // apagarTodosDados()
  </script>
</body>
</html>
```

---

## 7. Template LaTeX de Saída (Exemplo Mínimo)

```latex
\\documentclass[12pt,a4paper]{article}
\\usepackage[utf8]{inputenc}
\\usepackage[brazil]{babel}
\\usepackage{geometry}
\\geometry{margin=2.5cm}

\\title{Relatório de Avaliação — [Nome do App]}
\\author{[Nome do Aplicador] — [Registro Profissional]}
\\date{[Data da Aplicação]}

\\begin{document}
\\maketitle

\\section{Dados do Avaliado}
\\begin{itemize}
  \\item Nome: [nome]
  \\item Data de Nascimento: [data]
  \\item Documento: [cpf]
\\end{itemize}

\\section{Resultado da Avaliação}
% Preencher dinamicamente com os dados do registro

\\end{document}
```

---

## 8. Checklist de Entrega (Definition of Done)

- [ ]  Arquivo único `.html` — sem dependências externas
- [ ]  Versão visível na interface (header e/ou footer)
- [ ]  Nome do arquivo segue o padrão `app-nome-vX.Y.Z.html`
- [ ]  Cadastro do Usuário funcional
- [ ]  Cadastro do Aplicador funcional
- [ ]  Botões de contato (LinkedIn, e-mail, site) presentes e funcionais
- [ ]  Botão Gerar LaTeX — download + alert de confirmação
- [ ]  Botão Exportar CSV — download + alert de confirmação
- [ ]  Botão Copiar para Clipboard — cópia + alert de confirmação
- [ ]  Botão Simular Dados — preenchimento automático + alert
- [ ]  Botão Apagar Todos os Dados — confirm + limpeza + alert
- [ ]  Layout responsivo e funcional em Chrome, Firefox, Edge e Safari
- [ ]  Dados persistidos em localStorage
- [ ]  Changelog / histórico de versão incluído no arquivo

---

## 9. Observações Finais

- Este PRD deve ser **anexado ou referenciado** em todo prompt de geração de novo web app.
- Qualquer novo requisito deve ser incorporado ao PRD antes de iniciar o desenvolvimento.
- A versão deste PRD é **v1.0.0** — 5 de abril de 2026.

---

*Documento elaborado pelo sistema Veridicus I.A. — Perícias Câmara.*