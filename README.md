# Million IA — Página de Pós-Venda (Black Week 2026)

Página estática de confirmação pós-compra exibida depois do checkout (Cartroi → redirect).
Zero dependências de backend. Zero conexão com o sistema Million — a ativação real acontece
no sistema secundário de ativação (fora deste repo).

## O que a página comunica
1. Compra aprovada (reassuração imediata).
2. E-mail de confirmação em instantes.
3. **Link exclusivo de ativação em até 72h** após aprovação do pagamento (gerado pelo sistema secundário).
4. Acesso liberado pelo link — sem senha, sem cadastro adicional.

## Personalização por query params (passados no redirect do Cartroi)
- `?produto=combo` → "Combo Sistema Milionário + Pack Bônus"
- `?produto=dolar` → "Dólar de Midas"
- `?nome=Primeiro+Nome` → saudação personalizada (sanitizado, sem HTML)

Sem params, a página fica genérica (funciona igual).

## Deploy (Netlify, grátis)
- Conectar o repo em app.netlify.com → "Add new site → Import an existing project" → GitHub → `Brendoibv275/million-bf-postvenda`. Build command: nenhum. Publish directory: `.` (raiz).
- Ou arrastar a pasta em https://app.netlify.com/drop para um link imediato.

## Integração futura (não implementada — nada conectado ao Million)
- Configurar no Cartroi o redirect pós-compra para `https://<site>.netlify.app/?produto=combo&nome=...`
- O sistema secundário de ativação deve gerar o link exclusivo por comprador e disparar o e-mail de confirmação dentro das 72h prometidas nesta página. **A página promete 72h — o sistema secundário precisa honrar esse prazo** (reclamação de atraso = chargeback/consumer.gov).
