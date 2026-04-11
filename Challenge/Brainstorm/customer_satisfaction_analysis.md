# Definição da Target: Análise da Variável de Satisfação do Cliente

## 📊 Qual Variável Representa a Satisfação do Cliente?

### Variável Principal: `nps_score`
- **Tipo**: Numérica contínua (0-10)
- **Descrição**: Score direto do Net Promoter Score coletado do cliente
- **Distribuição observada**: Variação de 0.0 a 10.0 nos dados disponíveis
- **Interpretação tradicional**:
  - **Promotores**: 9-10 (clientes entusiastas que recomendam)
  - **Neutros**: 7-8 (clientes satisfeitos mas não entusiastas)
  - **Detratores**: 0-6 (clientes insatisfeitos que podem prejudicar a marca)

### Variável Complementar: `repeat_purchase_30d`
- **Tipo**: Binária (0/1)
- **Significado**: Indica se o cliente fez nova compra em 30 dias
- **Relevância**: Proxy comportamental da satisfação real
- **Correlação esperada**: Clientes com maior NPS tendem a recomprar mais

## 🎯 Por que o NPS Score foi Escolhido como Target?

### 1. **Alinhamento Estratégico**
- **Padrão de mercado**: NPS é métrica universalmente aceita para medir lealdade
- **Benchmark externo**: Permite comparação com concorrentes e setor
- **Simplicidade conceitual**: Fácil entendimento por stakeholders não-técnicos
- **Acionabilidade**: Diretamente conectado a ações de melhoria de CX

### 2. **Valor Preditivo**
- **Leading indicator**: Prediz comportamentos futuros (recompra, churn, advocacy)
- **Correlação com receita**: Estudos mostram correlação entre NPS e crescimento financeiro
- **Detecção precoce**: Identifica problemas antes que se tornem críticos
- **Segmentação natural**: Permite classificação clara em promotores/neutros/detratores

### 3. **Fundamentação Científica**
- **Metodologia validada**: Desenvolvida por Fred Reichheld (Bain & Company)
- **Robustez estatística**: Decades de validação em diferentes setores
- **Pesquisas acadêmicas**: Extensa literatura comprovando eficácia
- **Casos de sucesso**: Empresas como Amazon, Apple usam NPS como métrica core

## ⏰ Momento de Coleta na Jornada do Cliente

### Situação Atual (Problema Identificado)
- **Timing**: Após encerramento completo da jornada de compra
- **Metodologia**: Pesquisa pós-transação (provavelmente por email/SMS)
- **Delay típico**: 3-7 dias após entrega do produto
- **Taxa de resposta esperada**: 5-15% (padrão do mercado)

### Pontos Críticos do Timing Atual
1. **Muito tardio**: Problemas já ocorreram e impactaram a experiência
2. **Memória decay**: Cliente pode não lembrar detalhes específicos
3. **Oportunidade perdida**: Impossibilidade de intervenção preventiva
4. **Viés de seleção**: Apenas clientes muito satisfeitos ou insatisfeitos respondem

### Proposta de Melhoria
- **Múltiplos pontos de coleta**: Durante a jornada (pós-compra, pós-entrega, pós-suporte)
- **Micro-surveys**: Pesquisas rápidas em momentos-chave
- **Indicadores proxy**: Uso de dados comportamentais como early warning
- **Real-time feedback**: Coleta de feedback durante interações de suporte

## ⚠️ Riscos de Uso Inadequado da Variável

### 1. **Riscos Metodológicos**

#### **A. Viés de Resposta**
- **Problema**: Clientes extremamente satisfeitos ou insatisfeitos são mais propensos a responder
- **Impacto**: Distribuição bimodal artificial, sub-representação de neutros
- **Mitigação**: Ponderação por propensão de resposta, incentivos balanceados

#### **B. Gaming e Manipulação**
- **Problema**: Equipes podem "forçar" scores altos através de táticas inadequadas
- **Exemplos**: Solicitar apenas de clientes satisfeitos, timing manipulado
- **Mitigação**: Auditoria de processo, amostragem aleatória obrigatória

#### **C. Oversimplification**
- **Problema**: Reduzir experiência complexa a um único número
- **Risco**: Perder nuances importantes da jornada do cliente
- **Mitigação**: Complementar com CSAT detalhado, feedback qualitativo

### 2. **Riscos de Modelagem**

#### **A. Data Leakage**
- **Risco**: Usar variáveis que só existem após o NPS ser conhecido
- **Exemplo**: `repeat_purchase_30d` pode ser consequência, não causa do NPS
- **Prevenção**: Timeline rigorosa, features baseadas apenas em dados anteriores

#### **B. Overfitting em Outliers**
- **Problema**: Modelo pode aprender padrões de casos extremos não representativos
- **Impacto**: Performance ruim em novos dados
- **Solução**: Validação cruzada robusta, técnicas de regularização

#### **C. Concept Drift**
- **Risco**: Padrões de satisfação mudam com tempo (sazonalidade, concorrência)
- **Exemplo**: Expectativas de entrega mudaram com COVID-19
- **Mitigação**: Retreino periódico, monitoramento de performance

### 3. **Riscos de Negócio**

#### **A. Foco Excessivo em Score**
- **Problema**: Otimizar apenas para NPS pode prejudicar outras métricas
- **Exemplo**: Melhorar NPS mas aumentar custos operacionais insustentavelmente
- **Balanceamento**: Considerar ROI, margem, eficiência operacional

#### **B. Interpretação Cultural**
- **Risco**: Diferentes regiões/culturas podem ter padrões distintos de resposta
- **Evidência**: Norte vs Nordeste podem ter escalas de avaliação diferentes
- **Abordagem**: Normalização regional, modelos segmentados

#### **C. Causalidade vs Correlação**
- **Problema**: Confundir fatores correlacionados com drivers causais
- **Exemplo**: Clientes premium podem dar NPS alto por viés de confirmação
- **Solução**: Testes A/B, análise de causalidade, experimentos controlados

## 🔍 Recomendações para Uso Adequado

### 1. **Segmentação da Target**
```markdown
Promotores (9-10):     Foco em advocacy e upselling
Neutros (7-8):         Oportunidade de conversão
Detratores (0-6):      Prioridade em retenção/recuperação
```
