# Misticismo Books — US Market Series Engine (RAG)

Este repositório contém a base estratégica e operacional para construir uma série de **10 livros** voltada ao mercado dos EUA, com foco em:

- continuidade narrativa entre volumes
- padronização editorial
- otimização de descoberta por busca conversacional (GEO)
- metadados e palavras-chave com potencial comercial

O projeto está estruturado para funcionar como uma **base RAG (Retrieval-Augmented Generation)**: você recupera contexto canônico + contexto específico do livro e gera outlines, capítulos, metadata e assets com consistência.

## Objetivo do projeto

Criar uma série híbrida (ficção mística + práticas integradas) com qualidade de franquia:

- cada livro funciona como standalone
- cada livro avança um arco macro contínuo
- cada volume responde a uma intenção de busca real do leitor US

## Estrutura de arquivos

```text
rag/
  series_rag_master.json
  retrieval_chunks.jsonl
  generation_playbook.json
  keyword_bank_us_2026.json
claude.txt
deep1.txt
```

### `rag/series_rag_master.json`

Fonte principal do canon da série:

- posicionamento da série no mercado US
- padrão de formato (páginas, split narrativa/prática, ritmo)
- entidades canônicas e regras não negociáveis de continuidade
- blueprint dos 10 livros:
  - tema central
  - keyword primária
  - keywords secundárias
  - intenção GEO por livro
  - posicionamento Amazon
  - direção visual de capa/estética

### `rag/retrieval_chunks.jsonl`

Base de recuperação em chunks curtos para pipeline RAG:

- chunks canônicos globais (`book_scope = all`)
- chunk de intenção por livro (`book_scope = 1..10`)
- chunks de estratégia de lançamento e produto físico

Formato JSONL facilita:

- indexação vetorial
- filtros por `book_scope`, `chunk_type`, `tags`
- atualização incremental sem reescrever arquivo inteiro

### `rag/generation_playbook.json`

Playbook operacional para geração:

- ordem recomendada de retrieval
- schema obrigatório para gerar cada livro
- checklist de validação de continuidade
- template de metadata GEO/Amazon (title/subtitle/description/backend keywords)
- sequência de lançamento comercial

### `rag/keyword_bank_us_2026.json`

Banco de palavras-chave organizado por cluster de intenção:

- Shadow & Integration
- Trauma-Informed Manifestation
- Somatic Spirituality
- Ritual & Symbol Practice
- Nature & Feminine Sovereignty

Inclui regras de uso para evitar keyword stuffing e melhorar conversão.

## Como usar este RAG na prática

## 1) Escolha o volume-alvo

Defina `book_number` (1 a 10).

## 2) Faça retrieval do contexto

Recupere nesta ordem:

1. chunks canônicos (`book_scope=all`)
2. chunk do livro (`book_scope=<book_number>`)
3. blueprint do livro no `series_rag_master.json`
4. cluster de keywords relevante no `keyword_bank_us_2026.json`

## 3) Gere estrutura editorial do livro

Use o schema de `generation_playbook.json` para produzir:

- premissa
- conflito interno e externo
- sistema simbólico/ritual
- plano de capítulos
- transformação final
- ponte para o próximo volume

## 4) Gere metadados de venda

Monte:

- título + subtítulo orientados por intenção
- descrição com pergunta real de leitor nos primeiros 180 caracteres
- backend keywords (long-tail, sem repetição de raiz)

## 5) Valide continuidade

Passe pelo checklist:

- consistência de voz e história psicológica da protagonista
- fechamento de 1 loop de ferida por volume
- abertura clara para o próximo livro
- linguagem trauma-aware e sem alegações médicas

## Estratégia recomendada de go-to-market

Sequência sugerida:

1. validar demanda com Livro 3 ou Livro 4 no Kindle
2. otimizar metadata por CTR e taxa de leitura
3. construir lista de e-mail com sample chapters
4. lançar edições físicas colecionáveis com diferenciação ritual (ex.: bordas, marcadores, QR)

## Padrões editoriais da série

- idioma de publicação: **en-US**
- foco geográfico: **US**
- faixa sugerida por volume: **280–320 páginas**
- composição de conteúdo: **70% narrativa / 30% práticas**
- tom: íntimo, místico, psicologicamente fundamentado

## Roadmap de produção dos 10 livros

Para cada volume:

1. outline mestre (24 capítulos)
2. escrita do manuscrito v1
3. QA de continuidade com canon
4. QA de keywords + metadata
5. capa e pacote visual alinhados ao tema do volume
6. publicação Kindle + coleta de linguagem de reviews para iteração

## Licença e uso

Uso editorial e operacional interno do projeto.
Se for abrir para colaboração pública, adicione uma licença formal antes de aceitar contribuições.
