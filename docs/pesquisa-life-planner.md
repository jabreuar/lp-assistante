# Pesquisa: o Life Planner da Prudential do Brasil

> Pesquisa feita em outubro de 2026 para orientar o desenvolvimento do **lp-assistante**, um aplicativo de apoio ao Life Planner.
> Escopo: **somente Brasil**. A seção "Validação das fontes" mostra o quanto cada informação foi checada.

## Resumo

No Brasil, o Life Planner **não é empregado da Prudential**. Ele é um **corretor de seguros habilitado** e dono de uma **corretora franqueada** (*Corretora Franqueada Life Planner*). Ganha por comissão e segue um método consultivo: entender as necessidades do cliente antes de falar de produto e acompanhá-lo pela vida toda. A SUSEP aprovou o modelo de franquia da Prudential do Brasil em janeiro de 2003.

## 1. Atribuições principais

Nas palavras da própria Prudential: *"Ele não só vende: ele desperta a necessidade, personaliza o planejamento e acompanha o cliente ao longo da vida inteira."*

| Atribuição | O que significa na prática |
|---|---|
| **Prospecção** | Encontrar clientes (muitas vezes por indicação) e despertar a necessidade de proteção financeira |
| **Análise de necessidades** | Montar a apólice a partir de uma análise detalhada do perfil do cliente, com foco no planejamento familiar |
| **Recomendação e contratação** | Intermediar a contratação e orientar sobre os produtos e coberturas adequados |
| **Acompanhamento vitalício** | Atender o cliente "desde o primeiro contato até o acompanhamento em casos de sinistros" |
| **Gestão do negócio** | Administrar a própria corretora dentro do padrão da franquia (pilares: velocidade, qualidade e padrão) |

## 2. Habilitação e status legal

- **Requisitos para ser corretor:** ter 18 anos ou mais e ensino médio completo, passar no **Exame de Habilitação de Corretores** aplicado pela **ENS** (Escola de Negócios e Seguros) e se registrar no **IBRACOR**. Desde 21/11/2019 a SUSEP reconhece o IBRACOR como entidade autorreguladora dos corretores. O registro também pode ser feito pelo sistema da SUSEP, com conta gov.br nível ouro.
- **Curso obrigatório?** O blog da Prudential diz que o curso da ENS é obrigatório, mas a ENS apresenta o curso como *preparatório*. **Confirmar as regras atuais na ENS.**
- **Sem vínculo de emprego:** o corretor *"não pode ter vínculo empregatício com seguradoras"*. Por isso o modelo é uma franquia, com atuação como pessoa física ou por meio de uma corretora (pessoa jurídica).

## 3. Franquia: investimento, rede e perfil

| Item | Dado | Fonte / data |
|---|---|---|
| Investimento inicial | a partir de R$ 33 mil; retorno estimado em 5 a 12 meses | Prudential, jan/2026 |
| Investimento inicial | cerca de R$ 40 mil | Revista Apólice, jun/2026 |
| Tamanho da rede | 2.238 unidades | Prudential, jan/2026 |
| Tamanho da rede | mais de 2.400 corretoras em 48 pontos de apoio | Revista Apólice, jun/2026 |
| Perfil exigido | sem formação ou experiência obrigatória; buscam energia, disciplina, automotivação e trajetória | Prudential, jan/2026 |
| Suporte | treinamento e acompanhamento contínuos pelas Master Franquias | Prudential |

## 4. Treinamento e carreira

- **PruEAD+:** plataforma digital de treinamento (release de mar/2023) com mais de 1.600 conteúdos em quatro academias:
  - **Negócios:** modelo de negócio, processo de vendas e recrutamento.
  - **Gestão da Franquia:** finanças, contratos e manuais.
  - **Comportamento:** soft skills e liderança.
  - **Vida:** propósito e história do seguro de vida.
- **Carreira:** depois de um período como Life Planner, o franqueado pode virar **Master Franqueado B (MFB)**, cuja principal atribuição é *"recrutar e treinar novos corretores Franqueados Life Planner"*. A fonte é de 2011; os níveis atuais podem ser diferentes.
- **Rotina descrita em processos judiciais:** reuniões semanais com gestores, apresentação do relatório da semana anterior, treinamentos, conteúdo motivacional e apresentação de metas. O TRT-1 registrou atividades *"minuciosamente especificadas em normas"*, com metas e fiscalização.

## 5. Remuneração

- **Por comissão, sem salário fixo:** a Prudential resume o princípio como *"Contribuição = Compensação"* e diz que, "com dedicação, os ganhos são ilimitados".
- **Salários informados por sites** (Glassdoor, indicedeseguros), como "salário-base de R$ 15 mil + variável", **não combinam com o modelo de franquia** e não são confiáveis.
- **Lacuna:** não foram encontrados percentuais de comissão, regras de persistência (bônus por apólices que continuam ativas) nem metas oficiais de produção. A COF (Circular de Oferta de Franquia) deve ter esses dados, mas costuma ser entregue só aos candidatos.

## 6. Risco jurídico: vínculo empregatício

A Justiça do Trabalho já discutiu várias vezes se o Life Planner é, na verdade, empregado da Prudential:

- **Decisões que reconheceram vínculo:**
  - 4ª Vara do Trabalho de Curitiba, mantida pelo TRT-9 (jul/2024): não havia taxas de franquia, o franqueado usava a sede da empresa e não tinha autonomia real.
  - 8ª Turma do TST: manteve o reconhecimento de vínculo de uma corretora de Brasília.
