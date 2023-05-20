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

- Ferramenta utilizada para preencher campos nulos, mudar tipo dos dados, fazer carga no sql, etc.

![Captura de tela 2023-05-20 145319](https://github.com/Mecoaliza/CEPE/assets/113151407/21140b1d-b875-41db-b9be-b02142594286)


####  Linguagem M: Tratamento de dados, criação de colunas, mesclagens

- Algumas expressões usadas em M, porém não usei muitas, pois boa parte do tratamento foi feito no Pentaho

```
let
    Fonte = Sql.Databases("DESKTOP-U7K3B00"),
    soccer = Fonte{[Name="soccer"]}[Data],
    dbo_player_keepers = soccer{[Schema="dbo",Item="player_keepers"]}[Data]
in
    dbo_player_keepers
```
```
= Table.TransformColumnTypes(Fonte,{{"id_position", type text}, {"nm_descricao", type text}})
```
```
= Table.NestedJoin(dbo_player_stats, {"position"}, dim_position, {"id_position"}, "dim_position", JoinKind.LeftOuter)
```

![Captura de tela 2023-05-20 150132](https://github.com/Mecoaliza/CEPE/assets/113151407/449a8ab9-f77e-440f-8ff2-03d8295a2dff)

#### Linguagem DAX: criação de métricas

- Criei apenas algumas métricas simples, usei mais nos cards

```
goals = SUM(player_stats[goals]) 
```
```
goals = SUM(player_stats[goals]) 
```

### Modelagem e relacionamentos

- A modelagem foi a star schema, que possui algumas vantagens como: Simplicidade, Desempenho de consulta, Facilidade de manutenção,
Facilidade de consulta e análise e Flexibilidade.


![Captura de tela 2023-05-20 145904](https://github.com/Mecoaliza/CEPE/assets/113151407/8d4bb001-ddec-48cb-8114-676496423e86)

### Indicadores/bookmarks
- Criei indicadores que limpam os filtros e usei como botão para facilitar a experiência do usuário

![Captura de tela 2023-05-20 150620](https://github.com/Mecoaliza/CEPE/assets/113151407/fe706983-45c1-4850-90ab-506261096da5)

### Tooltips

- As tooltips criadas foi de detalhamento de quais jogadores receberam cartão amarelo ou vermelho.

![Captura de tela 2023-05-20 150728](https://github.com/Mecoaliza/CEPE/assets/113151407/22c4cfe1-c834-4c15-af75-0565968f5171)

![Captura de tela 2023-05-20 150811](https://github.com/Mecoaliza/CEPE/assets/113151407/15df1243-51f6-488a-8f05-c2deac01a3a6)


### Documentação 

- A documentação foi criada usando a ferramenta Power BI Helper, onde é possível vizualisar mais detalhes de tabelas que foram usadas ou tão, 
todas as relações, quais foram as formulas usadas, quais informações tem em ca file da coluna, entre vários outros detalhes.

O link para baixar o arquivo está [disponível aqui](file:///C:/Users/mecoa/AppData/Local/Microsoft/Windows/INetCache/IE/O9Z1BCA1/Futebol[2].htm)



