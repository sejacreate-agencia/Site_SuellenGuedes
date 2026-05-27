# 📘 Documentação do Site — Suellen Guedes Advogados

Guia completo para **editar textos**, **trocar fotos** e **publicar o site no Hostinger**.
Feito para ser entendido mesmo por quem nunca mexeu em HTML.

---

## 📁 Estrutura de arquivos

```
Site/
├── index.html             ← Página única do site (todo o conteúdo está aqui)
├── DOCUMENTACAO.md        ← Este guia
├── Imagens/               ← Fotos e logos usadas no site
│   ├── 1.jpeg             → HERO (foto principal de capa)
│   ├── 2.JPEG             → ESCRITÓRIO (foto da seção "sobre")
│   ├── 3.JPEG             → EQUIPE (card da Suellen)
│   ├── 4.JPEG             → EQUIPE (card da Jéssica)
│   ├── 5.JPEG             → CTA final (foto de fundo antes do rodapé)
│   ├── 68.png             → LOGO ESCURA (usada no menu quando branco e como favicon)
│   └── 69.png             → LOGO CLARA (usada no menu sobre fundo escuro e no rodapé)
├── Fotos/                 ← Fotos antigas (mantidas como reserva, opcional)
└── Referências/           ← Material de referência (não vai para o site)
```

> ⚠️ **Não renomeie** as pastas `Imagens`, `Fotos` e `Identidade Visual` — o HTML aponta para elas por nome.

---

## ✏️ Como editar textos

### Ferramenta recomendada

Abra `index.html` com **qualquer um destes**:

