# Banco de Dados de uma Loja de Vinhos (MySQL)

Modelagem relacional de uma loja de vinhos: **regiões, vinícolas e vinhos**, com chaves estrangeiras, dados de exemplo e uma consulta que junta as três tabelas. Meu primeiro projeto de estudos em SQL.

## 🧱 Stack

![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white&style=flat-square)

## 🗺️ Modelo de dados

```
regional (cod_regiao PK)
   │ 1
   │
   │ N
vinicola (cod_vinicola PK, cod_regiao FK)
   │ 1
   │
   │ N
vinhos (cod_vinhos PK, cod_vinicola FK)
```

| Tabela | Principais campos |
|---|---|
| `regional` | nome e descrição da região |
| `vinicola` | nome, descrição, telefone, e-mail e região |
| `vinhos` | nome, tipo, ano, descrição e vinícola |

## 🔍 Consulta principal

Lista cada vinho com o ano, a vinícola e a região de origem:

```sql
SELECT v.nome_vinhos, v.ano_vinhos, vi.nome_vinicola, r.nome_regiao
FROM vinhos v
JOIN vinicola vi ON v.cod_vinicola = vi.cod_vinicola
JOIN regional r  ON vi.cod_regiao  = r.cod_regiao;
```

## ▶️ Como rodar

```bash
mysql -u root -p < "PROJETO SQL.sql"
```

O script apaga e recria o banco `loja_vinhos`, insere os dados na ordem certa (regiões, depois vinícolas, depois vinhos) e termina mostrando o resultado da consulta principal. Testado no MariaDB.

## 🧠 O que pratiquei

- Criação de banco e tabelas com chaves primárias e estrangeiras
- Relacionamentos 1 para N
- Inserção de dados e consultas com `JOIN` entre três tabelas

## 🔭 Próximos passos

- [x] Corrigir a ordem dos `INSERT`
- [x] Usar aspas simples nos textos (padrão SQL)
- [ ] Adicionar consultas com `GROUP BY` e agregações (vinhos por região, vinícola mais antiga etc.)
