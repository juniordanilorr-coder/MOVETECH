# MoveTech — Análise de Corridas

Projeto integrador do curso Técnico em Ciência de Dados, desenvolvido no componente Matemática e Estatística para Ciência de Dados.

## Objetivo

Analisar os dados de corridas da MoveTech para apoiar decisões sobre distribuição da frota, redução do tempo de espera e aceitação das solicitações.

O projeto utilizará análise descritiva, amostragem, probabilidade e inferência estatística.

## Integrantes

- Danilo Ribeiro Rodrigues Junior
- Giovanna Muniz Antoniazzi
- Rafael de Moura de Oliveira
- Nicollas Bernardo Furtunnato 
- Leonardo Ricardo Gomes Belido
- Yasmin Alves Vitório

## Perguntas do projeto

- Como as categorias de serviço se relacionam com a aceitação das corridas?
- Qual é o tempo médio de espera e a probabilidade de ultrapassar 10 minutos?
- Quais regiões e horários precisam de maior atenção na distribuição da frota?
- Existem corridas com comportamento anômalo?

## Arquivos

| Arquivo | Descrição |
|---|---|
| `DADOS/movetech_corridas.csv` | Base original, preservada sem alterações. |
| `DADOS/DADOS.xlsx` | Versão tratada no Excel, com etapas registradas no Power Query. |
| `DADOS/DICIONARIO_DE_DADOS.md` | Dicionário de dados: descrição, classificação, unidade e valores de cada variável. |
| `notebook_v1.ipynb` | Notebook da primeira etapa: importação, classificação das variáveis e amostragem. |
| `requirements.txt` | Bibliotecas Python necessárias para executar o notebook. |
| `.gitignore` | Regras para ignorar arquivos locais e temporários. |
| `README.md` | Apresentação e documentação do projeto. |

## Preparação dos dados

A base original possui 19.202 registros e 13 colunas.

A preparação foi realizada no Power Query do Excel:

1. Remoção de 91 linhas completamente duplicadas, considerando as 13 colunas.
2. Padronização de espaços, maiúsculas, minúsculas e grafias nas colunas categóricas.
3. Correção de nomes de regiões sem acento.
4. Padronização dos dias da semana, incluindo a abreviação `SAB`.
5. Unificação de `black` e `pop` com suas respectivas categorias MoveTech.
6. Padronização dos separadores decimais.
7. Remoção do símbolo `R$` dos valores monetários.
8. Conversão de espera, duração, distância e valor para números decimais, usando a localidade Inglês (Estados Unidos) após a padronização.
9. Padronização dos horários, incluindo a conversão de formatos como `1h02` para `1:02`, seguida da conversão para o tipo Hora.
10. Correção final de grafias: `Ipe Amarelo` para `Ipê Amarelo` (1 registro), `Alto Da Serra` para `Alto da Serra`, sufixo `-Feira` para `-feira` nos dias da semana e nomes das categorias de serviço no formato `MoveTech Pop`, `MoveTech Black`, `MoveTech Mulher` e `MoveTech Bag`.

Após a remoção das duplicatas, a base permaneceu com 19.111 registros. A etapa 10 altera apenas a escrita dos rótulos: não muda a quantidade de registros nem os valores numéricos.

A verificação de qualidade foi realizada sobre todo o conjunto de dados. As colunas numéricas e de horário verificadas apresentaram 100% de valores válidos no Power Query.

Essa validação confirma a compatibilidade com os tipos definidos, mas não garante a ausência de inconsistências de negócio ou valores atípicos. Esses pontos serão investigados nas análises. Os valores atípicos foram mantidos na base.

Conforme orientação do professor, a limpeza é feita no Power Query e documentada neste README; o notebook parte da tabela já tratada.

## Ferramentas

- Excel e Power Query: preparação e conferência dos dados.
- VS Code: desenvolvimento do notebook.
- Python 3.14.6: ambiente previsto para as análises.
- pandas e NumPy: manipulação dos dados e sorteio das amostras.
- openpyxl: leitura da planilha pelo pandas.
- matplotlib, seaborn e SciPy: gráficos e distribuições de probabilidade (etapas seguintes).
- Git e GitHub: controle de versões e colaboração.

## Reprodução da preparação

As etapas de transformação estão registradas na consulta do Power Query, dentro de `DADOS/DADOS.xlsx`.

Ao abrir a planilha em outro computador, pode ser necessário ajustar o caminho da etapa Fonte para o arquivo `DADOS/movetech_corridas.csv` antes de atualizar a consulta.

O notebook lê a tabela já tratada (aba `movetech_corridas`); a leitura não executa nem atualiza a consulta do Power Query.

## Como executar o notebook

1. Clone o repositório e abra a pasta do projeto no VS Code.
2. Crie e ative um ambiente virtual (no Windows, pelo terminal do VS Code):

   ```
   python -m venv .venv
   .venv\Scripts\activate
   ```

3. Instale as bibliotecas:

   ```
   pip install -r requirements.txt
   ```

4. Abra `notebook_v1.ipynb`, selecione o kernel do ambiente `.venv` e execute todas as células (*Run All*).

O notebook usa caminhos relativos e deve ser aberto a partir da pasta raiz do projeto. O sorteio das amostras usa a semente 42. O notebook final deverá reproduzir todos os números apresentados no relatório.

## Andamento

- [x] Criar o repositório.
- [x] Preservar a base original.
- [x] Realizar a primeira preparação dos dados.
- [x] Enviar a base original e a planilha tratada ao GitHub.
- [x] Documentar a preparação dos dados e integrá-la ao pipeline técnico.
- [x] Classificar as variáveis e elaborar o dicionário de dados.
- [ ] Realizar e comparar as amostragens (primeira versão pronta no `notebook_v1.ipynb`; decisão final sobre os estratos em revisão).
- [ ] Desenvolver análises descritivas e visualizações.
- [ ] Aplicar distribuições de probabilidade.
- [ ] Desenvolver inferência estatística conforme o cronograma da disciplina.
- [ ] Realizar a etapa de Matemática Aplicada.
- [ ] Elaborar o relatório executivo e a apresentação.

## Uso de IA

O ChatGPT foi utilizado como apoio para explicar conceitos, orientar a configuração do Git e do GitHub, sugerir códigos e procedimentos de limpeza e auxiliar na documentação.

O Claude (Anthropic) foi utilizado para revisar o repositório e o notebook, conferir a preparação dos dados reproduzindo a limpeza de forma independente a partir do CSV original e comparando o resultado com `DADOS.xlsx`, apontar pendências e auxiliar na elaboração do dicionário de dados, do `requirements.txt` e desta atualização do README.

As operações foram executadas pelos integrantes, com conferência dos resultados ao longo do processo. A equipe é responsável por revisar as sugestões, compreender os procedimentos e validar as conclusões apresentadas.
