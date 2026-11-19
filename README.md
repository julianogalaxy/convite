# Convite digital Botox Day

Convite digital da **Odontologia Reabilitação Oral e Estética** (Hortolândia/SP). A paciente toca, assiste ao envelope abrindo em vídeo e a carta vira a página do convite, já com o nome dela, a data, o horário e, se houver, o valor individual.

Responsável técnica: Dra. Elisângela Rodrigues Mota Magalhães, CRO-SP 98531.

---

## Endereços

| Uso | Endereço |
|---|---|
| Convite (o que a paciente recebe) | https://julianogalaxy.github.io/convite/ |
| **Gerador (uso interno da recepção)** | https://julianogalaxy.github.io/convite/#gerador |
| Versão 2: envelope 3D | https://julianogalaxy.github.io/convite/v2-envelope-3d.html |
| Versão 3: primeiro filme | https://julianogalaxy.github.io/convite/v3-filme-1.html |

---

## Como enviar um convite (passo a passo da recepção)

1. No celular da recepção, abra o **Gerador**: `https://julianogalaxy.github.io/convite/#gerador`.
   Na primeira vez, use "Adicionar à tela inicial" para virar um atalho.
2. Preencha:
   - **Nome** da paciente (primeiro nome ou nome e sobrenome).
   - **Data** e **horário** reservados. Sem horário, o convite mostra o período do evento e convida a reservar.
   - **Valor** (opcional) e a **descrição do valor**, que vem como "Condição exclusiva para você".
   - **WhatsApp** da paciente (opcional). Com o número, a conversa dela já abre.
3. Toque em **Ver prévia** para conferir a experiência completa. Depois, **Voltar ao gerador**.
4. Toque em **Enviar pelo WhatsApp**. A mensagem e o link personalizado já vão preenchidos; é só enviar.
5. Toque em **Limpar para a próxima paciente** e repita.

O campo "Endereço do convite" já vem preenchido com o endereço acima. Se aparecer vazio, cole `https://julianogalaxy.github.io/convite/`.

### Regras importantes

- **Envie sempre o link, nunca o arquivo `.html`.** Aberto como arquivo no celular, o vídeo e as animações não funcionam.
- **Valor só em mensagem individual** para a paciente. Nunca em post, story, anúncio ou grupo (normas de publicidade do CFO).
- **Privacidade (LGPD):** nome, data, horário e valor ficam depois do `#` no link. Essa parte não sai do celular da paciente: não é enviada ao GitHub nem fica registrada em servidor. O histórico de envios do gerador fica só no aparelho da recepção.
- Se a paciente não tiver o número da clínica salvo, o WhatsApp pode pedir um toque a mais para abrir o link.

### Formato do link

O gerador cria um link curto e legível, por exemplo:

```
https://julianogalaxy.github.io/convite/#Juliano-Motta.0512.1030.x2klc
```

| Parte | Significado |
|---|---|
| `Juliano-Motta` | nome (hífen no lugar do espaço) |
| `0512` | dia e mês (5 de dezembro) |
| `1030` | horário (10h30), opcional |
| `x2klc` | valor codificado (não aparece como preço no link), opcional |

O valor nunca vai no texto da mensagem: a paciente vê a condição só dentro do convite. Se a descrição do valor for diferente do padrão, o gerador usa o formato completo (`#n=...&d=...&h=...&v=...&c=...`), que continua funcionando, assim como links antigos.

### Mensagem enviada (modelo padrão, editável no gerador)

```
Olá, Juliano! ✨

Nós, do consultório Odontologia Reabilitação Oral e Estética, junto com a Dra. Elisângela Mota Magalhães, preparamos um convite especial para você: *Botox Day* 💛

📅 Sábado, 5 de dezembro
⏰ Às 10h30
📍 R. Eliza Laurinda da Silva, 284 · Jardim Santana, Hortolândia

🎁 Reservamos uma condição exclusiva para você.

Para ver todos os detalhes, é só abrir o seu convite 💌
https://julianogalaxy.github.io/convite/#Juliano-Motta.0512.1030.x2klc

Qualquer dúvida, responda esta mensagem. Será um prazer receber você! 😊
```

---|---|
| `n` | nome |
| `d` | data (AAAA-MM-DD) |
| `h` | horário (HH:MM) |
| `v` | valor em centavos (`89000` = R$ 890,00) |
| `c` | descrição do valor |

---

## Como atualizar o convite

Os arquivos publicados ficam na raiz do repositório (`index.html`, `capa.jpg`). Qualquer alteração enviada para a branch `main` vai para o ar em cerca de 1 minuto, no mesmo endereço. Links já enviados passam a abrir a versão nova.

Para mudar textos, data do evento, procedimentos ou endereço, baixe e descompacte `fonte.zip`, edite `fonte/src/config/invitation.ts` e gere de novo:

```bash
cd fonte
npm install
npm run build:single          # gera dist/convite-v4-video-standalone.html
```

Copie o arquivo gerado para a raiz como `index.html` e mantenha as tags `og:` do `<head>` (são elas que mostram a capa na prévia do WhatsApp).

Mais detalhes técnicos no `README.md` dentro de `fonte.zip`.

Para publicar a alteração: no GitHub, **Add file > Upload files**, envie o novo `index.html` e confirme em **Commit changes**.

---

## Estrutura

```
index.html          convite v4 (filme) + gerador (#gerador)
capa.jpg            imagem da prévia do link no WhatsApp
v2-envelope-3d.html versão 2 (envelope 3D)
v3-filme-1.html     versão 3 (primeiro filme)
robots.txt          evita que o convite apareça no Google
fonte.zip           projeto-fonte: React + TypeScript + Vite + GSAP
                    (src/config: textos e personalização; src/components: envelope,
                     vídeo, carta, conteúdo e gerador; qa: testes Playwright)
```

## Pendências

- [ ] Confirmar data e horário oficiais do evento (hoje: 12/12/2026, das 9h às 18h) em `fonte/src/config/invitation.ts`.
- [ ] Informar o número de inscrição da clínica no CRO-SP (campo `croRegistration`), se houver.
- [ ] Testar no iPhone (Safari) e no Android (Chrome) antes dos envios em massa.
