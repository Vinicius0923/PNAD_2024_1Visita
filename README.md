### PNAD_2024_1Visita

Geração de Indicadores de Moradores sem Energia Elétrica (PNAD Contínua)
Objetivo
Este script calcula o total de moradores que não possuem ou não utilizam energia elétrica com base nos microdados da PNAD Contínua 2024 – 1ª visita, utilizando o pacote PNADcIBGE e o desenho amostral da pesquisa.
Principais Etapas

Carregamento de pacotes

PNADcIBGE, survey, dplyr, readr, writexl, stringi.


Configuração de caminhos
Define diretórios e arquivos:

Microdados (PNADC_2024_visita1.txt)
Input (input_PNADC_2024_visita1_20251119.txt)
Dicionário (dicionario_PNADC_microdados_2024_visita1_20251119.xls)


Leitura e rotulagem dos dados

read_pnadc() para carregar microdados.
pnadc_labeller() para aplicar rótulos.


Criação do desenho amostral

pnadc_design() para definir pesos e estratos.


Criação do indicador sem_energia

Normalização de texto (stri_trans_general).
Identificação de padrões: "nao utiliza/tem energia eletrica", "nao tem energia", "sem energia".


Cálculo dos totais

svyby() para estimar:

Moradores sem energia (svytotal).
Total de moradores (denominador).

Junção e agregação

Totais por UF.
Detalhamento por UF e situação (V1022).

Exportação para Excel

Arquivo: moradores_sem_energia_2024_visita1.xlsx
Abas:

Totais_por_UF
Detalhamento_UF_Situacao

Saída

Arquivo Excel com duas abas:

Totais_por_UF: agregação por Unidade da Federação.
Detalhamento_UF_Situacao: valores por UF e situação (urbano/rural).



Observações

Ajuste para PSU solitária: options(survey.lonely.psu = "adjust").
Indicador robusto para diferentes variações textuais.
Script compatível com PNADcIBGE e desenho amostral oficial.
