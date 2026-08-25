# E-mail marketing · Síndicos — ENERGIA A

Projeto estático pronto para deploy na Vercel. Serve dois propósitos:

1. **Hospedar a logo** em URL pública (`/logo-energia-a.png`) — o Gmail e o Outlook
   bloqueiam imagens em base64, então o e-mail precisa apontar para uma URL real.
2. **Servir a página "ver no navegador"** (`/`) — o mesmo layout do e-mail, para o
   link "não está vendo as imagens? abra no navegador" e para mandar por WhatsApp.

## Arquivos

| Arquivo | Para quê |
|---|---|
| `index.html` | Página pública (logo relativa `/logo-energia-a.png`) |
| `email-para-disparo.html` | **É este que você cola na ferramenta de e-mail** |
| `logo-energia-a.png` | Asset público da logo (versão branca, para o fundo navy) |
| `vercel.json` | Cache longo + CORS liberado na imagem |

## Deploy — opção 1: arrastar e soltar (mais rápido, sem instalar nada)

1. Acesse <https://vercel.com/new> e faça login.
2. Arraste a **pasta** `vercel-email-sindicos` para a área de upload
   (ou zipe e solte o `.zip`).
3. Nomeie o projeto, por exemplo `email-sindicos-energia-a`, e clique em **Deploy**.

## Deploy — opção 2: CLI

```bash
npm i -g vercel
cd vercel-email-sindicos
vercel --prod
```

## Depois do deploy — passo obrigatório

A Vercel vai te dar uma URL, algo como `https://email-sindicos-energia-a.vercel.app`.
Abra `email-para-disparo.html` e troque o placeholder pela URL real:

```bash
sed -i '' 's|https://SEU-PROJETO.vercel.app|https://SUA-URL-REAL.vercel.app|g' email-para-disparo.html
```

(no Windows/VS Code: Localizar e Substituir `https://SEU-PROJETO.vercel.app` pela sua URL)

Confirme abrindo `https://SUA-URL.vercel.app/logo-energia-a.png` no navegador —
se a logo aparecer, o e-mail vai renderizar certo no Gmail.

## Domínio próprio (opcional)

Em **Settings → Domains** você pode apontar algo como `campanha.energiaa.com.br`
(CNAME para `cname.vercel-dns.com`). Fica mais profissional no link "ver no navegador"
e evita que filtros antispam vejam um domínio genérico `.vercel.app`.
