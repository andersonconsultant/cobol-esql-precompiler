# Roteiro de Aprendizado: Integração COBOL-SQL com Parser Avançado

## Contexto do Projeto e Progresso

### Sobre o Projeto
Este é um projeto de estudo focado no Open-COBOL-ESQL-1.4, um sistema que integra COBOL com SQL através de um parser sofisticado. O projeto está localizado em `/home/server/Open-COBOL-ESQL-1.4`.

### Estado Atual (Última Atualização)
- **Parser Principal**: Analisado o arquivo `ocesql/parser.y`
- **Funcionalidades Principais Identificadas**:
  1. Processamento de comandos SQL embarcados em COBOL
  2. Gerenciamento de host variables
  3. Suporte a diversos tipos de dados COBOL
  4. Sistema de cursores e prepared statements

### Progresso de Aprendizado
- **Concluído**:
  - [x] Ambiente Unix/Linux básico
  - [x] Comandos básicos do terminal
  - [x] Gerenciamento de processos
  - [x] Permissões de arquivos
  - [x] Variáveis de ambiente
  - [x] Shell scripting básico

- **Em Andamento**:
  - Análise do parser COBOL-SQL
  - Compreensão da gramática do parser
  - Estudo das estruturas de dados do parser

- **Próximos Passos**:
  1. Aprofundar conhecimento em Flex/Bison
  2. Estudar tipos de dados COBOL e suas integrações
  3. Compreender o sistema de host variables

### Principais Descobertas
1. **Estruturas de Dados Críticas**:
   - `cb_field`: Gerenciamento de campos COBOL
   - `cb_exec_list`: Controle de execução SQL
   - Sistema de host references

2. **Tipos de Dados Suportados**:
   - COMP-1, COMP-2, COMP-3, COMP-5
   - PIC X VARYING
   - National character support

3. **Funcionalidades SQL**:
   - SELECT INTO
   - FETCH
   - PREPARE
   - EXECUTE
   - Cursor management

### Desafios Identificados
1. Complexidade da gramática do parser
2. Integração entre tipos COBOL e SQL
3. Gerenciamento de memória em estruturas complexas

## 1. Fundamentos e Pré-requisitos
### 1.1 Ambiente Unix/Linux
- [x] Comandos básicos do terminal
- [x] Gerenciamento de processos
- [x] Permissões de arquivos
- [x] Variáveis de ambiente
- [x] Shell scripting básico

### 1.2 Compilação e Build
- [ ] Entender o processo de compilação
- [ ] Makefile e GNU Make
  - [ ] Sintaxe básica
  - [ ] Regras e dependências
  - [ ] Variáveis e macros
  - [ ] Debugging de Makefiles
- [ ] Flex e Bison
  - [ ] Análise léxica com Flex
  - [ ] Arquivos .l (lex)
  - [ ] Análise sintática com Bison
    - [ ] Gramáticas BNF
    - [ ] Resolução de conflitos
    - [ ] Actions e tipos semânticos
    - [ ] Manipulação de tokens
  - [ ] Integração Flex/Bison
  - [ ] Debugging de parsers
  - [ ] Tratamento de erros no parser

## 2. Integração de Linguagens
### 2.1 COBOL Avançado
- [ ] Estruturas de dados em COBOL
  - [ ] PICTURE clauses e tipos de dados
  - [ ] USAGE clauses (COMP-1, COMP-2, COMP-3, COMP-5)
  - [ ] SIGN clauses (LEADING/TRAILING)
  - [ ] OCCURS clause para arrays
- [ ] Host Variables
  - [ ] Declaração e escopo
  - [ ] Tipos suportados
  - [ ] Conversão de tipos
- [ ] Embedded SQL
  - [ ] Sintaxe básica
  - [ ] Cursores
  - [ ] Prepared statements
  - [ ] Dynamic SQL
- [ ] Debugging COBOL-SQL
  - [ ] Trace de SQL
  - [ ] Debugging de host variables
  - [ ] Análise de erros de sintaxe

### 2.2 Parser Development
- [ ] Estruturas de Dados do Parser
  - [ ] cb_field e gerenciamento de campos
  - [ ] cb_exec_list para contexto de execução
  - [ ] Listas encadeadas e árvores
