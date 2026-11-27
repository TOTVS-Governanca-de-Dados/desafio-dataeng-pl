# Desafio Técnico — Engenharia de Dados e IA

## Radar Inteligente de Fornecedores

### Contexto

A área de Compras recebe mensalmente planilhas contendo CNPJs de possíveis fornecedores.

Atualmente, um analista consulta cada CNPJ manualmente, copia as informações cadastrais, identifica problemas e prepara um resumo para avaliação.

Esse processo é demorado, repetitivo, sujeito a erros e não oferece uma visão consolidada dos fornecedores.

## Objetivo

Desenvolver um MVP que utilize dados públicos de CNPJ, consultados por meio da [BrasilAPI](https://brasilapi.com.br/docs), para automatizar parte desse processo.

A solução deverá permitir que uma pessoa da área de Compras:

- Consulte uma lista de CNPJs;
- Identifique registros que precisam de atenção;
- Visualize informações consolidadas;
- Compreenda os dados sem depender de conhecimento técnico;
- Utilize IA para consultar ou interpretar as informações.

Você terá liberdade para escolher linguagem, arquitetura, armazenamento, interface e abordagem de IA.

## Entrada esperada

A solução deverá receber uma planilha CSV contendo, no mínimo:

```csv
cnpj,categoria_informada
```

Para a demonstração, utilize uma massa com:

- Pelo menos 10 CNPJs válidos;
- Pelo menos um CNPJ duplicado;
- Pelo menos dois registros inválidos ou inexistentes.

A coluna `categoria_informada` é opcional e pode representar a categoria pela qual o fornecedor foi apresentado à área de Compras.

## Parte 1 — Pipeline de dados

Construa um processo que:

1. Leia a planilha de entrada;
2. Normalize e valide os CNPJs;
3. Consulte os dados disponíveis na BrasilAPI;
4. Trate duplicidades, registros inválidos e consultas sem resultado;
5. Organize e transforme as informações;
6. Gere uma base consolidada;
7. Registre quando cada consulta foi realizada;
8. Possa ser executado novamente sem gerar duplicidades indevidas.

Considere situações como:

- CNPJ com ou sem pontuação;
- Registros duplicados;
- CNPJ inválido;
- Empresa não encontrada;
- Indisponibilidade ou erro na API;
- Resposta incompleta;
- Reexecução do processo.

Não esperamos uma arquitetura pronta para produção, mas queremos entender como você pensou em confiabilidade, manutenção e evolução.

## Parte 2 — Saída de dados

A base consolidada deverá apresentar, no mínimo:

- CNPJ original;
- CNPJ normalizado;
- Razão social;
- Nome fantasia;
- Situação cadastral;
- Data de abertura;
- Atividade econômica principal;
- Município;
- Estado;
- Data e hora da consulta;
- Status do processamento;
- Motivo do erro, quando aplicável.

Outros campos poderão ser utilizados caso sejam relevantes para o problema.

Também esperamos uma saída separada ou facilmente identificável para:

- CNPJs inválidos;
- Registros duplicados;
- Empresas não encontradas;
- Consultas que falharam;
- Registros que precisam de revisão humana.

Utilize apenas os dados necessários para resolver o problema. Caso a fonte retorne informações pessoais ou de sócios, avalie se elas realmente precisam ser armazenadas.

## Parte 3 — Visão para o negócio

A solução deverá oferecer uma visão simples para a área de Compras contendo, pelo menos:

- Total de CNPJs recebidos;
- Total processado com sucesso;
- Quantidade de erros ou pendências;
- Distribuição por situação cadastral;
- Distribuição por estado;
- Distribuição por atividade econômica;
- Lista de registros que precisam de revisão.

A apresentação pode ser feita por meio de:

- Aplicação simples;
- Dashboard;
- Relatório;
- Outra interface que considere adequada.

Não esperamos um front-end sofisticado. Um notebook pode apoiar a análise, mas não deve ser a única forma de apresentação para o usuário de negócio.

## Parte 4 — Aplicação de IA

Implemente uma funcionalidade de IA que ajude a área de Compras a compreender ou consultar os dados processados.

Pode ser, por exemplo:

- Um assistente em linguagem natural;
- Uma busca inteligente;
- Um gerador de resumos cadastrais;
- Outra abordagem que considere adequada para a área de Compras.

Não é obrigatório utilizar RAG. Esperamos que você escolha e justifique a abordagem mais apropriada para o problema.

A solução deverá ser capaz de responder perguntas semelhantes a:

- “Quantos fornecedores foram processados com sucesso?”
- “Quais fornecedores estão ativos em São Paulo?”
- “Resuma as informações do CNPJ X.”
- “Quais registros precisam de revisão e por quê?”
- “Quais são as principais atividades econômicas encontradas?”

As respostas devem utilizar apenas as informações disponíveis na base processada.

Quando uma informação não estiver disponível, a solução deverá informar isso claramente, sem inventar uma resposta. Sempre que possível, identifique quais registros ou campos sustentam a resposta.

A IA não deverá aprovar ou reprovar fornecedores automaticamente.

## Parte 5 — Eficiência operacional e ROI

Além da solução técnica, esperamos uma análise simplificada do benefício gerado para o negócio.

Considere o seguinte cenário atual:

- 500 CNPJs consultados por mês;
- 8 minutos de trabalho manual por CNPJ;
- 10% dos registros geram retrabalho;
- Cada retrabalho consome aproximadamente 5 minutos;
- Custo operacional estimado do analista: R$ 70 por hora;
- Um coordenador dedica 3 horas por mês à consolidação dos resultados;
- Custo estimado do coordenador: R$ 110 por hora;
- Investimento estimado para implantação da solução em produção: R$ 15.000.

Com base nesses dados e nas premissas da sua solução, estime os seguintes indicadores:

- Custo mensal estimado do processo atual;
- Horas consumidas atualmente;
- Tempo estimado por CNPJ com a nova solução;
- Intervenção humana que continuará necessária;
- Horas economizadas por mês;
- Percentual de redução do tempo operacional;
- Capacidade adicional gerada para a equipe;
- Custo mensal de infraestrutura e IA;
- Economia bruta mensal e anual;
- Benefício financeiro líquido;
- ROI estimado em 12 meses;
- Prazo estimado para retorno do investimento.

### Fórmulas sugeridas

**Economia operacional mensal**

> Custo mensal atual − custo mensal futuro

**Benefício em 12 meses**

> Economia operacional mensal × 12

**Benefício líquido em 12 meses**

> Benefício em 12 meses − investimento inicial

**ROI em 12 meses**

> Benefício líquido ÷ investimento inicial × 100

**Prazo de retorno**

> Investimento inicial ÷ economia operacional mensal

As premissas utilizadas deverão estar claramente identificadas. Caso algum número seja estimado, explique como chegou a ele.

Não é obrigatório demonstrar aumento de receita. Para este caso, o principal benefício esperado é a redução de esforço e custo operacional.

Possíveis ganhos de receita ou redução de risco só devem ser monetizados quando houver uma justificativa clara.

## Requisitos de qualidade

Esperamos encontrar:

- Instruções claras para executar o projeto;
- Organização e legibilidade do código;
- Tratamento básico de erros;
- Validações ou testes automatizados;
- Registro das principais decisões;
- Separação entre configuração e código;
- Ausência de senhas ou chaves no repositório;
- Arquivo `.env.example`, caso utilize variáveis de ambiente;
- Uma pequena amostra da saída;
- Limitações conhecidas;
- Possíveis evoluções da solução.

A solução deverá poder ser executada por outra pessoa seguindo as instruções do README.

Docker pode ser utilizado, mas não é obrigatório.

## Uso de ferramentas de IA no desenvolvimento

O uso de ferramentas de IA durante o desenvolvimento é permitido.

Inclua na documentação:

- Quais ferramentas foram utilizadas;
- Em quais partes elas ajudaram;
- Como o código ou conteúdo gerado foi validado;
- Quais decisões foram tomadas por você.

Não estamos avaliando memorização de sintaxe. Queremos entender seu raciocínio, suas decisões e como utiliza ferramentas de IA de forma responsável.

## Entrega

O repositório deverá conter:

- Código-fonte;
- Massa de dados utilizada na demonstração;
- Instruções para instalação e execução;
- Pipeline de consulta e tratamento;
- Saídas geradas;
- Funcionalidade de IA;
- Testes ou validações;
- Explicação da arquitetura;
- Premissas e cálculos de ROI;
- Limitações e próximos passos;

Não inclua chaves, senhas ou informações sensíveis no repositório.

## Apresentação

Prepare uma apresentação de até 10 minutos, direcionada a um coordenador da área de Compras.

A apresentação deverá explicar:

1. Qual problema está sendo resolvido;
2. Como o processo funciona atualmente;
3. Como a solução proposta funciona;
4. O que deixa de ser feito manualmente;
5. Quanto tempo pode ser economizado;
6. Qual o benefício estimado em reais;
7. Em quanto tempo o investimento pode se pagar;
8. Quais são as limitações e os riscos;
9. O que seria necessário para levar a solução à produção;
10. Quais são os próximos passos recomendados.

Evite uma apresentação excessivamente técnica. Detalhes de arquitetura e código poderão ser explorados durante as perguntas.

Após a apresentação, teremos aproximadamente 20 minutos para conversar sobre a implementação e as decisões tomadas.

## Tempo sugerido

Sugerimos dedicar entre 6 e 8 horas ao desafio.

Não esperamos uma solução completa de produção. Preferimos uma entrega menor, funcional e bem explicada a uma implementação extensa e sem clareza.

Caso alguma parte não seja concluída, documente:

- O que ficou pendente;
- Por que não foi concluído;
- Como você implementaria essa parte;
- Qual seria sua prioridade em uma próxima etapa.

## O que será avaliado

- Compreensão do problema e do usuário;
- Organização e qualidade do pipeline de dados;
- Tratamento de erros e qualidade dos dados;
- Clareza das decisões técnicas;
- Aplicação útil e responsável de IA;
- Capacidade de mensurar eficiência e retorno financeiro;
- Organização do código e da documentação;
- Comunicação com um público não técnico;
- Identificação de riscos, limitações e próximos passos.
