# Análise do Problema com Open-COBOL-ESQL

## Controle de Versão

| Versão | Data       | Descrição das Alterações                                  | Autor |
|--------|------------|----------------------------------------------------------|-------|
| 1.0.0  | 2024-03-20| Versão inicial - Documentação do problema e solução LD_PRELOAD | - |
| 1.1.0  | 2024-03-21| Adição da documentação do wrapper script                  | - |
| 1.1.1  | 2024-03-21| Atualização do status do projeto e marcos                 | - |

### Convenção de Versionamento

Utilizamos o versionamento semântico (MAJOR.MINOR.PATCH):
- MAJOR: Mudanças incompatíveis
- MINOR: Adições de funcionalidade compatíveis
- PATCH: Correções de bugs e pequenas melhorias

## Sobre este Documento

Este documento combina elementos de vários formatos de documentação técnica:

### 1. ADR (Architectural Decision Record)
- **Status**: Aceito e Implementado
- **Contexto**: Problema de linkagem em sistema COBOL-SQL
- **Decisão**: Uso de LD_PRELOAD como solução
- **Consequências**: Documentadas na seção de impactos

#### Relação com ADR Padrão
Este documento expande o formato tradicional de ADR incluindo:
- Histórico detalhado de investigação
- Documentação de tentativas e erros
- Guia de implementação
- Monitoramento de status

### 2. Troubleshooting Guide
- Diagnóstico passo a passo
- Soluções testadas
- Resultados documentados
- Procedimentos de verificação

### 3. Technical Documentation
- Especificações do ambiente
- Requisitos do sistema
- Procedimentos de configuração
- Guias de manutenção

### 4. Project Status Report
- Estado atual do projeto
- Marcos alcançados
- Próximos passos
- Problemas conhecidos

### Propósito do Documento

1. **Registro Histórico**
   - Documentar decisões arquiteturais
   - Manter histórico de problemas e soluções
   - Registrar evolução do projeto

2. **Guia Operacional**
   - Procedimentos de implementação
   - Troubleshooting
   - Manutenção do sistema

3. **Conhecimento Base**
   - Transferência de conhecimento
   - Treinamento de novos membros
   - Referência técnica

4. **Gestão de Projeto**
   - Acompanhamento de progresso
   - Identificação de riscos
   - Planejamento futuro

### Manutenção do Documento

Este documento deve ser atualizado quando:
- Novas decisões arquiteturais são tomadas
- Problemas significativos são encontrados
- Soluções alternativas são implementadas
- Mudanças no ambiente de desenvolvimento

## Histórico do Projeto

### Fase 1: Desenvolvimento Inicial
- Criação do programa COBOL para interação com PostgreSQL
- Implementação inicial focada em operações CRUD
- Tentativas iniciais de compilação e execução

### Fase 2: Identificação de Problemas
1. Primeiro problema: Erro de linkagem com libocesql
2. Tentativas de ajuste no código COBOL
3. Verificação de dependências e bibliotecas

### Fase 3: Investigação e Diagnóstico
1. Análise do parser (ocesql/parser.y)
2. Verificação do arquivo disconnectsql.cob
3. Simplificação do código para teste de conexão
4. Identificação do problema com OCESQLConnect

### Fase 4: Resolução
1. Descoberta da solução usando LD_PRELOAD
2. Validação da solução
3. Documentação do processo

## Estado Atual do Projeto

### Componentes Principais
1. **Programa Principal**: `FETCHTBL.cbl`
   - Localização: `sample/FETCHTBL.cbl`
   - Função: Teste de conexão com PostgreSQL
   - Estado: Funcional com LD_PRELOAD

2. **Biblioteca OCESQL**:
   - Versão: 1.4
   - Localização: `/usr/local/lib/libocesql.so`
   - Estado: Instalada e funcional

3. **Banco de Dados**:
   - Tipo: PostgreSQL
   - Database: cobolbd
   - Usuário: server
   - Estado: Configurado e acessível

### Ambiente de Desenvolvimento
- Sistema Operacional: Linux (win32 10.0.26100)
- GnuCOBOL: versão 3.1.2.0
- Workspace: vscode-remote://ssh-remote+servidor/home/server/Open-COBOL-ESQL-1.4

