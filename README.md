# Desafio Técnico — Radar Inteligente de Fornecedores

## Contexto

A área de Compras recebe listas de CNPJs e consulta cada empresa manualmente para verificar seus dados cadastrais. O processo toma tempo, gera retrabalho e dificulta uma visão consolidada dos fornecedores.

## Objetivo

Em **6 a 8 horas**, crie uma solução inicial que automatize parte dessa consulta usando dados públicos da [BrasilAPI](https://brasilapi.com.br/docs). O foco é demonstrar suas decisões e entregar algo simples, executável e bem explicado. Não é necessário criar uma solução pronta para produção.

Você pode escolher linguagem, armazenamento, interface e abordagem de inteligência artificial. Não é necessário usar Docker, geração aumentada por recuperação (RAG) ou criar um painel sofisticado.

## Escopo obrigatório

### 1. Entrada e processamento

Receba um arquivo CSV com a coluna `cnpj` obrigatória e a coluna `categoria_informada` opcional. Use uma amostra pequena com pelo menos:

- 5 CNPJs válidos;
- 1 CNPJ duplicado;
- 2 registros inválidos ou não encontrados.

O processamento deve:

- Padronizar e validar os CNPJs;
- Consultar a BrasilAPI e registrar data e hora da consulta;
- Tratar duplicidades, registros não encontrados e erros temporários;
- Gerar uma saída consolidada que não duplique resultados quando o processo for executado novamente.

Após remover a formatação, considere CNPJs com 14 caracteres alfanuméricos. Consulte somente os dados da amostra. Para que a demonstração e os testes não dependam da disponibilidade da API, você pode usar respostas salvas ou simuladas, desde que isso fique documentado.

### 2. Resultado para Compras

Apresente uma tabela ou relatório simples com:

- CNPJ informado e CNPJ padronizado;
- Razão social, situação cadastral, data de abertura e atividade econômica principal;
- Município, estado e data da consulta;
- Situação do processamento e motivo do erro, quando houver.

Inclua um resumo com total de entradas, empresas processadas com sucesso, duplicidades, erros ou pendências e uma lista dos registros que precisam de revisão. Uma distribuição por situação cadastral ou estado é suficiente.

Armazene somente os dados necessários. Não inclua informações pessoais de sócios sem justificar a necessidade.

### 3. Uso de inteligência artificial

Implemente uma função simples que ajude a consultar ou resumir os dados, por exemplo: “Quantos fornecedores foram processados?” ou “Quais registros precisam de revisão?”.

As respostas devem usar a base processada, indicar quando faltarem dados e não aprovar nem reprovar fornecedores. Se usar uma chave de serviço, inclua um exemplo de configuração e instruções para configurá-la; nunca inclua senhas ou chaves no repositório.

### 4. Estimativa de benefício

Use este cenário mensal:

- 500 CNPJs;
- 8 minutos de consulta manual por CNPJ;
- 10% dos registros geram 5 minutos adicionais de retrabalho;
- Custo do analista: R$ 70 por hora;
- Coordenação: 3 horas para consolidar resultados, a R$ 110 por hora;
- Investimento inicial estimado: R$ 15.000.

Considere o retrabalho como tempo adicional. Com essa premissa, o processo atual representa **73,8 horas e R$ 5.288,33 por mês**.

Estime o custo mensal futuro, incluindo o trabalho que continuará sendo feito por pessoas e os custos de infraestrutura e inteligência artificial. Apresente a economia mensal, o retorno sobre o investimento em 12 meses e o prazo de retorno. Identifique suas premissas.

Fórmulas:

- Custo futuro mensal = custo do trabalho restante + infraestrutura e inteligência artificial;
- Economia mensal = R$ 5.288,33 − custo futuro mensal;
- Benefício líquido em 12 meses = (economia mensal × 12) − R$ 15.000;
- Retorno sobre o investimento = benefício líquido ÷ R$ 15.000 × 100;
- Prazo de retorno = R$ 15.000 ÷ economia mensal, se a economia for positiva.

## O que entregar

- Código e arquivo de exemplo;
- Instruções para instalar e executar;
- Uma amostra do resultado;
- Testes ou verificações básicas;
- Decisões técnicas, premissas dos cálculos, limitações e próximos passos.

Prepare uma demonstração de até **5 minutos** para uma pessoa da área de Compras. Depois, conversaremos por até **10 minutos** sobre suas decisões. Se algo ficar incompleto, explique o que faltou e como priorizaria a próxima etapa.

O uso de ferramentas de inteligência artificial durante o desenvolvimento é permitido. Conte quais ferramentas usou, como validou os resultados e quais decisões tomou.

## Como será avaliado

Cada dimensão recebe nota de 0 a 2: **0** = não demonstrado; **1** = parcial; **2** = claro e bem justificado.

| Dimensão | O que vamos observar |
|---|---|
| Processamento e dados | Padronização, qualidade, tratamento de erros e reexecução |
| Resultado para Compras | Clareza das informações e identificação de pendências |
| Inteligência artificial responsável | Respostas úteis, baseadas nos dados e sem inventar informações |
| Benefício para o negócio | Premissas e cálculos de custo, economia e retorno |
| Execução e comunicação | Projeto executável, decisões explicadas e limitações reconhecidas |

Não serão avaliadas a linguagem, a escolha do fornecedor de inteligência artificial ou a ferramenta de visualização. A disponibilidade da BrasilAPI no dia da apresentação também não será avaliada.
