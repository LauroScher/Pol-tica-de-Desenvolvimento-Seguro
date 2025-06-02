# Política-de-Desenvolvimento-Seguro
Documento que estabelece diretrizes para integrar segurança no ciclo de vida de desenvolvimento (Secure SDLC), alinhado a PCI DSS, LGPD e OWASP.
---
 
 # 📜 Cenário Hipotético 
 *A FINPAY (empresa fictícia), uma fintech de médio porte que atua no setor de pagamentos digitais
(semelhante à Elo, Cielo e BB), está em fase de expansão nacional e deseja fechar
contratos estratégicos com grandes bancos e operadoras de cartões. No entanto,
durante as fases iniciais de auditoria de segurança e compliance, foram identificadas
fragilidades graves no processo de desenvolvimento seguro da empresa.
A área de engenharia de software já possui um time de Tech Leads e um gerente de
desenvolvimento, mas não há políticas formais ou procedimentos padronizados para
segurança no ciclo de vida de software (Secure SDLC). A ausência de práticas como
análise estática de código, validação de bibliotecas de terceiros, controle de
vulnerabilidades e homologações seguras coloca a empresa em risco e compromete
o fechamento dos contratos.
Além disso, a empresa recebeu uma exigência formal dos parceiros comerciais e
reguladores: apresentar, no prazo de 30 dias úteis, um conjunto completo de
políticas e procedimentos documentados que tratem especificamente de
desenvolvimento seguro, com prazos estabelecidos para tratamento de
vulnerabilidades (30, 60, 90 dias) conforme criticidade, ciclo de homologação,
auditoria de código-fonte e padronização da análise de bibliotecas de terceiros*
---  
 

 ## 🎯 **Objetivo**  
 Este documento tem como objetivo estabelecer diretrizes para incorporar práticas de segurança no
ciclo de vida de desenvolvimento de software (Secure SDLC) da FINPAY, com o propósito de melhorar
a proteção de dados sensíveis, incluindo dados de cartões e dados pessoais, em conformidade com
PCI DSS (Payment Card Industry Data Security), LGPD (Lei Geral de Proteção de Dados Pessoais - Lei
nº 13.709/2018) e boas práticas da OWASP (Open Web Application Security Project), além de atender
às exigências contratuais e de segurança de parceiros comerciais 
  
 ##  📖 **Glossário**
 - Secure SDLC: Ciclo de vida de desenvolvimento de software com práticas de segurança
integradas em todas as fase.
 -   PCI DSS (Payment Card Industry Data Security Standard): Padrão global de segurança de dados
desenvolvido pelas principais bandeiras de cartão de crédito para proteger informações
sensíveis de cartões de pagamento.
 -   Pipeline CI/CD: Integração Contínua e Entrega Contínua; práticas para automação do
desenvolvimento e implantação.
 -   LGDP: Lei Geral de Proteção de Dados.
 -   OWASP Top 10: Lista das 10 vulnerabilidades web mais críticas, publicada pela OWASP.
 -   SAST (Static Application Security Testing): Análise estática do código-fonte sem execução,
detectando vulnerabilidades como injeção SQL e falhas de autenticação.
 -   DAST (Dynamic Application Security Testing): Análise dinâmica com aplicação em execução,
identificando vulnerabilidades em tempo real.
 -   Fuzzing: Técnica de teste que injeta dados inválidos para identificar falhas.
 -   Zero-day: Vulnerabilidade desconhecida explorada antes da correção
  
 ## 🔍 **Escopo**  
 Aplica-se a:  
 - APIs, gateways de pagamento, apps móveis e sistemas internos.  
 - Equipes de desenvolvimento, segurança, DevOps e terceiros envolvidos no SDLC.  
  
## 👥 **Púlbico-alvo**
Destina-se a todos os colaboradores, prestadores de serviço, consultores e quaisquer terceiros que
participem, direta ou indiretamente, do ciclo de vida de desenvolvimento de software da FINPAY.
Principalmente:
- Desenvolvedores
- Tech Leaders
- Analistas de Segurança
- Arquitetos de Software

 ## **Referências**  
 Os documentos a seguir são referências para este material e fornecem as orientações.
 