### Progresso Atual
1. ✓ Instalação do ambiente
2. ✓ Configuração do GnuCOBOL
3. ✓ Instalação do Open-COBOL-ESQL
4. ✓ Configuração do PostgreSQL
5. ✓ Desenvolvimento do programa base
6. ✓ Resolução do problema de linkagem
7. ✓ Implementação de wrapper script
8. □ Pendente: Testes extensivos
9. □ Pendente: Documentação final

## Marcos do Desenvolvimento

### Marcos Concluídos
1. ✓ Configuração inicial do ambiente
2. ✓ Primeira compilação bem-sucedida
3. ✓ Identificação do problema de linkagem
4. ✓ Solução do problema com LD_PRELOAD
5. ✓ Documentação do processo
6. ✓ Implementação do wrapper script

### Próximos Marcos
1. □ Testes de integração
2. □ Documentação técnica completa
3. □ Deploy em produção

## Decisões Técnicas Importantes

### Decisões Tomadas
1. Uso de LD_PRELOAD para resolver problema de linkagem
2. Simplificação do código para isolamento do problema
3. Manutenção da estrutura original do projeto
4. Desenvolvimento de wrapper script para automação

### Alternativas Consideradas
1. Recompilação da biblioteca com flags diferentes
2. Modificação do código fonte
3. Uso de variáveis de ambiente alternativas

### Razões das Escolhas
1. LD_PRELOAD: Solução menos invasiva
2. Manutenção da compatibilidade
3. Facilidade de implementação

## Problemas Conhecidos e Status

### Resolvidos
1. ✓ Erro de linkagem com OCESQLConnect
2. ✓ Problemas de path da biblioteca
3. ✓ Questões de compilação

### Em Investigação
1. ⚡ Performance com LD_PRELOAD
2. ⚡ Impacto em outros módulos
3. ⚡ Compatibilidade com outros sistemas

### Pendentes
1. □ Otimização de performance
2. □ Testes de carga
3. □ Documentação de API

## Dependências e Requisitos

### Sistema
- Linux com suporte a 64 bits
- GnuCOBOL 3.1.2.0 ou superior
- PostgreSQL instalado e configurado
- Acesso root para instalação de bibliotecas

### Bibliotecas
- libocesql.so
- libcob.so
- libpq.so (PostgreSQL)

### Configuração
- Diretório de trabalho: /home/server/Open-COBOL-ESQL-1.4
- Path das bibliotecas: /usr/local/lib
- Arquivos de include: /home/server/Open-COBOL-ESQL-1.4/copy

## Contexto

Estamos trabalhando com o Open-COBOL-ESQL (ocesql), uma extensão para GnuCOBOL que permite a execução de comandos SQL embutidos em programas COBOL. O objetivo é estabelecer uma conexão com um banco de dados PostgreSQL através de um programa COBOL.

## Estrutura do Código Original

O programa COBOL (`FETCHTBL.cbl`) foi inicialmente desenvolvido com a seguinte estrutura:

```cobol
IDENTIFICATION DIVISION.
PROGRAM-ID. FETCHTBL.

ENVIRONMENT DIVISION.
CONFIGURATION SECTION.
SPECIAL-NAMES.
    DECIMAL-POINT IS COMMA.

DATA DIVISION.
WORKING-STORAGE SECTION.
EXEC SQL BEGIN DECLARE SECTION END-EXEC.
01  DBNAME                  PIC  X(30) VALUE SPACE.
01  USERNAME                PIC  X(30) VALUE SPACE.
01  PASSWD                  PIC  X(10) VALUE SPACE.
EXEC SQL END DECLARE SECTION END-EXEC.

EXEC SQL INCLUDE SQLCA END-EXEC.[]
```

### Principais Componentes
- Declaração de variáveis para conexão com banco de dados
- Inclusão do SQLCA (SQL Communications Area)
- Lógica de conexão e desconexão com o banco
- Tratamento de erros SQL

## Processo de Compilação e Execução

### Usando o Wrapper Script

Para simplificar o processo de compilação e execução, foi desenvolvido um wrapper script (`cobol-compile.sh`) que automatiza todas as etapas necessárias:

1. **Instalação do Wrapper**:
   ```bash
   # Copie o script para a pasta do projeto
   cp cobol-compile.sh /caminho/do/seu/projeto/
   
   # Torne o script executável
   chmod +x cobol-compile.sh
   ```