- [Visual Studio Code](https://code.visualstudio.com/) (gratuito, recomendado)
- Bloco de Notas (já vem no Windows)
- Notepad++

### Onde encontrar cada texto

Cada seção do site tem um comentário marcador no HTML. Procure por `<!-- ══ NOME ══ -->` (Ctrl+F).

| Seção visual | Marcador no HTML | Linha aprox. |
|---|---|---|
| Menu superior | `<!-- ══ NAV ══ -->` | ~615 |
| Capa (hero) | `<!-- ══ HERO ══ -->` | ~660 |
| Áreas de atuação | `<!-- ══ ÁREAS ══ -->` | ~700 |
| Escritório (sobre) | `<!-- ══ SOBRE ══ -->` | ~770 |
| Equipe | `<!-- ══ EQUIPE ══ -->` | ~830 |
| Depoimentos | `<!-- ══ DEPOIMENTOS ══ -->` | ~890 |
| CTA final (botão verde) | `<!-- ══ CTA ══ -->` | ~960 |
| Mini seção antes do rodapé | `<!-- ══ PRE-FOOTER ══ -->` | ~980 |
| Rodapé | `<!-- ══ FOOTER ══ -->` | ~995 |

### Regras de ouro ao editar

1. **Só altere o texto que aparece entre as tags.** Exemplo:
   ```html
   <h1>Defendemos direitos, mas cuidamos de pessoas.</h1>
        └──────────── ALTERE SÓ ESTA PARTE ──────────┘
   ```
2. **Nunca apague** os símbolos `<`, `>`, `</`, ou as aspas `"`.
3. Para destacar uma palavra em itálico dourado, envolva com `<em>palavra</em>`.
4. Para quebrar uma linha dentro de um título, use `<br>`.
5. Sempre **salve o arquivo** (Ctrl+S) e **abra no navegador** para conferir antes de publicar.

### Exemplos práticos

**Mudar a headline da capa:**
```html
<h1 class="anim fade-up d1">
  Defendemos direitos,<br>mas cuidamos de <em>pessoas</em>.
</h1>
```
Troque por:
```html
<h1 class="anim fade-up d1">
  Sua nova frase aqui,<br>com <em>destaque</em> em itálico.
</h1>
```

**Trocar o telefone do WhatsApp** (aparece em vários botões — use Localizar/Substituir Ctrl+H):
- Procurar: `5584991138600`
- Substituir por: `55XXNNNNNNNNN` (DDI + DDD + número, sem espaços)

**Trocar o e-mail:**
- Procurar: `suellenguedesadv@gmail.com`
- Substituir por: novo e-mail

**Trocar o Instagram:**
- Procurar: `suellennguedes`
- Substituir por: novo usuário

**Editar a biografia que abre ao clicar no card da advogada:**

Procure no final do arquivo, dentro do `<script>`, pelo bloco `const bios = {`. Cada advogada tem 4 campos:
```js
suellen: {
  name: 'Dra. Suellen Guedes',
  role: 'Advogada Trabalhista e Previdenciária · OAB/RN',
  photo: 'Imagens/3.JPEG',
  text: [
    'Primeiro parágrafo...',
    'Segundo parágrafo...',
    'Terceiro parágrafo...'
  ]
},
```
- **name**: nome que aparece no topo do modal.
- **role**: subtítulo (cargo + OAB).
- **photo**: caminho da foto que vai aparecer no lado esquerdo do modal.
- **text**: cada texto entre aspas vira um parágrafo. Para adicionar mais um parágrafo, é só adicionar uma nova linha terminada em vírgula.

**Editar a Política de Privacidade:**

A política aparece num modal quando clica no link "Política de privacidade" no rodapé.
Procure no JS pela função `openPrivacy()` — todo o texto está dentro de uma template string (entre crases ``).
Cada parágrafo `<p>…</p>` e cada subtítulo `<h4>…</h4>` pode ser editado livremente. Não apague as tags HTML.
**Importante:** se mudar e-mail ou WhatsApp em outras partes do site, lembre de atualizar também na seção 5, 7 da política.

**Editar/Adicionar um depoimento:**

Procure pelo marcador `<!-- ══ DEPOIMENTOS ══ -->`. Cada depoimento é um bloco `<div class="testi-card">…</div>`. Para trocar o texto:
```html
<p>"Texto do depoimento aqui."</p>
<div class="testi-author">
  <div class="testi-avatar">XY</div>   ← iniciais da pessoa
  <div class="testi-name">
    <strong>Nome do Cliente</strong>
    <span>Cliente atendida</span>
  </div>
</div>
```

**Alterar os números do contador animado da seção EQUIPE:**

Procure por `data-target="6"` (são os números que sobem de 0 até o valor):
```html
<span class="counter" data-target="6">0</span>
```
Mude o valor entre as aspas. Exemplos:
- `data-target="6"` → vira `data-target="10"` (passa a contar até 10).
- O `0` entre as tags é só o estado inicial; deixe como está.

Os 3 contadores atuais são: **6+ anos**, **2 áreas**, **100% atendimento humanizado**.

---

## 🖼️ Como trocar uma foto

1. Coloque a nova imagem dentro da pasta `Imagens/` (ou `Fotos/`).
2. Procure no `index.html` pelo nome da foto antiga (Ctrl+F).
3. Substitua pelo nome do novo arquivo.

**Exemplo — trocar foto do HERO:**
```html
<img src="Imagens/1.jpeg" alt="Suellen Guedes Advogada">
```
Para a nova foto chamada `nova-capa.jpg`:
```html
<img src="Imagens/nova-capa.jpg" alt="Suellen Guedes Advogada">
```

### Mapa das fotos do site

| Onde aparece | Caminho no HTML |
|---|---|
| HERO (capa) | `Imagens/1.jpeg` |
| ESCRITÓRIO (sobre) | `Imagens/2.JPEG` |
| Card Suellen (equipe) | `Imagens/3.JPEG` |
| Card Jéssica (equipe) | `Imagens/4.JPEG` |
| CTA final (fundo escuro) | `Imagens/5.JPEG` (dentro do CSS `.cta-bg`) |
| Logo escura (menu sobre branco e favicon) | `Imagens/68.png` |
| Logo clara (menu sobre escuro e rodapé) | `Imagens/69.png` |

### Boas práticas para fotos

- **Formato**: `.jpg` ou `.jpeg` (mais leves) ou `.png` para logos.
- **Tamanho máximo recomendado**: até 500 KB cada (use [tinypng.com](https://tinypng.com/) para comprimir).
- **Proporção**:
  - HERO e Escritório: **retrato** (vertical), mínimo 800×1200 px.
  - Equipe: **retrato**, mínimo 600×800 px.
  - CTA (fundo): **paisagem ou retrato grande**, mínimo 1200×800 px.
- Cuidado com **maiúsculas/minúsculas**: `1.jpeg` é diferente de `1.JPEG` no servidor.

---

## 🚀 Como publicar no Hostinger

O Hostinger oferece 3 jeitos. **O mais simples é pelo Gerenciador de Arquivos**.

### Opção 1 — Gerenciador de Arquivos (recomendado)

1. Entre em [hpanel.hostinger.com](https://hpanel.hostinger.com/).
2. No menu lateral, clique em **Sites** → escolha o domínio.
3. Vá em **Arquivos** → **Gerenciador de Arquivos**.
4. Abra a pasta **`public_html`** (é a raiz do site).
5. **Apague tudo que estiver dentro** dela (se for a primeira publicação, geralmente tem só um `default.php`).
6. Clique em **Upload** (ícone de seta para cima) e envie:
   - `index.html`
   - A pasta `Imagens/` inteira (contém todas as fotos **e** as logos)
   - A pasta `Fotos/` (apenas se ainda usar alguma foto antiga)
7. Aguarde o upload terminar.
8. Acesse o seu domínio no navegador — pronto. ✅

> 💡 Para enviar uma pasta inteira: compacte ela em `.zip` no seu PC, faça upload do `.zip` e use a opção **Extrair** dentro do Gerenciador de Arquivos.

### Opção 2 — FTP (FileZilla)

Mais prático se você for editar com frequência.

1. Baixe o [FileZilla](https://filezilla-project.org/).
2. No Hostinger, vá em **Avançado** → **Contas FTP** e crie/copie:
   - Servidor (host): `ftp.seudominio.com`
   - Usuário e senha de FTP
   - Porta: `21`
3. No FileZilla, conecte com esses dados.
4. À direita aparece o servidor — abra `public_html`.
5. À esquerda, navegue até a pasta `Site/` do seu computador.
6. **Arraste** os arquivos da esquerda para a direita.
7. Substitua quando perguntar.

### Opção 3 — Git (se souber usar)

```bash
git push hostinger main
```
Configure o webhook no painel do Hostinger em **Avançado** → **Git**.

---

## 🔄 Como atualizar o site depois de uma edição

1. Edite o `index.html` no seu PC.
2. Salve (Ctrl+S).
3. Teste localmente abrindo o arquivo no navegador (duplo clique).
4. Faça upload do **`index.html` atualizado** para `public_html/` (substitua o antigo).
5. Se trocou alguma foto, faça upload também da nova foto na pasta `Imagens/`.
6. Limpe o cache do navegador (Ctrl+F5) para ver as mudanças.

---

## 🌐 Conectar um domínio próprio

Se ainda usa o domínio temporário do Hostinger (algo tipo `seusite.hostingersite.com`):

1. No Hostinger, vá em **Domínios** → **Domínio Principal**.
2. Clique em **Alterar** e digite seu domínio comprado (ex: `suellenguedes.adv.br`).
3. Se comprou o domínio em outro lugar (Registro.br, GoDaddy etc.), aponte os DNS para os servidores do Hostinger:
   - `ns1.dns-parking.com`
   - `ns2.dns-parking.com`
4. Aguarde até 24h para propagar.

---

## 📞 Checklist final antes de publicar

- [ ] Todos os textos foram revisados (sem erros de digitação).
- [ ] Telefone do WhatsApp está correto em **todos** os botões.
- [ ] E-mail de contato está correto.
- [ ] Link do Instagram aponta para o perfil certo.
- [ ] Todas as fotos abrem corretamente quando você testa no navegador.
- [ ] Testou o site em **celular** (modo responsivo) e **desktop**.
- [ ] Clicou em todos os botões para garantir que abrem o WhatsApp.

---

## 🆘 Problemas comuns

| Problema | Solução |
|---|---|
| Foto não aparece | Verifique o nome do arquivo (maiúscula/minúscula) e a pasta. |
| Mudei o texto mas não aparece no site online | Limpe o cache: **Ctrl+F5** no navegador. |
| Site não abre depois de publicar | Confirme que o arquivo se chama exatamente `index.html` (tudo minúsculo). |
| Layout ficou quebrado | Você provavelmente apagou alguma tag `<` ou `>` sem querer. Restaure a versão anterior. |
| Acentos aparecem como `?` ou `Ã£` | Salve o arquivo com codificação **UTF-8** (no VS Code, canto inferior direito). |

---

## 📌 Identidade do site (referência rápida)

- **Cores principais** (definidas no CSS, variáveis `:root`):
  - Creme de fundo: `#F7F4EF`
  - Preto principal: `#1A1814`
  - Dourado (destaque): `#B8956A`
  - Dourado claro: `#D4B08C`
- **Fontes**:
  - Títulos: *Cormorant Garamond* (serifa elegante)
  - Textos: *DM Sans* (sem serifa, limpa)
- **Botão flutuante de WhatsApp**: sempre visível no canto inferior direito.

---

**Última atualização desta documentação:** 26 de maio de 2026

Para qualquer dúvida ou nova alteração, é só chamar a Seja Create. 💛
