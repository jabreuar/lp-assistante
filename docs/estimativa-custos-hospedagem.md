# Estimativa de custos de hospedagem: lp-assistante

> Estimativa feita em outubro de 2026 com os preços públicos de cada provedor.
> **Os valores são aproximados.** Confirme nas páginas de preço antes de contratar (links no fim). Os valores marcados com ⚠️ vêm de fontes secundárias ou de cálculos próprios.

## Premissas

**Arquitetura de referência:**
- app web (PWA) e/ou mobile;
- backend com API;
- banco relacional Postgres (para o CRM de clientes, as análises de necessidades e o histórico de cada cliente);
- autenticação;
- armazenamento de arquivos (PDFs dos planos);
- backups.

**Câmbio:** US$ 1 = **R$ 5,50**. Ajuste conforme a cotação do dia.

**LGPD:** o app guarda dados pessoais e financeiros e, às vezes, de saúde. A preferência é hospedar **no Brasil (São Paulo)**. Hospedar fora é permitido, mas exige mais cuidado com a transferência internacional de dados.

**Cenários de uso:**

| Cenário | Life Planners | Clientes cadastrados (≈500 por LP) | Banco de dados | Arquivos |
|---|---|---|---|---|
| **MVP / piloto** | até 50 | ~25 mil | < 1 GB | < 10 GB |
| **Regional** | ~300 | ~150 mil | ~2–5 GB | ~50 GB |
| **Rede nacional** | ~2.400 (toda a rede) | ~1,2 milhão | ~10–20 GB | ~200–400 GB |

## Comparativo de custo mensal

| Opção | Região Brasil? | MVP | Regional | Rede nacional |
|---|---|---|---|---|
| **A. Supabase + Vercel** | ✅ Supabase em São Paulo (sa-east-1); a Vercel serve pela CDN | **US$ 45** (~R$ 250) | **US$ 50–70** (~R$ 275–385) | **US$ 120–160** (~R$ 660–880) |
| **B. Firebase (Blaze)** | ✅ southamerica-east1 | **US$ 0–5** (~R$ 0–30) | **US$ 15–40** ⚠️ (~R$ 80–220) | **US$ 120–200** ⚠️ (~R$ 660–1.100) |
| **C. Render** | ❌ sem região no Brasil | **US$ 27** (~R$ 150) | **US$ 75** ⚠️ (~R$ 410) | **US$ 150** ⚠️ (~R$ 825) |
| **D. AWS Lightsail** | ✅ São Paulo | **US$ 27** ⚠️ (~R$ 150) | **US$ 55** ⚠️ (~R$ 300) | **US$ 130–180** ⚠️ (~R$ 715–990) |
| **E. Magalu Cloud** | ✅ nuvem brasileira, cobrança em reais | **~R$ 170** | **~R$ 250** ⚠️ | **~R$ 450–650** ⚠️ |
| **F. HostGator (VPS NVMe)** | ✅ Brasil ⚠️ confirmar onde fica o data center | **~R$ 40–60** | **~R$ 70–90** | **~R$ 200–250** ⚠️ |
| **G. Locaweb (VPS)** | ✅ São Paulo | **~R$ 45–60** | **~R$ 80–120** ⚠️ | **sob consulta** ⚠️ |
| **H. KingHost (VPS)** | ✅ Brasil | **~R$ 35–60** ⚠️ | **sob consulta** ⚠️ | **sob consulta** ⚠️ |
| **I. Hostinger (VPS KVM)** | ✅ São Paulo | **~R$ 45–80** | **~R$ 45–80** | **~R$ 150–300** ⚠️ |
| **J. Vultr** | ✅ São Paulo (preço 1,5× maior) | **US$ 38** (~R$ 210) | **US$ 70** ⚠️ (~R$ 385) | **US$ 150–200** ⚠️ (~R$ 825–1.100) |
| **K. Fly.io** | ✅ São Paulo, região `gru` (preço 1,615× maior) | **US$ 45–50** (~R$ 260) | **US$ 80–100** ⚠️ (~R$ 440–550) | **US$ 150–250** ⚠️ (~R$ 825–1.375) |

> **As VPS das opções F a I são as mais baratas, mas o custo esconde trabalho.** Nelas, você instala e administra o Postgres, aplica atualizações de segurança, configura firewall, faz backups fora do servidor e monitora tudo. Para dados financeiros e de saúde protegidos pela LGPD, essa responsabilidade é sua. Além disso, os preços anunciados costumam ser **promocionais**: valem para contratos de 12 a 36 meses e a renovação sai bem mais cara.

