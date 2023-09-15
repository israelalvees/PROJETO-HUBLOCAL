<div align="center">
	
![ETL](https://img.shields.io/badge/ETL-pink?style=for-the-badge&logo=sql&logoColor=white) ![LOOKER STUDIO](https://img.shields.io/badge/LOOKER%20STUDIO-Blue?style=for-the-badge&color=blue&labelColor=007ACC) ![GOOGLE](https://img.shields.io/badge/GOOGLE-Google?style=for-the-badge&labelColor=white&color=black)







</div>
<br>


<p align="center">
<img src="https://img.shields.io/badge/STATUS-CONCLUÍDO-blue"/>
</p>
<br>


# PROJETO-HUBLOCAL

## OBJETIVO: 

-  Construir uma dashboard comercial utilizando o Looker Studio (Data Studio) para apoiar a análise de dados da área de marketing e comercial da Hub.

## PRIMEIRA ETAPA:

- Análise exploratória dos dados.
- Foi detectado uma quanditade de Nulls e valores erradicos (0, 1, 7) em fontes como Anúncio, Campanha.

## SEGUNDA ETAPA: ETL

- Após feita a análise, foi identificado que não havia necessiade de ultilizar-se Ferramenta de ETL, como Pentaho. A quantidade de dados a ser tradada era pouca e simples.
- O tratamento foi feito no próprio Google Sheets.
- DADOS NÃO INFORMADOS: Em alguns campos não foi informado o dado, sendo assim os nulls e outros dados incoerentes foram substituidos pela informação "não informado". Afim de se ter uma análise mais clara e real.

- IMPORTANTE: Foi solicitado um filtro por NOME DO LEAD, porém essa informação não consta na Base de Dados fornecida. Sendo assim não foi possível criar o filtro. No dia a dia, seria contactado o Engenheiro ou verificado a possibilidade de atualizar a base para incluir a informação. No caso por ser um teste, não foi possível faze-lo.  

## TERCEIRA ETAPA: Criação do Dash.

- Utilizando a planilha como fonte de dados, foi criado o dash de acordo com o solicitado.
- Na página "Venda por Origem" foi sugerido um outro tipo de visualização, tendo em vista que o gráfico pizza não é o ideal quando a uma quantidade grande de dados, pois dificulta o entendimento.
- Foi ultilizado formulas no Looker Studio afim de atingir-se a análise solicitada:

  - Conversão de Negociação Realizadas:
    ```sql    
    SUM(CASE WHEN Funil: etapa = 'Proposta Enviada' THEN 1 ELSE 0 END) / SUM(CASE WHEN Funil: etapa = 'Reunião Realizada' THEN 1 ELSE 0 END)
    ```
  - Conversão de Propostas Enviadas:
    ```sql
    SUM(CASE WHEN Funil: etapa = 'Negociação' THEN 1 ELSE 0 END) / SUM(CASE WHEN Funil: etapa = 'Proposta Enviada' THEN 1 ELSE 0 END)
    ```

  - Conversão de Xeque Mate:
    ```sql
    SUM(CASE WHEN Funil: etapa = 'Xeque Mate' THEN 1 ELSE 0 END) / SUM(CASE WHEN Funil: etapa = 'Negociação' THEN 1 ELSE 0 END)
    ```


  
    