2. **Uso do Wrapper**:
   ```bash
   # Compilar e executar um programa
   ./cobol-compile.sh seu_programa.cbl
   
   # Limpar arquivos temporários, compilar e executar
   ./cobol-compile.sh seu_programa.cbl -c
   ```

3. **Funcionalidades do Wrapper**:
   - Pré-processamento automático com ocesql
   - Compilação com GnuCOBOL e flags corretas
   - Configuração automática do LD_PRELOAD
   - Limpeza de arquivos temporários
   - Verificação de dependências
   - Mensagens de status coloridas e claras

4. **Benefícios**:
   - Elimina a necessidade de lembrar comandos complexos
   - Garante consistência na compilação
   - Configura automaticamente o ambiente
   - Reduz erros de digitação
   - Facilita o desenvolvimento

### Processo Manual (Alternativa)

Se necessário, o processo também pode ser realizado manualmente em duas etapas:

1. Pré-processamento com ocesql:
```bash
ocesql sample/FETCHTBL.cbl sample/FETCHTBL.cbl.pre
```

2. Compilação com GnuCOBOL:
```bash
cobc -x -o sample/FETCHTBL sample/FETCHTBL.cbl.pre -I/home/server/Open-COBOL-ESQL-1.4/copy -L/usr/local/lib -locesql
```

3. Execução com LD_PRELOAD:
```bash
LD_PRELOAD=/usr/local/lib/libocesql.so ./FETCHTBL
```

## Tentativas de Solução

### 1. Simplificação do Código
Reduzimos o código para testar apenas a conexão, removendo todas as operações SQL complexas:
- Mantivemos apenas as variáveis essenciais
- Focamos apenas no OCESQLConnect e OCESQLDisconnect
- Adicionamos mensagens de diagnóstico claras

### 2. Ajustes nos Parâmetros de Compilação
Tentamos diferentes combinações de flags de compilação:
- Inclusão do diretório de cópias (-I)
- Especificação do diretório de bibliotecas (-L)
- Linkagem com a biblioteca ocesql (-locesql)

### 3. Verificação da Estrutura do Programa
- Validamos a sintaxe COBOL
- Confirmamos a correta declaração das variáveis
- Verificamos a ordem das chamadas SQL

## Problema Atual

O principal problema persiste: o executável não consegue encontrar o módulo `OCESQLConnect`:

```
*** TEST CONNECT STARTED ***
libcob: error: module 'OCESQLConnect' not found
```

### Possíveis Causas
1. **Instalação da Biblioteca**: A `libocesql` pode não estar instalada corretamente
2. **Problemas de Path**: O sistema pode não estar encontrando a biblioteca em tempo de execução
3. **Linkagem**: Possível problema na linkagem dinâmica da biblioteca

## Resultados das Verificações

### Pré-processamento
O ocesql gera corretamente as chamadas:
```
Generate:OCESQLConnect
Generate:OCESQLDisconnect
```

### Compilação
A compilação ocorre sem erros, mas com um aviso sobre `_FORTIFY_SOURCE`:
```
<command-line>: warning: "_FORTIFY_SOURCE" redefined
```

### Verificação da Biblioteca
Localização e permissões dos arquivos da biblioteca:
```bash
# Arquivos encontrados
/usr/local/lib/libocesql.la
/usr/local/lib/libocesql.a
/usr/local/lib/libocesql.so.0
/usr/local/lib/libocesql.so
/usr/local/lib/libocesql.so.0.1.0

# Permissões
-rw-r--r-- 1 root   root   143756 Apr 21 10:37 /usr/local/lib/libocesql.a
-rwxr-xr-x 1 root   root      956 Apr 21 10:37 /usr/local/lib/libocesql.la
lrwxrwxrwx 1 root   root       18 Apr 21 10:37 /usr/local/lib/libocesql.so
lrwxrwxrwx 1 root   root       18 Apr 21 10:37 /usr/local/lib/libocesql.so.0
-rwxr-xr-x 1 server server 102360 Apr 21 10:37 /usr/local/lib/libocesql.so.0.1.0
```