**Custo por Life Planner na rede nacional:** cerca de **R$ 0,20 a R$ 0,45 por mês**. A hospedagem pesa pouco no preço de uma assinatura.

## Detalhes de cada opção

### A. Supabase (Postgres, autenticação e arquivos) + Vercel (front-end web)

**Preços:**
- **Supabase Pro:** US$ 25/mês. Inclui US$ 10 de crédito de processamento, 8 GB de banco, 100 GB de arquivos, 250 GB de tráfego de saída e 100 mil usuários ativos por mês.
- **Upgrades de processamento:** Small por US$ 15/mês, Medium por US$ 60/mês. O crédito de US$ 10 é descontado.
- **Excedentes:** US$ 0,125/GB de banco, US$ 0,0213/GB de arquivos e US$ 0,09/GB de tráfego.
- **Vercel Pro:** US$ 20 por desenvolvedor por mês, com US$ 20 de crédito de uso. O plano Hobby é **só para uso não comercial**, então não serve aqui.

**Custo por cenário:**
- MVP: Supabase Pro (US$ 25) + Vercel Pro (US$ 20).
- Regional: processamento Small (+US$ 5 líquido) e algum consumo extra na Vercel.
- Nacional: processamento Medium (+US$ 50 líquido), excedente de arquivos (~US$ 5) e uso da Vercel (US$ 20–50).

**Não incluído:** backup com restauração para qualquer momento (PITR). É um opcional pago; verificar o preço.

**Prós:**
- Postgres de verdade.
- Row Level Security (RLS) isola os dados de cada corretora, o que ajuda muito na LGPD.
- Autenticação pronta.
- Dados em São Paulo.
- Desenvolvimento rápido.

**Contras:**
- O plano Free pausa por inatividade e não faz backup, então não serve para produção.

### B. Firebase (Firestore, Auth, Storage, Functions), plano Blaze

**Preços:**
- **Camada grátis:** 50 mil leituras e 20 mil gravações por dia no Firestore, 1 GiB de dados, 50 mil usuários ativos por mês na autenticação, 2 milhões de chamadas de Functions por mês.
- **Depois da camada grátis:** paga-se pelo uso. Os preços na região de São Paulo são um pouco maiores que nos EUA.

**Custo por cenário:**
- ⚠️ Regional e nacional: estimativa supondo ~2.000 leituras por LP por dia. Na rede nacional isso dá ~144 milhões de leituras por mês.

**Prós:**
- Muito barato no início.
- Sincronização offline nativa, útil para visitas a clientes.

**Contras:**
- O banco é NoSQL, menos adequado para um CRM relacional e para relatórios de metas e produção.
- O custo varia com o número de leituras, então é difícil de prever.
- Dependência da Google (lock-in).

### C. Render (servidor + Postgres gerenciado)

**Preços:**
- **Servidor web:** Starter a US$ 7/mês; Standard a US$ 25/mês.
- **Postgres:** a partir de ~US$ 7; o plano Basic-1GB custa ~US$ 20.
- ⚠️ O plano de workspace pode cobrar por membro da equipe.

**Contras:**
- **Não tem região no Brasil.** Isso aumenta a latência e exige cuidado com a transferência internacional de dados (LGPD).

**Prós:**
- Simples de operar.

### D. AWS Lightsail (São Paulo)

**Preços:**
- **Instância de 2 GB:** ~US$ 12/mês.
- **Banco gerenciado:** a partir de ~US$ 15/mês (Micro).
- **Balanceador de carga:** ~US$ 18/mês, necessário na rede nacional.
- ⚠️ Os preços da região de São Paulo podem ser maiores que os da tabela base, e a franquia de tráfego por lá é **metade** da de outras regiões.

**Prós:**
- Preço fixo e previsível.
- Dados no Brasil.
- Caminho natural para crescer dentro da AWS.

**Contras:**
- Você mesmo administra o servidor: atualizações, segurança e deploy.

### E. Magalu Cloud (nuvem brasileira)

**Preços:**
- **Máquina virtual BV2-2-10** (2 vCPU, 2 GB): R$ 59,99/mês.
- **Banco gerenciado (Postgres):**

| Plano | Configuração | Preço mensal |
|---|---|---|
| BV1-4-10 | 1 vCPU, 4 GB | R$ 94,22 |
| BV2-4-10 | 2 vCPU, 4 GB | R$ 100,00 |
| BV4-8-10 | 4 vCPU, 8 GB | R$ 188,00 |

