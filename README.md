# Teste_WorCup_2022
Analise de dados de futebol
Critérios avaliadas:
- Linguagem M: Tratamento de dados, criação de colunas, mesclagens
- Linguagem DAX: criação de métricas;
- Modelagem e relacionamentos;
- Indicadores/bookmarks;
- Tooltips;
- Visual.

O link para baixar o arquivo está [disponível aqui](https://onedrive.live.com/?id=7782EEBC0072CC7B%212329&cid=7782EEBC0072CC7B)



### Soluções Utilizadas

- Pentaho
- SQL Server
- Power BI

### Fluxo de ETL

![Captura de tela 2023-05-20 144905](https://github.com/Mecoaliza/CEPE/assets/113151407/2f631301-3ada-48e1-a392-28740aa57e7f)


#### Transformação Pentaho

![Captura de tela 2023-05-20 145319](https://github.com/Mecoaliza/CEPE/assets/113151407/21140b1d-b875-41db-b9be-b02142594286)

#### Modelagem Dimensional

![Captura de tela 2023-05-20 145904](https://github.com/Mecoaliza/CEPE/assets/113151407/ace0b818-0854-483d-945c-7c42bf82a26b)

####  Linguagem M: Tratamento de dados, criação de colunas, mesclagens

= Table.TransformColumnTypes(Fonte,{{"id_position", type text}, {"nm_descricao", type text}})
= Table.NestedJoin(dbo_player_stats, {"position"}, dim_position, {"id_position"}, "dim_position", JoinKind.LeftOuter)

![Captura de tela 2023-05-20 150132](https://github.com/Mecoaliza/CEPE/assets/113151407/449a8ab9-f77e-440f-8ff2-03d8295a2dff)

#### Linguagem DAX: criação de métricas

goals = SUM(player_stats[goals]) 
goals = SUM(player_stats[goals]) 

### Modelagem e relacionamentos

![Captura de tela 2023-05-20 145904](https://github.com/Mecoaliza/CEPE/assets/113151407/8d4bb001-ddec-48cb-8114-676496423e86)

### Indicadores/bookmarks

![Captura de tela 2023-05-20 150620](https://github.com/Mecoaliza/CEPE/assets/113151407/fe706983-45c1-4850-90ab-506261096da5)

### Tooltips

![Captura de tela 2023-05-20 150728](https://github.com/Mecoaliza/CEPE/assets/113151407/22c4cfe1-c834-4c15-af75-0565968f5171)

![Captura de tela 2023-05-20 150811](https://github.com/Mecoaliza/CEPE/assets/113151407/15df1243-51f6-488a-8f05-c2deac01a3a6)


### Documentação 

[Disponível aqui](file:///C:/Users/mecoa/Downloads/Estatisticas%20Futebolistica%20-%20Copa%20do%20Mundo%202022/Documentacao.htm)
