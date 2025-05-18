# Filmmaker Pro 🎵🎬🤖

**Versão:** 3.0 (Maio de 2025)
**Autor:** Leoni Santos "Belmot"

Bem-vindo ao **Filmmaker Pro**! Este projeto implementa um assistente criativo baseado em Inteligência Artificial que transforma letras de música em roteiros detalhados de videoclipe. Utilizando um sistema de dois agentes com a API Google Gemini e o Google ADK (Agent Development Kit), o Filmmaker Pro guia você desde a análise inicial da letra até um roteiro cena a cena.

## Visão Geral

O objetivo do Filmmaker Pro é auxiliar diretores, produtores e criadores de conteúdo a superar o bloqueio criativo e a estruturar suas ideias para videoclipes. Ele automatiza parte do processo de pré-produção, oferecendo:

1.  **Análise Profunda da Letra:** Compreensão de temas, emoções e palavras-chave.
2.  **Geração de Conceitos Criativos:** Múltiplas sinopses e sugestões visuais iniciais.
3.  **Desenvolvimento de Roteiro Detalhado:** Um roteiro cena a cena, refinado com base no feedback do usuário.

## Como Funciona: O Pipeline de Dois Agentes

O Filmmaker Pro utiliza uma arquitetura de dois agentes especializados para criar os roteiros:

1.  **Agente 1: ProdutorDeVideoclipes (Conceitualizador)**
    *   **Entrada:** Letra da música e informações contextuais opcionais (gênero musical, humor desejado, palavras-chave).
    *   **Tarefa:**
        *   Realizar uma análise detalhada da letra (emoção principal, temas, palavras-chave).
        *   Gerar 3 ideias de sinopses curtas para o videoclipe.
        *   Propor sugestões para o conceito visual (paleta de cores, atmosfera/estilo, locações, elementos simbólicos).
    *   **Saída:** Um relatório com a análise, sinopses e sugestões visuais.

2.  **Agente 2: RoteiristaRefinadorDetalhado (Roteirista Sênior)**
    *   **Entrada:** O output do Agente 1 e o feedback do usuário (qual sinopse focar, elementos adicionais desejados).
    *   **Tarefa:**
        *   Desenvolver UM roteiro de videoclipe coeso e elaborado, focado na direção fornecida pelo usuário.
        *   Estruturar o roteiro em cenas numeradas (INTRO, VERSO 1, REFRÃO, etc.).
        *   Para cada cena, detalhar: Cabeçalho, Descrição Visual, Ação, Elementos Simbólicos e Transições (opcional).
        *   Incluir considerações sobre figurino, maquiagem ou efeitos, se relevante.
    *   **Saída:** Um roteiro detalhado pronto para inspirar a produção.

## Recursos Principais

*   **Geração de Roteiros Baseada em IA:** Utiliza o poder do Google Gemini para criatividade e análise.
*   **Pipeline de Dois Agentes:** Um agente para ideias conceituais e outro para detalhamento, permitindo um processo iterativo com feedback do usuário.
*   **Entrada Flexível:** Aceita a letra da música e permite adicionar contexto para refinar as sugestões.
*   **Saída Estruturada:** Fornece análises, sinopses e um roteiro cena a cena formatado.
*   **Foco na Praticidade:** Gera ideias que visam ser inspiradoras e factíveis para produção.
*   **Construído com Google ADK:** Aproveita o Agent Development Kit para gerenciar os agentes.

## Tecnologias Utilizadas

*   **Linguagem:** Python
*   **Modelo de IA:** Google Gemini (especificamente `gemini-2.0-flash` como configurado no código, mas flexível através de `MODEL_ID`)
*   **Framework de Agentes:** Google Agent Development Kit (ADK) - `google.adk.agents`, `google.adk.runners`, `google.adk.sessions`
*   **SDK da API:** `google-generativeai`
*   **Ambiente de Execução Primário:** Google Colab (devido ao uso de `google.colab.userdata` e `IPython.display`)

## Pré-requisitos

*   Uma conta Google Cloud com a API do Google Gemini habilitada.
*   Sua `GOOGLE_API_KEY` configurada como um "Secret" no Google Colab com o nome `GOOGLE_API_KEY`.
*   Um ambiente Google Colab ou um ambiente Python 3.x com as bibliotecas necessárias instaladas.

## Configuração e Instalação

1.  **Obtenha o Código:**
    *   Clone este repositório ou copie o código do arquivo `Filmmaker-Pro2.py` (ou como você nomear) para um notebook do Google Colab.

2.  **Configure sua API Key:**
    *   No Google Colab, vá em "Secrets" (ícone de chave no painel esquerdo).
    *   Adicione um novo secret com o nome `GOOGLE_API_KEY` e cole sua chave de API como valor. Certifique-se de que "Notebook access" esteja habilitado para este secret.

3.  **Instale as Dependências (se não estiverem no Colab ou se executar localmente):**
    ```bash
    pip install google-generativeai google-adk
    # A biblioteca IPython é geralmente pré-instalada no Colab
    ```

## Como Usar

1.  Abra o notebook do Google Colab contendo o código do Filmmaker Pro.
2.  Execute a célula de código.
3.  Siga as instruções no output:
    *   Cole a letra da música. Quando terminar, pressione Enter, digite `FIM` em uma nova linha e pressione Enter novamente.
    *   Forneça informações opcionais: gênero musical, humor desejado e palavras-chave adicionais.
