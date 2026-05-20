# Resumo — JPA Avançado

# Novas Entidades
Entidades representam tabelas do banco de dados.

Ao criar novas entidades:
- seguimos a modelagem do banco;
- mapeamos atributos e relacionamentos;
- usamos anotações da JPA.

---

# Relacionamento Muitos-para-Muitos (ManyToMany)
Representa situações onde:
- muitos registros se relacionam com muitos outros.

Exemplo:
- Pedido possui vários Produtos;
- Produto pode estar em vários Pedidos.

Normalmente gera:
- tabela intermediária.

---

# Relacionamento Bidirecional
Ocorre quando:
- duas entidades se conheem mutuamente.

Exemplo:
- Pedido possui Cliente;
- Cliente possui lista de Pedidos.

Objetivo:
- permitir navegação nos dois lados.

---

# Persistência em Relacionamentos Bidirecionais
Ao persistir entidades relacionadas:
- ambos os lados da relação precisam estar sincronizados.

Importante:
- manter consistência dos relacionamentos em memória.

---

# Funções de Agregação
Funções usadas em consultas JPQL para cálculos.

Principais:
- min → menor valor
- max → maior valor
- avg → média
- sum → soma

Muito usadas em:
- relatórios;
- estatísticas;
- dashboards.

---

# Consultas de Relatórios
JPQL permite criar consultas específicas para:
- projeções;
- relatórios;
- dados resumidos.

Objetivo:
- evitar carregar entidades completas desnecessariamente.

---

# select new
Recurso do JPQL usado para:
- retornar objetos personalizados;
- criar DTOs diretamente na consulta.

Vantagem:
- consultas mais leves e organizadas.

---

# Named Queries
Consultas JPQL pré-definidas e reutilizáveis.

Objetivo:
- organização;
- reutilização;
- centralização das consultas.

---

# Estratégias EAGER e LAZY

## EAGER
Carrega relacionamento imediatamente.

Vantagem:
- dados já disponíveis.

Desvantagem:
- pode carregar informações desnecessárias.

---

## LAZY
Carrega relacionamento apenas quando necessário.

Vantagem:
- melhor performance.

Desvantagem:
- pode gerar LazyInitializationException.

---

# LazyInitializationException
Erro que ocorre quando:
- tentamos acessar relacionamento LAZY;
- fora do contexto ativo da JPA.

Normalmente acontece:
- após fechar EntityManager;
- fora da transação.

---

# Boas Práticas de Carregamento
Evitar:
- carregar relacionamentos desnecessários;
- consultas excessivas.

Objetivo:
- melhorar performance;
- evitar problemas de memória.

---

# join fetch
Recurso JPQL usado para:
- carregar relacionamentos junto da consulta;
- evitar problemas de LAZY.

Muito usado para:
- otimizar consultas.

---

# Parâmetros Opcionais
Permitem criar consultas dinâmicas.

Objetivo:
- aplicar filtros apenas quando necessário.

---

# Criteria API
API da JPA para criação de consultas programaticamente.

Características:
- consultas dinâmicas;
- tipagem forte;
- construção via Java.

Muito usada quando:
- filtros são variáveis.

---

# Consultas Dinâmicas
Com Criteria API podemos:
- adicionar filtros dinamicamente;
- montar consultas conforme necessidade.

---

# @Embeddable
Define uma classe reutilizável incorporável em entidades.

Usado para:
- agrupar atributos relacionados.

Exemplo:
- endereço;
- dados bancários.

Objetivo:
- reutilização;
- organização.

---

# @Embedded
Usado para incorporar uma classe @Embeddable dentro de uma entidade.

---

# Herança entre Entidades
JPA permite herança entre entidades.

Objetivo:
- reutilizar estrutura e comportamento.

---

# Estratégia SINGLE_TABLE
Toda hierarquia é salva em:
- uma única tabela.

Usa:
- coluna discriminadora para diferenciar tipos.

Vantagem:
- melhor performance.

Desvantagem:
- tabela maior e menos normalizada.

---

# Estratégia JOINED
Cada classe possui:
- sua própria tabela.

As tabelas são unidas por:
- chaves primárias e estrangeiras.

Vantagem:
- banco mais normalizado.

Desvantagem:
- consultas mais complexas.

---

# Chave Composta
Chave primária formada por:
- mais de um atributo.

Usada quando:
- um único campo não identifica entidade sozinho.

---

# @EmbeddedId
Usado para mapear:
- chave composta.

A chave é criada em:
- uma classe separada.

---

# Relação entre @EmbeddedId e @Embeddable
A classe da chave composta:
- usa @Embeddable.

A entidade:
- usa @EmbeddedId.

---

# Objetivo Geral
Melhorar:
- modelagem;
- performance;
- reutilização;
- organização;
- flexibilidade das consultas.

---
