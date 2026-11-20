# Portfólio — Luiz | Editor

Site estático de arquivo único (`index.html`), sem build e sem dependências (só a fonte Poppins via Google Fonts).

## O que tem

- Cabeçalho com foto circular, nome e frase de posicionamento
- Fundo preto com pontinhos discretos; perto do cursor (ou do toque) os pontos acendem em laranja
- Seção **Vídeos** (16:9) e seção **Shorts** (9:16)
- Miniatura em alta resolução (`maxresdefault`) com fallback automático para `hqdefault`
- Ao clicar (ou Enter/Espaço), a miniatura vira o player do YouTube **dentro do site**, já tocando
- Ícones de e-mail, Instagram e Discord (modal com botão "Copiar", fecha no X, fora ou com Esc)
- Seção "Minha história"
- Responsivo: vídeos em 1 coluna no celular, shorts em 2 colunas (1 em telas muito pequenas), sem rolagem horizontal

## Como editar

Abra o `index.html` em qualquer editor de texto.

**Vídeos e shorts** — no `<script>`, bloco `CONFIG`. Cole o link completo ou só o ID:

```js
long:   ['https://youtu.be/FFpIaHqa4WI', 'https://youtu.be/OUTRO_ID'],
shorts: ['https://youtube.com/shorts/ID_DO_SHORT'],
```

Espaços sem vídeo aparecem como "Em breve". Para mostrar mais cards, aumente `longSlots` / `shortSlots`.

**E-mail, Instagram e Discord** — também no `CONFIG` (`email`, `instagram`, `discord`). Para outra rede, copie o `<a id="insta" ...>` no HTML e troque o link e o ícone. Para remover um ícone, apague a linha dele (e o JS correspondente, se for o Discord).

**Textos** — procure no HTML: `<h1>` (nome e função), `.tagline` (frase), `<h2>Minha história</h2>` e o parágrafo abaixo dele.

**Foto** — gere o base64 da nova foto (quadrada, ~240×240, JPEG) e troque o conteúdo de `src="data:image/jpeg;base64,..."` na tag `<img class="avatar">`. Ou use um arquivo: `src="foto.jpg"` e coloque `foto.jpg` ao lado do `index.html`.

**Cores** — no topo do CSS, em `:root`:

```css
--bg:#0a0a0a;      /* fundo */
--text:#ffffff;    /* texto */
--accent:#ff6a00;  /* destaque */
--dot:rgba(255,255,255,.14); /* pontinhos */
```

Se mudar `--accent`, troque também `255,106,0` nos `rgba(...)` do CSS para a mesma cor em RGB.

## Publicar no GitHub

1. Crie uma conta em github.com e clique em **New repository** (ex.: `portfolio`), público.
2. Na página do repositório, clique em **uploading an existing file**.
3. Arraste `index.html` e `README.md` e clique em **Commit changes**.

(Pelo terminal: `git init`, `git add .`, `git commit -m "portfolio"`, `git branch -M main`, `git remote add origin URL_DO_REPO`, `git push -u origin main`.)

## Hospedar na Vercel

1. Entre em vercel.com com sua conta do GitHub.
2. **Add New → Project** e escolha o repositório `portfolio`.
3. Deixe **Framework Preset: Other**, sem build command e sem output directory.
4. Clique em **Deploy**. Em alguns segundos você recebe um link `https://seu-projeto.vercel.app`.
5. Para atualizar o site: edite o `index.html` no GitHub e faça commit — a Vercel publica sozinha.

## Dica

Se um vídeo não tocar dentro do site (erro 153 ou "incorporação desativada"), o dono do vídeo bloqueou a incorporação. Em Vercel/HTTPS o player funciona normalmente; abrir o `index.html` direto do computador (`file://`) pode dar erro no player do YouTube — teste sempre pelo link publicado.
