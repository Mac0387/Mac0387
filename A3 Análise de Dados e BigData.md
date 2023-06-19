# Trabalho A3

UC ANÁLISE DE DADOS E BIG DATA

Tema:
Análise de dados exploratória do Campeonato Brasileiro de 2003 a 2022

Nome e RA:

Marco Antonio de Ávila Cardoso – RA 321217291



# Análise de dados exploratória do Campeonato Brasileiro de 2003 a 2022


 


# Introdução:

O Campeonato Brasileiro de Futebol é uma das competições esportivas mais tradicionais e prestigiadas do país, envolvendo os principais clubes de futebol do Brasil. Ao longo dos anos, o campeonato tem sido palco de partidas emocionantes, rivalidades acirradas e momentos inesquecíveis para os fãs do esporte. A análise exploratória dos dados desse campeonato oferece uma oportunidade de compreender melhor o desempenho das equipes ao longo do tempo e explorar estatísticas-chave.

Neste estudo, iremos explorar um conjunto de dados abrangendo o período de 2003 a 2022, que foram extraídos a partir de pesquisas no Google e compilados por meio da plataforma Kaggle. Esses dados fornecem informações valiosas sobre o desempenho dos clubes, permitindo-nos investigar diferentes aspectos do Campeonato Brasileiro de Futebol.

Essas informações nos permitirão analisar tendências, identificar padrões e compreender o impacto desses fatores no desempenho das equipes ao longo dos anos.


# Objetivo:

O objetivo deste estudo é realizar uma análise exploratória de alguns dados do Campeonato Brasileiro de Futebol, no período de 2003 a 2022, com foco em identificar padrões e obter insights sobre o desempenho dos clubes em relação a vários aspectos do jogo. Para alcançar esse objetivo, serão realizadas as seguintes análises:

1.	Identificação do clube com o maior número de vitórias;
2.	Comparação da média de finalizações e finalizações na direção do gol entre os clubes;
3.	Média de gols por time como mandante e como visitante;


# Metodologia:

Para compreender diferentes aspectos do desempenho dos clubes, foi utilizada a legenda do conjunto de dados disponível abaixo:

Legenda do arquivo: campeonato-brasileiro-full.csv

Coluna	 Descrição
Rodada 	 Rodada que aconteceu a partida
Data 	 Data que ocorreu a partida
Horário 	  Horário que ocorreu a partida
Dia 	 Dia da semana que ocorreu a partida
Mandante 	 Clube mandante                      
Visitante 	 Clube Visitante
formacao_mandante	 Formação do mandante
formacao_visitante	 Formação do visitante
tecnico_mandante	 Técnico do mandante
tecnico_visitante	 Técnico do visitante
Vencedor 	 Clube vencedor da partida. Quando tiver "-"
Arena 	 Arena que ocorreu a partida                      
Mandante Placar 	 Gols que o clube mandante fez na partida                      
Visitante Placar 	 Gols que o clube visitante fez na partida                      
Estado Mandante 	 Estado do clube mandatorio                      
Estado Visitante 	 Estado do clube visitante                      
Estado Vencedor 	 Estado do clube vencedor. Quando tiver "-"


Legenda do arquivo: campeonato-brasileiro-estatisticas-full.csv

Coluna	 Descrição
partida_ID 	 ID da partida
Rodada 	 Rodada da partida
Clube 	 Nome do clube
Chutes 	 Finalizações
Chutes a gol 	 Finalizações na direção do gol
Posse de bola 	 Percentual da posse de bola
Passes 	 Quantidade de passes que o clube deu na partida
precisao_passes 	 Percentual da precisão de passe
Faltas 	 Quantidade de faltas cometidas na partida
cartao_amarelo 	 Quantidade de cartões amarelos para o clube na partida
cartao_vermelho 	 Quantidade de cartões vermelhos para o clube na partida
Impedimentos 	 Quantidade de impedimentos para o clube na partida
Escanteios 	 Quantidade de escanteios para o clube na partida



# Configuração do Ambiente:

O ambiente foi configurado em Python através do site https://colab.research.google.com/ e foi utilizado as bibliotecas pandas, numpy e matplotlib.

Importar as bibliotecas necessárias
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

Configurar opções para exibição dos dados
pd.set_option('display.max_columns', None)  # Exibir todas as colunas do DataFrame

Carregar os conjuntos de dados
df_partidas = pd.read_csv('caminho/do/arquivo/campeonato-brasileiro-full.csv')
df_estatisticas = pd.read_csv('caminho/do/arquivo/campeonato-brasileiro-full.csv')



# Leitura dos Dados:

Exemplo de uso das bibliotecas e visualização dos dados.

print("Exemplo de visualização dos dados:")
print("Dados do conjunto de partidas:")
print(df_partidas.head())
print("Dados do conjunto de estatísticas:")
print(df_partidas.head())



# Visão geral do conjunto de dados

Panorama geral de quantas linhas, colunas cada conjunto de dados possui e também o tipo dos dados armazenados.

Leitura dos dados e atribuição a uma variável chamada df