### Verificação das Variáveis de Ambiente
```bash
# Variáveis de ambiente
LD_LIBRARY_PATH=
COBOL_LIBRARY_PATH=
COB_LIBRARY_PATH=

# Cache de bibliotecas do sistema (ldconfig)
libocesql.so.0 (libc6,x86-64) => /usr/local/lib/libocesql.so.0
libocesql.so (libc6,x86-64) => /usr/local/lib/libocesql.so
```

Observações sobre as variáveis de ambiente:
1. Nenhuma das variáveis de ambiente está configurada (LD_LIBRARY_PATH, COBOL_LIBRARY_PATH, COB_LIBRARY_PATH)
2. No entanto, a biblioteca `libocesql` está corretamente registrada no cache do sistema (ldconfig)
3. O sistema pode encontrar a biblioteca através do cache do ldconfig, mas o GnuCOBOL pode estar procurando em locais específicos

### Versões do Software
- GnuCOBOL: versão 3.1.2.0
- Open-COBOL-ESQL: versão 1.4 (baseado no diretório do projeto)

Observações sobre a verificação:
1. A biblioteca `libocesql` está corretamente instalada em `/usr/local/lib`
2. Todos os arquivos necessários estão presentes (`.so`, `.la`, `.a`)
3. As permissões estão corretas (executável para `.so` e `.la`)
4. Os links simbólicos estão configurados adequadamente
5. A versão do GnuCOBOL é compatível com o Open-COBOL-ESQL

### Análise de Carregamento de Biblioteca e Erros

#### Dependências do Executável
```bash
linux-vdso.so.1
/usr/lib/x86_64-linux-gnu/libodbc.so
libcob.so.4 => /lib/x86_64-linux-gnu/libcob.so.4
libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6
# ... outras dependências ...
```
Observação: A `libocesql.so` não aparece na lista de dependências do executável!

#### Símbolos na Biblioteca libocesql
```bash
00000000000087f0 T OCESQLConnect
00000000000008ba0 T OCESQLConnectInformal
00000000000008970 T OCESQLConnectShort
```
Observação: Os símbolos OCESQLConnect existem e estão exportados corretamente na biblioteca.

#### Símbolos no Executável
```bash
00000000000041c0 b call_OCESQLConnect.5
```
Observação: O executável tem uma referência ao OCESQLConnect, mas como um símbolo não resolvido.

#### Diagnóstico do Problema
1. A biblioteca `libocesql.so` não está sendo linkada corretamente ao executável
2. Os símbolos OCESQLConnect existem na biblioteca, mas não estão sendo resolvidos
3. O executável está procurando o símbolo, mas não consegue encontrá-lo em tempo de execução
4. Possível problema na ordem de linkagem ou flags de compilação

## Próximos Passos Sugeridos

1. ~~Verificar a instalação da biblioteca libocesql~~ (CONCLUÍDO)
2. ~~Validar variáveis de ambiente~~ (CONCLUÍDO)
3. ~~Analisar logs do sistema~~ (CONCLUÍDO):
   - ~~Mensagens de erro detalhadas~~ ✓
   - ~~Problemas de carregamento de biblioteca~~ ✓

4. Novas Ações Corretivas Sugeridas:
   a. Modificar o comando de compilação para forçar a linkagem:
      ```bash
      cobc -x -o sample/FETCHTBL sample/FETCHTBL.cbl.pre -I/home/server/Open-COBOL-ESQL-1.4/copy -L/usr/local/lib -locesql -Wl,-rpath=/usr/local/lib
      ```
   
   b. Verificar se o módulo está registrado corretamente no GnuCOBOL:
      ```bash
      cobcrun --info
      ```
   
   c. Tentar compilação com flags adicionais de debug:
      ```bash
      cobc -v -x -o sample/FETCHTBL sample/FETCHTBL.cbl.pre -I/home/server/Open-COBOL-ESQL-1.4/copy -L/usr/local/lib -locesql
      ```

5. Verificar a compatibilidade (PENDENTE):
   - Versão do GnuCOBOL
   - Versão do Open-COBOL-ESQL
   - Arquitetura do sistema (32/64 bits)

## Conclusões Atualizadas

O problema parece estar relacionado à linkagem dinâmica da biblioteca. Embora a biblioteca esteja instalada e os símbolos existam, há uma falha na resolução dos símbolos em tempo de execução. Isso pode ser causado por:

