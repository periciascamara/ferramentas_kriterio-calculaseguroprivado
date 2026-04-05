Fala, dev\! Para construir essa aplicação web, vamos estruturar o sistema dividindo a lógica em duas partes principais, que refletem exatamente os dois documentos oficiais do Instrumento de Avaliação de Invalidez Funcional (IAIF) 1-4. O nosso objetivo final com esse algoritmo é calcular uma pontuação máxima de 80 pontos, onde o gatilho para aprovar a Invalidez Funcional Permanente Total por Doença (IFPD) é atingir, no mínimo, **60 pontos** 3, 5\.  
Abaixo, apresento o passo a passo da modelagem de dados, sugestão de interface (UI) e a lógica de programação.

### Passo 1: Frontend \- Tabela de Relações Existenciais (Documento 1\)

Nesta primeira tela, o perito avaliará 3 atributos obrigatórios do paciente. Como o paciente só pode ser classificado em um único grau de gravidade por atributo, a interface ideal deve utilizar componentes de múltipla escolha mutuamente exclusivos, como **Radio Buttons** ou **Select Dropdowns**.  
**Interface Sugerida e Valores:**Você vai criar três grupos de *Radio Buttons*. Para cada atributo, o perito deve escolher um dos graus:

* **Relações do Segurado com o cotidiano** 6-9:  
* Value \= 0 (1º Grau): Mantém relações, deambula livremente, sai à rua sozinho 6, 8\.  
* Value \= 10 (2º Grau): Apresenta desorientação, necessita de auxílio à locomoção, comunica-se com dificuldade 6, 8\.  
* Value \= 20 (3º Grau): Retido ao lar, perda na mobilidade ou fala, não realiza atividades do cotidiano 7, 9\.  
* **Condições Clínicas e Estruturais do Segurado** 7, 9-12:  
* Value \= 0 (1º Grau): Hígido, livre movimentação, sem evidência de disfunção 7, 9\.  
* Value \= 10 (2º Grau): Disfunção secundária de doenças, depende de suporte médico constante (assistido) 10, 12\.  
* Value \= 20 (3º Grau): Quadro clínico avançado/instável, restrição ampla a esforços físicos, suporte médico mantido 11, 12\.  
* **Conectividade do Segurado com a vida** 2, 4, 13, 14:  
* Value \= 0 (1º Grau): Autossuficiência para vestir-se, higiene, asseio pessoal e alimentação 13, 14\.  
* Value \= 10 (2º Grau): Necessita de auxílio para trocar de roupa, banho e preparo/consumo de alimentos 13, 14\.  
* Value \= 20 (3º Grau): Necessita de auxílio total para higiene e não é capaz de realizar sozinho necessidades fisiológicas 2, 4\.

*Regra de Validação na UI:* Torne os três campos required. O sistema só deve permitir avançar se os três atributos forem pontuados 15, 16\.

### Passo 2: Frontend \- Tabela de Fatores de Risco e Morbidade (Documento 2\)

Na segunda etapa, avaliamos fatores agravantes. Como o paciente pode apresentar vários desses fatores simultaneamente, a interface ideal utiliza **Checkboxes**, mapeando cada fator para um valor booleano (true/false) 2, 4\.  
**Interface Sugerida e Valores:**Crie um formulário com 5 *Checkboxes*. Quando marcados, eles somam a seguinte pontuação:

1. Checkbox (Soma **2 pontos**): Idade interfere na morbidade e/ou IMC superior a 40 2, 17\.  
2. Checkbox (Soma **2 pontos**): Risco de sangramentos, rupturas ou ocorrências iminentes 17, 18\.  
3. Checkbox (Soma **4 pontos**): Existem mais de 2 fatores de risco e/ou associação de duas ou mais doenças crônicas em atividade 17, 18\.  
4. Checkbox (Soma **4 pontos**): Recidiva, progressão em doença tratada e/ou disfunção imunológica 17, 18\.  
5. Checkbox (Soma **8 pontos**): Risco de morte súbita, tratamento paliativo e/ou refratariedade terapêutica 17, 18\.

*Regra de Validação na UI:* Diferente do Passo 1, aqui os campos não são obrigatórios. O perito só marca o que for constatado no paciente 16, 19\.

### Passo 3: Backend \- O Algoritmo de Cálculo (Regra de Negócio)

No seu *controller* (usando JavaScript como exemplo), você receberá o *payload* do frontend e fará a consolidação. O algoritmo precisa somar os valores e verificar se a nota atinge o critério da SUSEP 3, 5\.  
function calcularIAIF(documento1, documento2) {  
    let pontuacaoTotal \= 0;

    // 1\. Processamento do Documento 1 (Radio Buttons \- Máximo 60 pontos)  
    // Certifique-se de que os valores chegam como inteiros (Number)  
    pontuacaoTotal \+= Number(documento1.relacoesCotidiano);  
    pontuacaoTotal \+= Number(documento1.condicoesClinicas);  
    pontuacaoTotal \+= Number(documento1.conectividadeVida);

    // 2\. Processamento do Documento 2 (Checkboxes \- Máximo 20 pontos)  
    if (documento2.idadeOuImcElevado) pontuacaoTotal \+= 2;  
    if (documento2.riscoSangramento) pontuacaoTotal \+= 2;  
    if (documento2.multiplosFatoresRisco) pontuacaoTotal \+= 4;  
    if (documento2.recidivaOuDisfuncao) pontuacaoTotal \+= 4;  
    if (documento2.morteSubitaOuPaliativo) pontuacaoTotal \+= 8;

    // 3\. Regra de Negócio Final (Aprovação \>= 60\)  
    const atingiuInvalidez \= pontuacaoTotal \>= 60;

    return {  
        pontuacaoFinal: pontuacaoTotal,  
        invalidezComprovada: atingiuInvalidez,  
        mensagem: atingiuInvalidez   
            ? "Status: Aprovado. O quadro clínico atingiu a pontuação mínima de 60 pontos, configurando Invalidez Funcional Permanente Total por Doença (IFPD)."   
            : "Status: Negado. A pontuação não atingiu o mínimo exigido de 60 pontos."  
    };  
}  
Implementando essa arquitetura e lógica, o seu aplicativo web estará perfeitamente alinhado com o Instrumento de Avaliação de Invalidez Funcional (IAIF) exigido pelas seguradoras 3, 5\.  