df = pd.read_csv('/content/campeonato-brasileiro-estatisticas-full.csv')

# Verificação do tamanho do conjunto de dados

print("Tamanho do conjunto de dados - estatisticas:")
print(df.shape)  # Retorna o número de linhas e colunas do DataFrame
print("Informações sobre as colunas e tipos de dados - estatisticas:")
print(df.info())  # Retorna informações sobre as colunas, incluindo nome e tipo de dado

df = pd.read_csv('/content/campeonato-brasileiro-full.csv')

# Verificação do tamanho do conjunto de dados
print("Tamanho do conjunto de dados - partidas:")
print(df.shape)  # Retorna o número de linhas e colunas do DataFrame
print("Informações sobre as colunas e tipos de dados - partidas:")
print(df.info())  # Retorna informações sobre as colunas, incluindo nome e tipo de dado


# Análise dos Dados

1.	Identificação do clube com o maior número de vitórias

Identificação do clube com o maior número de vitórias:
Com base nos dados analisados, foi identificado que o clube com o maior número de vitórias no Campeonato Brasileiro de Futebol, no período de 2003 a 2022, é o São Paulo Futebol Clube, com 351 vitórias.

Identificar o clube com o maior número de vitórias
vitorias_por_time = df_partidas.loc[df_partidas['vencedor'] != '-', 'vencedor'].value_counts()
clube_maior_vitoria = vitorias_por_time.idxmax()
numero_vitorias = vitorias_por_time.max()
nome_clube_maior_vitoria = df_partidas.loc[df_partidas['vencedor'] == clube_maior_vitoria, 'vencedor'].iloc[0]
print(f"Clube com o maior número de vitórias: {nome_clube_maior_vitoria} ({numero_vitorias} vitórias)")


2.	Comparação da média de finalizações e finalizações na direção do gol entre os clubes;

Ao analisar a média de finalizações e finalizações na direção do gol entre os clubes do Campeonato Brasileiro de Futebol, observou-se que Bragantino possui a maior média de finalizações e finalizações em direção ao gol. Vale ressaltar que ainda seria possível fazer uma análise de efetividade dos chutes com relação a quantidade de gols.

Cálculo da média de finalizações por clube
media_finalizacoes = df_estatisticas.groupby('clube')['chutes'].mean()

Cálculo da média de finalizações na direção do gol por clube
media_finalizacoes_gol = df_estatisticas.groupby('clube')['chutes_no_alvo'].mean()

Ordenação dos clubes em ordem decrescente pela média de finalizações
media_finalizacoes = media_finalizacoes.sort_values(ascending=False)

Ordenação dos clubes em ordem decrescente pela média de finalizações na direção do gol
media_finalizacoes_gol = media_finalizacoes_gol.sort_values(ascending=False)

Preparação dos dados para o gráfico
clubes = media_finalizacoes.index
finalizacoes = media_finalizacoes.values
finalizacoes_gol = media_finalizacoes_gol.values

Configuração do gráfico
plt.figure(figsize=(10, 6))
plt.bar(clubes, finalizacoes, label='finalizações')
plt.bar(clubes, finalizacoes_gol, label='finalizações na Direção do Gol')
plt.title('Comparação da Média de finalizações e finalizações na direção do Gol por Clube')
plt.xlabel('Clube')
plt.ylabel('Média')
plt.legend()

Alternar a posição dos nomes dos clubes
plt.xticks(rotation=90)

Exibição do gráfico
plt.show()



# 3.	Média de gols por time como mandante e como visitante

Ao analisar a média de gols por time como mandante e como visitante, observou-se que os times apresentaram diferentes desempenhos dependendo de sua condição de jogo. Esses resultados podem indicar uma maior efetividade ou adaptação ao ambiente de jogo para cada time.


Agrupar os dados pelo nome do time
gols_por_time = df_partidas.groupby('mandante').agg({'mandante_Placar': 'mean', 'visitante_Placar': 'mean'})

Renomear as colunas
gols_por_time.columns = ['Média Gols em Casa', 'Média Gols Fora de Casa']

Exibir a média de gols por partida de cada time
print(gols_por_time)



# Conclusão:

A análise exploratória dos dados do Campeonato Brasileiro de Futebol, no período de 2003 a 2022, permitiu obter insights valiosos sobre o desempenho dos clubes em relação a diferentes aspectos do jogo. Foi identificado o clube com o maior número de vitórias, comparada a média de finalizações e finalizações na direção do gol entre os clubes, e analisada a média de gols por time como mandante e como visitante. Essas informações proporcionam uma compreensão mais aprofundada do desempenho das equipes ao longo do tempo e contribuem para uma análise mais abrangente do Campeonato Brasileiro de Futebol.



# Referência:

Campeonato Brasileiro de Futebol – 2003 a 2022. Disponível em: https://www.kaggle.com/datasets/adaoduque/campeonato-brasileiro-de-futebol

Ferramenta utilizada: Colaboratory - https://colab.research.google.com/ - Linguagem Python