1. Falta de flags apropriadas durante a compilação
2. Problemas na configuração do loader dinâmico
3. Incompatibilidade entre as versões do GnuCOBOL e Open-COBOL-ESQL
4. Possível necessidade de recompilar a biblioteca com flags específicas

Este documento será útil para:
- Documentação do problema
- Base para futuras investigações
- Referência para problemas similares
- Suporte à comunidade Open-COBOL-ESQL 

### Análise do Processo de Compilação Detalhado

```bash
cobc (GnuCOBOL) 3.1.2.0
Built     Apr 14 2024 07:59:15
Packaged  Dec 23 2020 12:04:58 UTC
C version "13.2.0"
```

#### Etapas do Processo
1. Pré-processamento: 
   ```bash
   sample/FETCHTBL.cbl.pre -> /tmp/cob14284_0.cob
   ```

2. Compilação C:
   ```bash
   gcc -c -finline-functions -D_FORTIFY_SOURCE=2 -ggdb3 -pipe
       -Wdate-time -D_FORTIFY_SOURCE=3 -Wno-unused -fsigned-char
       -Wno-pointer-sign -I"/home/server/Open-COBOL-ESQL-1.4/copy"
       -o "/tmp/cob14284_0.o" "/tmp/cob14284_0.c"
   ```

3. Linkagem:
   ```bash
   gcc -Wl,--export-dynamic -o "sample/FETCHTBL"
       "/tmp/cob14284_0.o" -Wl,-Bsymbolic-functions -flto=auto
       -ffat-lto-objects -Wl,-z,relro -L"/usr/local/lib"
       -L/usr/lib/x86_64-linux-gnu -lcob -lm -l"ocesql"
   ```

#### Observações Importantes
1. O GCC está usando otimizações LTO (Link Time Optimization)
2. A biblioteca ocesql está sendo linkada corretamente (-locesql)
3. O caminho da biblioteca está correto (-L"/usr/local/lib")
4. Flags de segurança estão ativas (_FORTIFY_SOURCE)

#### Novas Descobertas
1. A flag `-Wl,-rpath` não é suportada diretamente pelo `cobc`
2. O processo de compilação está correto e completo
3. O problema parece estar na resolução dinâmica de símbolos em tempo de execução

## Próximos Passos Atualizados

1. ~~Verificar a instalação da biblioteca libocesql~~ (CONCLUÍDO)
2. ~~Validar variáveis de ambiente~~ (CONCLUÍDO)
3. ~~Analisar logs do sistema~~ (CONCLUÍDO)
4. ~~Análise do processo de compilação~~ (CONCLUÍDO)
5. ~~Análise do carregamento de bibliotecas~~ (CONCLUÍDO)

6. Novas Ações Corretivas Prioritárias:

   a. Verificar se a biblioteca pode ser carregada manualmente:
      ```bash
      LD_PRELOAD=/usr/local/lib/libocesql.so ./FETCHTBL
      ```

   b. Recompilar a biblioteca com flags de visibilidade:
      ```bash
      make clean
      ./configure CFLAGS="-fvisibility=default"
      make
      sudo make install
      ```

   c. Verificar a configuração do GnuCOBOL para módulos:
      ```bash
      cobcrun --info
      cobcrun --runtime-conf
      ```

   d. Tentar criar um wrapper em C para testar o carregamento:
      ```c
      #include <dlfcn.h>
      void *handle = dlopen("/usr/local/lib/libocesql.so", RTLD_NOW);
      ```

7. Investigação de Configuração do Sistema:
   - Verificar /etc/ld.so.conf.d/
   - Confirmar cache do ldconfig
   - Verificar permissões do diretório /usr/local/lib

## Conclusões Atualizadas

O problema está claramente identificado como uma falha no carregamento dinâmico da biblioteca libocesql. As causas prováveis são:

1. A biblioteca não está sendo reconhecida como uma dependência necessária
2. Problema na exportação de símbolos da biblioteca
3. Configuração incorreta do loader dinâmico
4. Possível incompatibilidade na forma como o GnuCOBOL carrega módulos externos

Este documento será útil para:
- Documentação do problema
- Base para futuras investigações
- Referência para problemas similares
- Suporte à comunidade Open-COBOL-ESQL 

## Resolução do Problema

### Solução Encontrada
O problema foi resolvido usando `LD_PRELOAD` para garantir o carregamento da biblioteca:
```bash
LD_PRELOAD=/usr/local/lib/libocesql.so ./FETCHTBL
```

