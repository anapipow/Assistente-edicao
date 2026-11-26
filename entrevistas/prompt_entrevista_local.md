Estou fazendo a cobertura da 13ª Mostra de Cinema de Gostoso (São Miguel do Gostoso, RN) para a **Cine Ninja**. Preciso que você trabalhe com uma entrevista gravada:

- **Arquivo:** `F:\2026 - 11 Mostra de Cinema de Gostoso\Vídeos\Osmo\DJI_20261124152757_0530_D.MP4`
- **Entrevistado:** Eryck Rocha, diretor do documentário **ELZA**
- **Pasta de saída:** crie `F:\2026 - 11 Mostra de Cinema de Gostoso\Entregas\Eryck Rocha\` e salve tudo lá. Nunca altere o arquivo original.

Se faltar FFmpeg, Python ou faster-whisper, rode antes `/preparar-computador` ou instale o que faltar (`pip install faster-whisper opencv-python-headless`).

## Etapa 1 — Análise (me mostre e espere minha aprovação)

1. **Transcreva** o áudio em português com faster-whisper (modelo `medium`, `word_timestamps=True`, `vad_filter=True`, `initial_prompt` com os nomes próprios: "Eryck Rocha, ELZA, Elza Soares, Mostra de Cinema de Gostoso, Cine Ninja"). Salve `transcricao.txt` com marcação de tempo [mm:ss] por frase, e guarde os tempos por palavra num JSON para usar nos cortes e nas legendas.
2. **Aspas:** de 6 a 10, numa tabela com: tempo, **fala literal** e **versão para card** (só ajeitando a sintaxe, sem mudar o sentido). Marque com ⭐ as 3 mais fortes.
3. **Cortes:** de 3 a 6 sugestões, cada um com **no máximo 1 minuto**. Todo corte começa no início de uma frase e termina no fim de uma ideia; nunca corte no meio. Dê um título curto, o tempo de início e fim, a duração e a ideia de cada corte. Indique o que pode ser descartado, como a conversa antes de a entrevista começar.
4. **Manchetes:** de 6 a 8 opções para card de notícia divulgando o filme, variando o ângulo: informativa, com aspa e curta.
5. **Pontos a checar:** nomes próprios, títulos e datas que a transcrição pode ter errado, e afirmações que dependem de confirmação.

## Etapa 2 — Cortes de vídeo (depois que eu aprovar)

Padrão dos vídeos para o carrossel do Instagram:
- **Formato 3:4, 1080×1440**, H.264 (`-crf 19`), 30 fps, áudio AAC 192k, com fade de 0,15s no começo e de 0,3s no fim. Se o original for 1920×1080, recorte uma janela de 810×1080 e escale.
- **Enquadramento:** o rosto do entrevistado precisa ficar centralizado o tempo todo. Faça o recorte acompanhar o rosto: detecte o rosto a cada 0,5s com OpenCV, descarte detecções absurdas (longe da mediana) e suavize o movimento, para a câmera não tremer.
  - Óculos escuros e contraluz enganam a detecção. **Sempre confira:** gere uma folha de contato de cada corte, com um quadro a cada 2 ou 3 segundos, e olhe. Se o rosto estiver fora do centro, marque a posição à mão a partir de quadros do vídeo original e refaça.
- **Os cortes não podem perder palavras:** confira nos tempos por palavra se a última palavra termina antes do fim do corte. Se precisar, estenda o corte por menos de 1 segundo.
- **Legenda embutida (arquivo .ass, gravado com o filtro `ass` do FFmpeg):**
  - fonte **Montserrat Bold** (peso 700). Se a fonte não estiver instalada, baixe do Google Fonts;
  - no .ass, use `PlayResX: 216`, `PlayResY: 288` e `Fontsize: 11`, o que dá cerca de 55 px de altura no vídeo de 1440;
  - texto branco, contorno preto de 0.7 e sombra de 0.3, centralizado embaixo, com `MarginV: 26`;
  - uma linha por vez, com até cerca de 30 caracteres. Quebre nas vírgulas e pontos quando der;
  - **maiúsculas:** a primeira palavra de cada corte começa com maiúscula, e depois de ponto, interrogação ou exclamação também;
  - **pontuação:** o último texto do corte termina com ponto final;
  - corrija nomes próprios e termos que a transcrição errar, mas mantenha a fala como foi dita.
- Nomeie os arquivos com número e título, por exemplo `1_titulo_do_corte.mp4`.

## Etapa 3 — Texto do post (quando eu pedir)

Escreva a legenda do carrossel do Instagram neste formato:
- **Primeiro parágrafo:** uma frase de abertura forte, **sem repetir aspas**, seguida de 🎬.
- **Contexto:** "Na 13ª Mostra de Cinema de Gostoso, a Cine Ninja conversou com…", com o nome em negrito e o filme em itálico.
- De 2 a 3 parágrafos curtos com as ideias principais, intercalando aspas curtas.
- No final: "▶️ Arrasta pro lado e assiste aos trechos da entrevista.", depois "📍 13ª Mostra de Cinema de Gostoso" e "🎥 Cobertura: Cine Ninja".
- De 6 a 9 hashtags, sempre incluindo #CineNinja e #MostraDeGostoso.
- Depois do texto, liste o que eu preciso confirmar antes de postar: informações que não estão na entrevista, nomes e @.

Regras gerais: escreva em português do Brasil e não invente fatos. Se algo não estiver na entrevista nem no que eu te passar, marque como "a confirmar".
