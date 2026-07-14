# Pré-inscrição · Influência 2.0

Formulário de pré-inscrição do evento **Influência 2.0** (Spark Maxx), feito para ser
**embedado via iframe no Beehiiv**. Coleta **Nome, E-mail, Telefone e Empresa**, dispara
um webhook para o n8n e o n8n registra a conversão no RD Station.

## Fluxo

```
Form (index.html)  →  POST  →  Webhook n8n  →  Conversão RD Station
```

- **Webhook (produção):** `https://growthsparkmaxx.app.n8n.cloud/webhook/pre-inscricao-influencia`
- **Workflow n8n:** `Pré-inscrição Influência 2.0 (Beehiiv) → RD` (`kHC3wJoH2NC3knCt`)
- **RD:** `POST /platform/events` · `conversion_identifier: pre-inscricao-influencia-2.0`

O endpoint do webhook está configurado em `index.html` na constante `WEBHOOK_URL`.

## Hospedagem

O projeto é um único arquivo estático (`index.html`). Qualquer host estático serve:

- **Vercel:** importe este repositório → deploy automático. A URL raiz já serve o form.
- **GitHub Pages:** Settings → Pages → branch `main` → `/root`.

## Embed no Beehiiv

Use um bloco **Embed** (não "Custom HTML" — o Beehiiv sandboxa `<script>`) e cole:

```html
<iframe src="https://SUA-URL-HOSPEDADA/"
        style="width:100%;max-width:520px;border:0;height:640px;"
        loading="lazy"></iframe>
```

## Recursos do form

- Validação de campos obrigatórios (HTML5)
- Máscara de telefone BR `(11) 99999-9999`
- Honeypot anti-spam
- Estado de sucesso após envio
- Visual alinhado ao e-mail da campanha (cinza-azulado + CTA laranja)