**Custo por cenário:**
- MVP: 1 máquina virtual + banco BV1-4-10 + armazenamento de arquivos.
- Nacional: 2 ou 3 máquinas virtuais + banco BV4-8-10, possivelmente com uma réplica.

**Prós:**
- Cobrança em reais, sem risco de câmbio.
- Dados e empresa no Brasil, um bom argumento de LGPD para vender aos Life Planners.

**Contras:**
- Ecossistema e serviços gerenciados menos maduros.
- Você também administra o servidor.

### F. HostGator Brasil (VPS NVMe, você administra)

A HostGator trocou os planos antigos de VPS por uma linha NVMe. Todos incluem IP dedicado, transferência ilimitada e SSL. Segundo reviews, a infraestrutura roda sobre a Oracle Cloud. ⚠️ Confirmar se o data center fica no Brasil.

**Preços (todos "a partir de", ou seja, promocionais):**

| Plano | Configuração | Preço mensal |
|---|---|---|
| NVMe 2 | 1 vCPU, 2 GB, 50 GB | R$ 21,69 |
| NVMe 4 | 2 vCPU, 4 GB, 100 GB | R$ 30,39 |
| NVMe 8 | 4 vCPU, 8 GB, 200 GB | R$ 55,99 |
| NVMe 12 | 4 vCPU, 12 GB, 300 GB | R$ 77,49 |
| NVMe 16 | 6 vCPU, 16 GB, 400 GB | R$ 104,99 |
| NVMe 32 | 8 vCPU, 32 GB, 500 GB | R$ 130,49 |

**Custo por cenário:**
- MVP: NVMe 4, com app e banco na mesma máquina, mais um backup externo (~R$ 10–20).
- Regional: NVMe 8.
- Nacional: NVMe 12 para o app e NVMe 16 para o banco, mais backup.

### G. Locaweb (VPS)

**Preços:**
- VPS 1 GB: R$ 15,90 (renova por R$ 23,92).
- VPS 2 GB: R$ 21,90.
- VPS 4 GB: R$ 32,90.
- Todos os planos com 2 vCPU, SSD e transferência ilimitada.

**Prós:** empresa brasileira tradicional, com suporte em português e data center em São Paulo.

**Custo por cenário:**
- MVP: VPS 4 GB, considerando o preço de renovação.
- ⚠️ Rede nacional: os planos maiores não foram encontrados nas fontes. Consultar a Locaweb.

### H. KingHost (VPS)

**Preços:**
- VPS 1 GB, 50 GB SSD: a partir de R$ 22,90 (renova por R$ 33,90).

**Custo por cenário:**
- 1 GB é pouco para rodar o app e o Postgres juntos. ⚠️ Os preços dos planos de 2 a 4 GB não foram encontrados; o MVP foi estimado com base nas outras opções.

**Prós:** empresa brasileira (Porto Alegre), suporte em português.

### I. Hostinger (VPS KVM)

**Preços:**
- KVM 2 (2 vCPU, **8 GB**, 100 GB NVMe, backups semanais): de R$ 38,99 a R$ 43,99 na promoção; **R$ 77,99 no preço normal**.
- Tem data center em São Paulo.

**Custo por cenário:**
- MVP e regional: uma única KVM 2 aguenta os dois cenários, já que tem muita memória para o preço.
- ⚠️ Nacional: estimativa com KVM 4 ou KVM 8, ou duas KVM 2 (uma para o app e outra para o banco).

### J. Vultr (nuvem, região de São Paulo)

**Preços:**
- Em São Paulo, todos os planos custam **1,5×** o preço base. Exemplo: o servidor de 1 GB sai por US$ 7,50 em vez de US$ 5.
- Postgres gerenciado: a partir de ~US$ 15 no preço base, ou seja, ~US$ 22,50 em São Paulo.

**Custo por cenário:**
- MVP: servidor de 2 GB (~US$ 15) + Postgres gerenciado (~US$ 22,50).
- ⚠️ Nacional: dois servidores de 4 GB + Postgres com alta disponibilidade (HA).

**Prós:** banco gerenciado e dados no Brasil por um preço intermediário.

### K. Fly.io (região `gru`, São Paulo)

**Preços:**
- São Paulo tem o **maior multiplicador** de preço da Fly.io: **1,615×** o preço base.
- Managed Postgres: a partir de **US$ 38/mês** no plano Basic (1 GB de RAM), mais US$ 0,28/GB de armazenamento. O Managed Postgres está disponível em `gru`.
- Servidores (machines): cobrados por segundo.