- **Decisões que negaram vínculo:**
  - 4ª Turma do TST (a partir de out/2023).
  - STF: Min. Cármen Lúcia (dez/2024) e Min. Dias Toffoli (13/12/2024), que anulou a decisão do TRT-1.
  - Fundamentos: ADPF 324 e Tema 725 (RE 958.252), que validam contratos entre pessoas jurídicas, a não ser que haja prova concreta de subordinação direta.

## 7. O que isso significa para o lp-assistante

1. **O usuário é um empresário.** O app deve tratar o Life Planner como dono da própria corretora, com seus clientes, metas e finanças, e não como funcionário da Prudential.
2. **O centro do app:** análise de necessidades + CRM + acompanhamento vitalício, que são as três atribuições que mais aparecem nas fontes.
3. **LGPD:** o app vai guardar dados pessoais, financeiros e, às vezes, de saúde (dados sensíveis). Isso exige consentimento, criptografia, controle de acesso e prazo para apagar os dados. A corretora é a controladora dos dados; o app é o operador.
4. **Marca e sistemas da Prudential:** não usar o nome ou o logo sem autorização, nem integrar com sistemas internos (cotação, emissão de apólices) sem acordo. As simulações devem avisar que são estimativas.
5. **SUSEP:** o app é uma ferramenta do corretor e não vende seguro direto ao consumidor.
6. **Não substituir o PruEAD+:** a capacitação oficial fica com a Prudential. O app pode, no máximo, guardar anotações e roteiros pessoais.

## Validação das fontes

- **Brasil:** pesquisa feita por buscas na web e leitura das páginas, **sem** a etapa de verificação cruzada com três votos. As fontes mais fortes são as páginas da própria Prudential e as decisões judiciais.
- **Outros países:** a primeira rodada, que comparou vários mercados, usou verificação cruzada. Nela, a afirmação de que "o curso da ENS é obrigatório, seguido de exame e registro no IBRACOR" **foi refutada da forma como estava escrita**. Daí o ponto em aberto na seção 2.
- **Contexto histórico:** o modelo Life Planner nasceu na Prudential do Japão, com venda consultiva baseada em necessidades para clientes de renda mais alta. Ele vale só como contexto: o modelo brasileiro tem estrutura própria (franquia e corretor independente).

## Fontes

- [Prudential: Corretor de seguros, o que faz e como se tornar](https://www.prudential.com.br/blog/negocios/corretor-de-seguros-o-que-faz-e-como-se-tornar)
- [Prudential: Seguro de vida cria oportunidades para empreendedores (jan/2026)](https://www.prudential.com.br/imprensa/releases/seguro-de-vida-cria-oportunidades-para-empreendedores)
- [Prudential: plataforma de treinamento PruEAD+ (2023)](https://www.prudential.com.br/imprensa/releases/prudential-do-brasil-aprimora-plataforma-treinamento-para-franqueados)
- [Revista Apólice: Franquia Life Planner na ABF Expo (jun/2026)](https://revistaapolice.com.br/2026/06/prudential-apresenta-franquia-life-planner-na-abf-expo/)
- [Sonho Seguro: modelo de franquias da Prudential (2025)](https://www.sonhoseguro.com.br/2025/05/modelo-de-franquias-da-prudential-impulsiona-expansao-do-seguro-de-vida-no-brasil/)
- [CQCS: 20 novos Master Franqueados B (2011)](https://cqcs.com.br/noticia/prudential-do-brasil-tem-mais-20-novos-master-franqueados-b-mfbs/)
- [Portal do Franchising: Franquia Prudential](https://franquias.portaldofranchising.com.br/franquia-prudential/)
- [Sindicato das Seguradoras: como atuar como corretor (2025)](https://www.sindicatoseguradoras.com.br/2025/02/13/veja-o-que-fazer-para-atuar-como-corretor-de-seguros/)
- [ENS: Exame da SUSEP](https://enscursos.com.br/blog/exame-da-susep-seu-caminho-para-se-tornar-corretor-de-seguros/)
- [Migalhas: TST nega vínculo (out/2023)](https://www.migalhas.com.br/quentes/394493/tst-nega-vinculo-de-emprego-entre-franqueado-e-prudential)
- [Migalhas: STF anula decisão do TRT-1 (dez/2024)](https://www.migalhas.com.br/quentes/421606/stf-anula-decisao-e-manda-trt-1-revisar-caso-de-vinculo-na-prudential)
- [ConJur: Cármen Lúcia nega vínculo (dez/2024)](https://conjur.com.br/2024-dez-30/carmem-anula-decisoes-que-reconheciam-vinculo-de-emprego-entre-seguradora-e-corretores/)
- [Sedep: 8ª Turma do TST reconhece vínculo](https://www.sedep.com.br/noticias/tst-seguradora-prudential-do-brasil-seguros-tera-de-reconhecer-vinculo-de-emprego-com-corretora/)
- [Nuredin Advogados: TRT-9 reconhece vínculo (jul/2024)](https://nuredin.adv.br/relacao-entre-life-planner-e-a-empresa-de-seguros-prudential-caracteriza-vinculo-de-emprego-afirma-a-justica-do-trabalho/)