| **Ferramentas**       | **Contribuição**                                                                 |
|------------------|---------------------------------------------------------------------------------|
| **OWASP**        | Oferece diretrizes para identificação de vulnerabilidades e validação de entradas no Secure SDLC. Alinha-se a PCI DSS e LGPD, promovendo segurança desde a concepção. |
| **PCI DSS**      | Estabelece padrões para proteção de dados de cartões, incluindo requisitos como criptografia, monitoramento e testes de segurança regulares. Complementa a LGPD. |
| **LGPD** (Lei nº 13.709/2018) | Define regras para tratamento de dados pessoais, com sanções para não conformidade (multas de até R$50 milhões). Exige transparência e consentimento. |

 ## 📌 **Aderência e Compliance**  
 Recomenda-se:
 
 **PCI DSS**  
 - Construir e manter uma rede e sistema seguros
 - Proteger dados de cartões.  
 - Implementar controle de acesso rigoroso.  
 - Monitorar e testar redes regularmente.  
 - Manter uma política de segurança da informação
  
 **LGPD**  
- Mapeamento e Gestão de Dados Pessoais (Identificar, mapear fluxo e documentar finalidades).
- Nomeação de Encarregado de Dados (DPO).
- Consentimento e Transparência (Obter consentimento explícito, informar direitos dos titulares, garantir comunicação transparente)
- Segurança de Dados (Implementar criptografia, tokenização,  adotar autenticação multifator, realizar testes regulares)
- Gestão de Incidentes (Plano de Resposta a Incidentes de Segurança)
- Gestão de Terceiros e parceiros (Auditar fornecedores)
- Integração com outros padrões (LGPD com PCI DSS)

**Procedimento para análise estática e dinâmica do código (OWASP)**

***- Análise Estática (SAST)***
- Integrar ferramentas SAST no pipeline CI/CD para análise automatizada.
- Definir regras baseadas no OWASP Top 10, priorizando autenticação e proteção de dados
sensíveis.
- Priorização de vulnerabilidades por gravidade com prazos específicos para resolução.
- Mitigação de falsos positivos via configuração correta e revisão manual em áreas críticas.
- Validação de segurança para ferramentas terceirizadas.
- Documentação obrigatória de correções.

***- Análise Dinâmica (DAST)***
- Configurar ambientes similares à produção com isolamento seguro.
- Testes automatizados e manuais com simulações realistas, incluindo pentests.
- Correlação de resultados DAST com SAST para maior precisão.
- Priorizar vulnerabilidades baseado em modelos de ameaça.
- Monitoramento contínuo para prevenir ataques zero-day.
- Uso de técnicas avançadas como fuzzing e contratação eventual de serviços externos para
testes de penetração.

**Procedimento de homologação de código para produção (OWASP)**

***- Processo de build e deploy***
- Definição de um processo de build automatizado num pipeline CI/CD.
- Revisão de ferramentas de build e desenvolvimento para garantir que ainda estão sendo
mantidas pelos fornecedores, com patches de atualização e com a melhor configuração de
hardening possível.
- Guardar um hash ou outra forma de garantir a integridade do artefato produzido antes de
subir ao ambiente para comparação no pipeline.
- Implementação de ferramentas de SAST e DAST no pipeline CI/CD dos projetos.
- Manter um registro de onde todas as dependências são utilizadas em cada projeto.
- Construção de um repositório central com dependências e versões aprovadas para o uso de
todos os projetos.
- Automatização no pipeline em busca de dependências vulneráveis e não permitir a
homologação caso seja encontrada alguma.
- Atualização das dependências caso seja reportada alguma vulnerabilidade na versão usada.

***- Verificação de código***
- Conduzir testes de segurança para garantir o correto funcionamento, a confidencialidade,
integridade e disponibilidade.
- Conduzir testes de autenticação, controle de acesso, validação de campos de entrada,
codificação e criptografia.
- Conduzir testes de regressão para garantir que bugs consertados não voltem a ocorrer com
atualizações no código.
- Testes automatizados e manuais, além de testes de penetração regulares.
  
 ## **Papéis e Responsabilidades**  
A aplicação efetiva das recomendações feitas exige que cada indivíduo e equipe compreenda seu
papel e suas responsabilidades na integração da segurança em todo o ciclo de vida de
desenvolvimento de software:

**- Desenvolvedores:**
- Executar testes SAST.
- Corrigir vulnerabilidades identificadas.
- Integrar ferramentas ao pipeline CI/CD.

**- QA/Testes:**
- Executar testes DAST.
- Validar ambientes de testes e homologação.

**- Analista SOC:**
- Configurar e gerenciar ferramentas conduzidas para analisar possíveis vulnerabilidades.
- Revisar resultados e definir prioridades de correção.

**- DevOps:**
- Automatizar e garantir a execução contínua dos testes SAST e DAST nos pipelines CI/CD.

**- Tech Leaders:**
- Supervisão técnica da qualidade do código.
- Integração de práticas seguras no desenvolvimento.