4.  Aguarde o **Agente 1 (ProdutorDeVideoclipes)** gerar as ideias iniciais. O output será exibido formatado em Markdown.
5.  Após a saída do Agente 1, você será solicitado a fornecer feedback para o **Agente 2 (RoteiristaRefinadorDetalhado)**:
    *   Indique qual sinopse ou tema principal deve ser o foco.
    *   Adicione qualquer feedback ou elementos específicos que gostaria de ver no roteiro refinado.
6.  Aguarde o Agente 2 gerar o roteiro detalhado, que também será exibido formatado.

## Exemplo de Fluxo de Saída (Conceitual)

1.  **Output do Agente 1:**
    ```markdown
    ## 1. Análise da Letra
    > Emoção principal: Saudade nostálgica
    > Temas: Passagem do tempo, memórias de infância, perda.
    > Palavras-chave: "ontem", "rio", "brincadeira", "adeus".

    ## 2. Ideias de Sinopses
    > * **Sinopse A:** Um adulto revisita sua casa de infância abandonada, e flashbacks mostram momentos felizes contrastando com a solidão presente.
    > * **Sinopse B:** Uma narrativa surreal onde o tempo flui de forma não linear, com o protagonista tentando recapturar momentos que escapam como água.
    > * **Sinopse C:** Uma performance da banda em um local que se transforma, refletindo as diferentes fases da vida mencionadas na letra.

    ## 3. Sugestões para o Conceito Visual
    > * **Paleta de Cores:** Tons sépia e dessaturados para o presente; cores vibrantes e quentes para os flashbacks.
    > * **Atmosfera/Estilo:** Sonhador, melancólico, com toques de realismo mágico.
    > * **Locações:** Casa antiga, campo aberto ao pôr do sol, um rio.
    > * **Elementos Simbólicos:** Relógio antigo, fotografias desbotadas, um barco de papel.
    ```

2.  **Output do Agente 2 (após feedback do usuário focando na Sinopse A):**
    ```markdown
    ## Roteiro do Videoclipe Detalhado

    **Título Provisório:** Ecos de Ontem

    **Logline:** Um homem confronta as memórias agridoces de sua infância ao retornar à sua casa abandonada, buscando um encerramento para o que se foi.

    ## Estrutura de Cenas

    **CENA 1 - EXT. CASA ABANDONADA - DIA (INTRO)**
    > **DESCRIÇÃO VISUAL:** Céu nublado. Uma casa de campo antiga, com pintura descascada e janelas quebradas. A natureza começa a tomar conta. Paleta dessaturada.
    > **AÇÃO:** CARLOS (40s), olhar cansado, aproxima-se lentamente da casa. Close no rosto dele, hesitação. Ele toca a maçaneta enferrujada.
    > **ELEMENTOS SIMBÓLICOS:** A casa como representação do passado.
    > **TRANSIÇÃO:** Corte rápido para um flash de cor vibrante (flashback).

    **CENA 2 - INT. CASA (PASSADO) - DIA (VERSO 1)**
    > **DESCRIÇÃO VISUAL:** A mesma casa, mas cheia de vida. Luz solar entra pelas janelas. Cores quentes e vibrantes.
    > **AÇÃO:** CARLOS CRIANÇA (8) corre pela sala, rindo, brincando com um pequeno barco de papel. Sua MÃE (30s) sorri da cozinha.
    > **ELEMENTOS SIMBÓLICOS:** Barco de papel (inocência, sonhos).
    > **TRANSIÇÃO:** Dissolve para a sala atual.

    **(Restante do roteiro segue com REFRÃO, VERSO 2, etc.)**

    ## Considerações Adicionais
    > * **Figurino:** Carlos adulto com roupas simples e escuras. Carlos criança com roupas coloridas.
    > * **Maquiagem:** Enfatizar o cansaço no rosto de Carlos adulto.
    ```

## Roadmap e Possíveis Melhorias

*   Criação de uma interface gráfica (Web ou Desktop) para facilitar a interação.
*   Opção de salvar/exportar os roteiros gerados em formatos como PDF ou Fountain.
*   Integração com APIs de geração de imagens (ex: Stable Diffusion, DALL-E) para gerar *storyboards* visuais conceituais para as cenas.
*   Permitir ao usuário escolher diferentes modelos Gemini ou ajustar parâmetros como temperatura.
*   Adicionar mais agentes especializados (ex: um agente para *breakdown* de produção, um para sugestões de trilha sonora complementar se a música for instrumental).
*   Suporte multilíngue para letras de música.

## Contribuindo

Contribuições são bem-vindas! Se você tiver ideias para melhorar o Filmmaker Pro, sinta-se à vontade para:
1.  Fazer um Fork do projeto.
2.  Criar sua Feature Branch (`git checkout -b feature/AmazingFeature`).
3.  Commitar suas mudanças (`git commit -m 'Add some AmazingFeature'`).
4.  Fazer o Push para a Branch (`git push origin feature/AmazingFeature`).
5.  Abrir um Pull Request.

## Licença

Este projeto é distribuído sob a Licença MIT. Veja o arquivo `LICENSE` para mais informações (você precisará criar este arquivo se quiser especificar uma).
