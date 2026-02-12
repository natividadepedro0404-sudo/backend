# 🚀 Guia de Hospedagem 24/7 (Cloud + Vercel)

Este guia ensina como deixar seu bot rodando 24 horas por dia, sem precisar do seu PC ligado.

## 📋 Arquitetura
1. **Frontend (Vercel)**: Interface visual pública.
2. **Backend (Railway/Render)**: O robô que escaneia o Discord.

---

## 🔧 Passo 1: Preparar o Backend (Cloud)

### 1. Subir para o GitHub
Para hospedar na nuvem, você deve primeiro colocar seu código em um repositório privado no GitHub.
- **DICA**: Não inclua o arquivo `.env` no GitHub!

### 2. Hospedar no Railway.app (Recomendado)
1. Crie uma conta no [Railway.app](https://railway.app).
2. Clique em **"New Project"** -> **"Deploy from GitHub repo"**.
3. Escolha este repositório.
4. Vá em **"Variables"** e adicione:
   - `DISCORD_TOKEN`: Seu token.
   - `WEBHOOK_URL`: Seu webhook.
   - `PORT`: `3000`
5. O Railway gerará um domínio (ex: `https://seu-bot.up.railway.app`). **Copie esta URL.**

---

## 🎨 Passo 2: Sincronizar o Frontend

### 1. Atualizar o `config.js`
No seu computador, abra o `config.js` e cole a URL que o Railway te deu:

```javascript
const CONFIG = {
    BACKEND_URL: 'https://seu-bot.up.railway.app', // URL DO RAILWAY
};
```

### 2. Redeploy no Vercel
No terminal do seu PC:
```bash
vercel --prod
```

---

## ⚡ Opção Alternativa: Rodar Local (ngrok)
Se você **não quiser** usar o Railway e preferir deixar seu PC ligado:

1. Inicie o bot: `node start.js`
2. Rode o ngrok: `ngrok http 3000`
3. Copie a URL `https://...ngrok-free.app`
4. Cole no `config.js`
5. Rode `vercel --prod`

---

## 📝 Notas Importantes
- ✅ **Cloud**: Funciona 24h, consome pouco recurso.
- ⚠️ **ngrok**: Só funciona enquanto seu PC estiver ligado e o terminal aberto.
- 🔄 **Mudou a URL?**: Sempre que mudar a URL no `config.js`, você precisa rodar `vercel --prod` novamente.

