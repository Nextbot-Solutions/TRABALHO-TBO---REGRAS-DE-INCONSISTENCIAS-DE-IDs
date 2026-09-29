# TRABALHO-TBO---REGRAS-DE-INCONSISTENCIAS-DE-IDs

# Busca e Ordenação – Projeto 1

Projeto da disciplina de Busca e Ordenação (IFNMG – Campus Montes Claros).
Professor: Tadeu Zubaran

Alunos: Diogo e Pedro

## Módulo escolhido

**Módulo 4 – Regra de Inconsistência de IDs**

Ao carregar os dados, se um cinema referencia um código de filme que não existe,
o sistema associa esse cinema ao filme existente com o código maior mais próximo
(o "sucessor").

## Como compilar e executar

chcp 65001

## Como funciona

1. **Carregamento:** os arquivos são lidos inteiros para a memória e interpretados
   manualmente. Cada filme é guardado uma única vez em um vetor.
2. **Ordenação:** o sistema verifica se os filmes estão ordenados por ID.
   Se não estiverem, aplica um merge sort implementado do zero.
3. **Tabela de sucessores:** para cada ID possível entre o menor e o maior,
   a tabela guarda a posição do primeiro filme com ID maior ou igual.
   Assim, a consulta do sucessor é feita em **O(1)**.
4. **Busca binária:** também implementada manualmente, em O(log n),
   para comparação de desempenho.
5. **Cinemas:** cada referência a filme é resolvida pela tabela durante a carga.

## Decisões de projeto

- A tabela ocupa cerca de 5 MB de memória, mas deixa a consulta
  cerca de 100 vezes mais rápida que a busca binária.
- IDs maiores que o último filme não têm sucessor e são marcados como tal.
- O cinema `cc00399` aparece duplicado no arquivo. Os dois registros
  foram mantidos e o sistema exibe um aviso na carga.

## Resultados

| Medida | Valor |
|---|---|
| Carga total | ~300 ms |
| Referências de filmes nos cinemas | 2009 |
| Referências corrigidas | 397 |
| Consulta O(1) | ~3 ns |
| Busca binária | ~325 ns |