**- Gerência de Tecnologia:**
- Aprovação de exceções.
- Análise de relatórios e conformidade com regulamentos.
- Revisão da política de desenvolvimento seguro.

**- Pentesters:**
- Realizar revisões técnicas especializadas.
- Conduzir pentests e análises avançadas de vulnerabilidades.

**- Arquitetos de Software:**
- Validar arquiteturas.
- Mitigar vulnerabilidades estruturais no design.

 ## ⚠️ **Sanções**  
 
### LGPD (Art. 52):
- Advertência, com indicação de prazo para adoção de medidas corretivas;
- Multa simples de até 2% (dois por cento) do faturamento da pessoa jurídica de direito privado,
grupo ou conglomerado no Brasil no seu último exercício, excluídos os tributos, limitada, no total,
a R$ 50.000.000,00 (cinquenta milhões de reais) por infração;
- Multa diária, observado o limite total;
- Publicização da infração após devidamente apurada e confirmada a sua ocorrência;
- Bloqueio dos dados pessoais a que se refere a infração até a sua regularização;
- Eliminação dos dados pessoais a que se refere a infração.

### PCI DSS:
- Multas e penalidades impostas pelas bandeiras de cartão e bancos adquirentes.
- Perda da capacidade de processar transações com cartões de pagamento.
- Custos associados a investigações forenses, notificações a clientes e reemissão de cartões.
- Danos à reputação da FINPAY.

### Adicionalmente, das diretrizes estabelecidas de acordo com o OWASP, pode resultar em:
- Bloqueio temporário de deploy para ambientes produtivos até resolução das vulnerabilidades
críticas.
- Registro formal de não conformidade e exigência de ações corretivas.
- Advertências formais e treinamento obrigatório em segurança para casos reincidentes ou
negligência.
- Investigação e possíveis sanções disciplinares no caso de incidentes graves, como vazamento de
dado
  
## Prazos de Correção

| Severidade | Prazo |
|------------|--------|
| Alta       | 0 a 7 dias |
| Média      | 7 a 30 dias |
| Baixa      | 30 a 90 dias |
  
## 🎓 Plano de Treinamento e Conscientização

### Formato
- Treinamentos presenciais/remotos
- Workshops práticos
- Campanhas de pílulas de conhecimento
- Avaliações de eficácia

### Estrutura
- **Duração por módulo**: 8h (4h teóricas + 4h práticas)
- **Avaliação mínima**: 80%
- **Ferramentas**: SAST, DAST, gestão de vulnerabilidades
- **Documentação**: Em repositório interno

### Temas por Trimestre

| Quarter | Tema | Objetivo |
|---------|------|----------|
| 1º | Fundamentos de Segurança e Conformidade | Introduzir PCI DSS, OWASP e LGPD |
| 2º | Análise de Código e Bibliotecas Terceiras | Utilizar SAST/DAST e validar bibliotecas |
| 3º | Homologação e Auditoria de Código | Padronizar processos de homologação |
| 4º | Cultura de Segurança e Maturidade | Revisar práticas e preparar auditorias externas |

---

## Resultados Esperados

- Detecção precoce de vulnerabilidades
- Redução no tempo de correção
- Conformidade com PCI DSS, LGPD e OWASP
- Cultura de segurança organizacional
- Atingir Níveis 1 e 2 da prática Security Testing do OWASP SAMM v2
- 100% dos desenvolvedores treinados com ≥ 80% nas avaliações
- Redução de 50% das vulnerabilidades críticas em 1 ano
- Mitigação conforme prazos
- Documentação completa em 30 dias úteis
- Aprovação em auditorias externas
 ## 📅 **Aprovação e Revisão**  
 | Versão | Data       | Responsável          |  
 |--------|------------|----------------------|  
 | 1.0    | 31/05/2025 | Lauro Scher |  

## **Referências usadas:** 
- Segurança no Ciclo de Vida de
Desenvolvimento de Software em uma
Fintech - CISSA. (Documentação disponibilizada pelo docente Milton Vinicius Morais de Lima)
- OWAPS SAMM-v2.pdf 
- OWASP Application Security Verification Standard 4.0.3.pdf

## Equipe responsável 
Tópicos  | Responsáveis pela elaboração |
 |--------|---------------------------|
| Documentação | Lauro Scher, Julia Ribeiro Tamborlin, Maria Fernanda Coelho de Luna
|Procedimento para análise estática e dinâmica do código| Lauro Scher, Thiago Henrique Marques | 
|Procedimento de homologação de código| Breno Pedro Pinto, Gustavo Costa|
| Plano de treinamento e conscientização | Leonam Bernardo de Lima |