**Custo por cenário:**
- MVP: Postgres Basic + uma ou duas machines pequenas.
- ⚠️ Nacional: Postgres de nível maior e várias machines.

**Prós:** deploy simples com containers e banco gerenciado no Brasil.

**Contras:** em São Paulo, fica mais caro que Supabase e Vultr.

## Custos fixos, que se aplicam a qualquer opção

| Item | Custo |
|---|---|
| Apple Developer Program (se houver app iOS) | US$ 99/ano (~R$ 545) |
| Google Play Console (se houver app Android) | US$ 25, taxa única (~R$ 140) |
| Domínio .com.br | ~R$ 40/ano |
| E-mail transacional (Resend, Postmark etc.) | grátis até alguns milhares de e-mails por mês |
| Monitoramento de erros (Sentry) | grátis no início |
| Build mobile (Expo EAS, se usar React Native) | grátis no início; planos pagos se precisar de mais builds |

## Recomendação

1. **MVP: opção A (Supabase em São Paulo + Vercel).** Custa cerca de **R$ 250/mês**.
   - Tem Postgres para o CRM e as análises de necessidades.
   - O RLS isola os dados de cada corretora.
   - A autenticação já vem pronta e os dados ficam no Brasil.
   - Tem o menor tempo até a primeira entrega.
2. **Se "dados 100% no Brasil, em empresa brasileira" for argumento de venda:** avaliar a **opção E (Magalu)**, que custa cerca de **R$ 170/mês**, mas exige mais trabalho de operação.
3. **Orçamento mínimo e alguém com experiência em Linux e DevOps no time:** uma **VPS Hostinger KVM 2** (~R$ 45–80/mês, 8 GB) ou **HostGator NVMe 4/8** (~R$ 30–60/mês) roda o MVP com folga. Antes, verifique três coisas:
   - backups automáticos guardados fora do servidor;
   - o preço de renovação, e não o promocional;
   - o local exato do data center.
4. **Evitar a opção C (Render)** enquanto não houver região no Brasil. A Fly.io funciona, mas sai cara em São Paulo.
5. **Revisar a escolha ao passar de ~300 Life Planners.** Nessa escala, o custo ainda é baixo (menos de R$ 1 por LP por mês). O que pesa mais é o custo do time de operação.

## Fontes de preço

- [Supabase: preços](https://supabase.com/pricing) e [regiões](https://supabase.com/docs/guides/platform/regions)
- [Vercel: preços](https://vercel.com/pricing)
- [Firebase: preços](https://firebase.google.com/pricing)
- [Render: preços](https://render.com/pricing). Valores conferidos em [frontdeskreview.com (set/2026)](https://frontdeskreview.com/software/managed-postgres/render/) e [kuberns.com](https://kuberns.com/blogs/render-postgres-pricing-setup-limits/)
- [AWS Lightsail: preços](https://aws.amazon.com/lightsail/pricing/) e [franquia de tráfego por região](https://docs.aws.amazon.com/lightsail/latest/userguide/amazon-lightsail-faq-data-transfer-allowance.html)
- [Magalu Cloud: preços de máquinas virtuais](https://magalu.cloud/precos/virtual-machines/) e [de banco gerenciado (DBaaS)](https://magalu.cloud/precos/dbaas/)
- HostGator VPS: [tudosobrehospedagemdesites.com.br](https://tudosobrehospedagemdesites.com.br/hostgator/servidor-vps/) e [kompare.com.br](https://www.kompare.com.br/hostgator/servidor-vps)
- [Locaweb: servidor VPS](https://www.locaweb.com.br/servidor-vps/) e [comparativo da serverspace.com.br (2026)](https://serverspace.com.br/about/blog/melhores-vps-brasil-2026/)
- KingHost VPS: [whtop.com](https://www.whtop.com/pt/plans/king.host/145164)
- Hostinger VPS: [leiturasingular.com.br](https://leiturasingular.com.br/hostinger-vps-vale-a-pena/) e [kildaryoliver.com.br](https://kildaryoliver.com.br/quanto-custa-vps-hostinger-brasil/)
- Vultr: [ployz.dev](https://ployz.dev/blog/vultr-pricing) e [getdeploying.com](https://getdeploying.com/vultr)
- [Fly.io: preços](https://fly.io/pricing/) e [Managed Postgres](https://fly.io/docs/mpg/). Multiplicador de região conferido em [srvrlss.io](https://www.srvrlss.io/provider/fly/)
