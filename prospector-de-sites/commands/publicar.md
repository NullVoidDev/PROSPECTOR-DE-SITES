---
description: Publica as páginas redesenhadas na Vercel e retorna as URLs públicas
argument-hint: "[nome do cliente ou todos]"
---
 
Publique páginas na Vercel seguindo a skill `deploy-vercel`.
 
## Passos
 
1. Leia `prospector-config.json`. Se o bloco da Vercel não estiver configurado, oriente o usuário a rodar o `/setup` primeiro — não prossiga sem ele.
2. Determine o que publicar: `$ARGUMENTS` (um cliente ou "todos"), ou liste as páginas com status `redesenhado` em `leads.md`/banco de dados e pergunte.
3. **Gere a página-capa de cada cliente**: preencha `references/capa-proposta-template.html` (skill `proposta-email`) com os dados do lead + assinatura do config e salve como `sites/[slug]/proposta.html`. Ela é necessária para exibir a proposta de antes/depois.
4. **Publique usando a Vercel CLI**:
   - Execute o deploy a partir do sandbox usando terminal local (`run_command`) diretamente na pasta do cliente:
     ```bash
     vercel deploy --name "demo-[slug]" --yes --cwd "sites/[slug]"
     ```
   - Capture a URL pública gerada no output do comando (ex: `https://demo-[slug].vercel.app`).
5. **Verificação HTTPS (bloqueante)**: Abra a URL gerada com `https://` e confirme que carrega com cadeado válido. Como a Vercel gera SSL automaticamente, a validação é imediata.
6. Atualize `leads.md` e o banco do dashboard: status `publicado` + `urlNova` (definida como a URL gerada pela Vercel) e o link da capa (`[URL]/proposta.html`).
 
## Saída
 
Liste, por cliente: URL da página nova e URL da capa (`[URL]/proposta.html`), ambas testadas em https. Sugira o próximo passo: `/proposta` para enviar os e-mails.