Resultado bem-sucedido:
```
*** TEST CONNECT STARTED ***
*** Connection successful! ***
*** TEST CONNECT FINISHED ***
```

### Guia de Implementação

#### 1. Preparação do Ambiente
1. Verificar instalação do GnuCOBOL:
   ```bash
   cobc --version  # Deve mostrar versão 3.1.2.0 ou superior
   ```

2. Verificar instalação do Open-COBOL-ESQL:
   ```bash
   ls -l /usr/local/lib/libocesql*  # Deve mostrar as bibliotecas
   ```

3. Configurar variáveis de ambiente (opcional, mas recomendado):
   ```bash
   export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
   export COB_LIBRARY_PATH=/usr/local/lib:$COB_LIBRARY_PATH
   ```

#### 2. Processo de Compilação
1. Pré-processamento do arquivo COBOL:
   ```bash
   ocesql arquivo.cbl arquivo.cbl.pre
   ```

2. Compilação do programa:
   ```bash
   cobc -x -o executavel arquivo.cbl.pre -I/home/server/Open-COBOL-ESQL-1.4/copy -L/usr/local/lib -locesql
   ```

#### 3. Execução do Programa
Duas opções disponíveis:

a. **Usando LD_PRELOAD (Recomendado)**:
   ```bash
   LD_PRELOAD=/usr/local/lib/libocesql.so ./executavel
   ```

b. **Script Wrapper (Alternativa)**:
   Criar um arquivo `run_cobol.sh`:
   ```bash
   #!/bin/bash
   LD_PRELOAD=/usr/local/lib/libocesql.so $@
   ```
   Tornar executável e usar:
   ```bash
   chmod +x run_cobol.sh
   ./run_cobol.sh ./executavel
   ```

### Solução de Problemas Comuns

1. **Erro: módulo 'OCESQLConnect' não encontrado**
   - Verificar se libocesql.so está em /usr/local/lib
   - Usar LD_PRELOAD conforme descrito acima
   - Verificar permissões da biblioteca

2. **Erro de compilação**
   - Verificar paths no -I e -L
   - Confirmar que SQLCA está incluído
   - Verificar sintaxe SQL no código COBOL

3. **Erro de conexão com banco**
   - Verificar credenciais no código
   - Confirmar que o banco está acessível
   - Verificar configuração do PostgreSQL

### Manutenção e Escalabilidade

1. **Versionamento**
   - Manter registro das versões das bibliotecas
   - Documentar mudanças nas configurações
   - Usar controle de versão para scripts

2. **Documentação**
   - Manter este documento atualizado
   - Documentar novas soluções encontradas
   - Registrar casos de uso bem-sucedidos

3. **Monitoramento**
   - Registrar erros de execução
   - Monitorar performance das conexões
   - Acompanhar uso de recursos

### Recomendações para Novos Desenvolvimentos

1. **Estrutura de Projeto**
   ```
   projeto/
   ├── src/
   │   └── *.cbl
   ├── bin/
   │   └── executaveis
   ├── scripts/
   │   └── run_cobol.sh
   └── README.md
   ```

2. **Práticas Recomendadas**
   - Sempre usar o script wrapper para execução
   - Manter backups dos arquivos fonte
   - Testar conexões antes de operações complexas
   - Implementar tratamento de erros adequado

3. **Checklist de Deployment**
   - [ ] Bibliotecas instaladas
   - [ ] Variáveis de ambiente configuradas
   - [ ] Script wrapper presente
   - [ ] Permissões corretas
   - [ ] Testes de conexão realizados

## Conclusão Final

O problema inicial de carregamento da biblioteca `libocesql` foi resolvido usando `LD_PRELOAD`. Esta solução:
1. É confiável e testada
2. Não requer modificações no código fonte
3. Pode ser facilmente automatizada
4. Funciona em diferentes ambientes

Para implementações futuras, recomenda-se:
1. Usar o script wrapper fornecido
2. Seguir o guia de implementação
3. Manter a documentação atualizada
4. Implementar o checklist de deployment

Este documento serve como referência completa para:
- Diagnóstico de problemas
- Implementação de soluções
- Manutenção do sistema
- Treinamento de novos desenvolvedores 