- [ ] Processamento de Tipos
  - [ ] Validação de tipos
  - [ ] Conversão entre COBOL e SQL
  - [ ] Tratamento de tipos especiais
- [ ] Gerenciamento de Memória
  - [ ] Alocação de estruturas
  - [ ] Limpeza de recursos
  - [ ] Prevenção de memory leaks

## 3. SQL e Integração de Banco de Dados
### 3.1 Comandos SQL
- [ ] SELECT INTO
- [ ] FETCH
- [ ] PREPARE
- [ ] EXECUTE
- [ ] CONNECT
- [ ] Cursores
  - [ ] Declaração
  - [ ] Operações (OPEN, FETCH, CLOSE)
  - [ ] Scrollable cursors

### 3.2 Tratamento de Dados
- [ ] Host References
  - [ ] Sintaxe e uso
  - [ ] Validação de tipos
  - [ ] Arrays e estruturas
- [ ] Varying Length Data
  - [ ] VARYING clause
  - [ ] PIC X VARYING
  - [ ] National character support

## 4. Segurança e Otimização
### 4.1 Segurança
- [ ] SQL Injection
- [ ] Buffer Overflows
- [ ] Memory Leaks
- [ ] Permissões e autenticação
- [ ] Logging e auditoria

### 4.2 Performance
- [ ] Otimização de Parser
  - [ ] Redução de conflitos
  - [ ] Otimização de regras
  - [ ] Cache de símbolos
- [ ] Otimização de SQL
  - [ ] Prepared statements
  - [ ] Batch processing
  - [ ] Connection pooling

## 5. Testes e Qualidade
- [ ] Testes de Parser
  - [ ] Testes de gramática
  - [ ] Testes de tipos
  - [ ] Testes de host variables
- [ ] Testes de SQL
  - [ ] Validação de queries
  - [ ] Testes de cursores
  - [ ] Testes de prepared statements

## 6. Deployment e Produção
- [ ] Ambiente de desenvolvimento
- [ ] Ambiente de teste
- [ ] Ambiente de produção
- [ ] Monitoramento
- [ ] Backup e disaster recovery

## Como Usar Este Guia

1. Marque os itens que você já domina
2. Para cada item não marcado:
   - Crie um prompt específico para aprender sobre o tópico
   - Solicite exemplos práticos
   - Peça exercícios relacionados
   - Documente seu aprendizado

3. Para cada seção, antes de avançar:
   - Certifique-se de entender os conceitos básicos
   - Faça exercícios práticos
   - Documente problemas e soluções encontradas

## Exemplo de Prompt para Aprendizado

Para aprender sobre um tópico específico, use o formato:
```
"Preciso entender melhor [TÓPICO]. 
Contexto atual: [ONDE ESTOU NO PROJETO]
Conhecimento prévio: [O QUE JÁ SEI]
Objetivo: [O QUE PRECISO FAZER]
Dúvidas específicas: [LISTAR DÚVIDAS]"
```

## Acompanhamento de Progresso

Para cada tópico concluído:
- [ ] Entendi os conceitos fundamentais
- [ ] Realizei exercícios práticos
- [ ] Documentei o aprendizado
- [ ] Apliquei no projeto
- [ ] Identifiquei pontos de melhoria

---

*Nota: Este é um documento vivo que deve ser atualizado conforme seu progresso e necessidades específicas do projeto.*

## Exercícios Práticos

### Parser
1. Modificar gramática para suportar novo tipo de comando SQL
2. Adicionar validação de tipos para novo USAGE
3. Implementar tratamento de erro personalizado
4. Otimizar regras de gramática existentes

### SQL
1. Implementar novo tipo de cursor
2. Criar prepared statement com arrays
3. Adicionar suporte a novo tipo de dado
4. Otimizar query com host variables 



em Scanner.l foi alterado: 
// Remover ou comentar
// %option reentrant
// %option prefix="yy"

// Manter apenas
%option noyywrap
%option 8bit
%option caseless
%option never-interactive
%option yylineno
%option stack