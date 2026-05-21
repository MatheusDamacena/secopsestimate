<div align="center">

<img src="https://img.shields.io/badge/SecOps-Sizing%20Tool-4285f4?style=for-the-badge&logoColor=white" alt="SecOps Sizing Tool"/>

# SecOps Ingestion Sizing Tool

**Ferramenta de pré-venda técnica para dimensionamento de volume de ingestão do Google Chronicle SecOps**

[![Version](https://img.shields.io/badge/versão-1.1.0-4285f4?style=flat-square)](https://github.com/)
[![Lang](https://img.shields.io/badge/idiomas-PT%20%7C%20EN%20%7C%20ES-34a853?style=flat-square)](https://github.com/)
[![License](https://img.shields.io/badge/licença-MIT-fbbc04?style=flat-square)](./LICENSE)
[![Standalone](https://img.shields.io/badge/standalone-HTML%20único-9c27b0?style=flat-square)](https://github.com/)

</div>

---

## 📌 Sobre

O **SecOps Ingestion Sizing Tool** resolve um problema crítico de pré-venda:

> *O Google SecOps é licenciado por **TB/ano** (volume de dados ingeridos). Não existe conversão direta cotar sem entender o ambiente gera estimativas incorretas e perda de negócio.*

Esta ferramenta permite calcular o volume estimado de ingestão a partir do inventário real do cliente, produzindo a métrica correta para cotação do Chronicle SecOps com relatório exportável em PDF e planilha XLSX.

Acesse na web: https://matheusdamacena.github.io/secopsestimate/

---

## ✨ Funcionalidades

### 🧮 Dimensionamento

| # | Funcionalidade | Descrição |
|---|---|---|
| 1 | **146 tipos de evento catalogados** | 10 categorias: Servidores, Rede, Endpoint, Identidade, Apps, Cloud, Segurança, OT/IoT, Dados/IA, Telecom |
| 2 | **Cálculo em tempo real** | EPS × bytes/evt × 86.400 s/dia → GB/dia → GB/mês → **TB/ano** — atualiza a cada input |
| 3 | **Barra de progresso** | Contador visual de tipos de evento configurados vs. total disponível |
| 4 | **Badge TOP** | Identifica automaticamente eventos com impacto >5% no volume total |
| 5 | **Tooltip de cálculo** | Hover sobre GB/dia mostra a conta completa: `Qtde × EPS × bytes × 86.400 = evt/dia → GB/dia → TB/ano` |
| 6 | **Coluna de Observação** | Campo de nota livre por linha (ex: "cliente confirmou 250 instâncias") — exportado no XLSX |

### 🔍 Navegação e filtros

| # | Funcionalidade | Descrição |
|---|---|---|
| 7 | **Filtro por categoria** | Sidebar e barra de ícones lateral, clique em qualquer categoria para filtrar a tabela |
| 8 | **Busca de tipo de evento** | Campo de pesquisa por nome ou fabricante em tempo real |
| 9 | **Filtro "Só preenchidos"** | Exibe apenas os tipos de evento com quantidade > 0 |
| 10 | **Sidebar retrátil** | Recolhe o painel de navegação para ampliar o espaço da tabela |
| 11 | **Redimensionamento de colunas** | Arraste a borda de qualquer coluna do cabeçalho para ajustar a largura |

### ➕ Eventos extras

| # | Funcionalidade | Descrição |
|---|---|---|
| 12 | **Evento Customizado** | Adiciona uma linha totalmente editável: nome, escopo, qtde, EPS/ativo e bytes/evento |
| 13 | **Duplicar Evento** | Modal com busca e checkboxes duplica qualquer tipo existente com quantidade independente (ex: dois fabricantes de NGFW) |

### 📊 Análise e comparação

| # | Funcionalidade | Descrição |
|---|---|---|
| 14 | **Cenários A e B** | Salve dois sizings diferentes e compare com delta de TB/ano e percentual de variação |
| 15 | **Gráfico de Composição** | Donut chart interativo com participação % de cada categoria no volume total |
| 16 | **Calculadora Rápida** | Aba dedicada — converte MB/GB/TB por dia, hora ou mês e EPS diretamente para TB/ano |

### 📄 Exportação

| # | Funcionalidade | Descrição |
|---|---|---|
| 17 | **Relatório PDF** | Aba 3 com layout A4: cabeçalho com nome do projeto, 5 métricas, donut chart, tabela detalhada e totais  exportado via print nativo do browser (sem dependências) |
| 18 | **Export XLSX** | Planilha profissional com formatação, cores por hierarquia, zebra striping, totais em verde e fórmulas, nome do projeto no título e no nome do arquivo |

### ⚙️ Produtividade

| # | Funcionalidade | Descrição |
|---|---|---|
| 19 | **Nome do projeto** | Campo no header — aparece no relatório PDF, no título do XLSX e no nome do arquivo exportado |
| 20 | **Persistência local** | Estado salvo automaticamente no `localStorage` dados, notas, tema, idioma e cenários preservados ao fechar o browser |
| 21 | **Compartilhar link** | Botão "Compartilhar" codifica o sizing completo na URL (base64), abra em outro browser e o estado é restaurado |
| 22 | **Tema claro / escuro** | Paleta Google Material Design — tipografia Google Sans + Roboto Mono (mesmas fontes do Chronicle SecOps) |
| 23 | **Multilíngue** | Interface completa em Português 🇧🇷, English 🇺🇸 e Español 🇪🇸 — incluindo labels, hints, placeholders e categorias |
| 24 | **Zero instalação** | Arquivo HTML único — roda localmente ou em qualquer hospedagem estática |

---

## 🚀 Como usar

### Opção 1 — Direto no browser (recomendado)

Baixe `secops_calculator.html` e abra em qualquer browser moderno. Funciona completamente offline.

### Opção 2 — GitHub Pages

1. Fork deste repositório
2. **Settings → Pages** → branch `main` → pasta `/root`
3. Acesse `https://seu-usuario.github.io/nome-do-repo`

### Opção 3 — Hospedagem estática

Qualquer servidor web estático funciona: Netlify, Vercel, S3, Azure Static Web Apps, etc.

---

## 📋 Fluxo de uso recomendado

```
1. Digite o nome do projeto / cliente no campo do header
        ↓
2. Aba "Sizing por Fonte"
   → Navegue pelas categorias na sidebar ou barra de ícones
   → Preencha a coluna "Qtde" com o número de ativos do ambiente
   → Ajuste EPS/ativo e bytes/evento se tiver dados reais
   → Use a coluna Observação para anotar contexto de cada linha
        ↓
3. Métricas atualizam em tempo real
   ✓ Badges TOP identificam os eventos de maior impacto
   ✓ Hover sobre GB/dia mostra o cálculo detalhado
        ↓
4. Se necessário:
   · Tipos de evento não listados  → "+ Evento Customizado" na sidebar
   · Múltiplos fabricantes         → "Duplicar Evento" na sidebar
   · Comparar dois escopos         → alterne Cenário A / B
   · Ver composição visual         → botão "Composição"
        ↓
5. Aba "Relatório"
   → Revise o layout A4 com gráfico e tabela completa
   → Clique "Imprimir / Salvar PDF" para exportar
        ↓
6. "Exportar XLSX" na sidebar
   → Planilha formatada pronta para a proposta
```

---

## 📐 Fórmula de cálculo

```
Volume diário (bytes) = Qtde × EPS/ativo × bytes/evento × 86.400 s/dia

GB/dia  = Volume diário ÷ 1.000.000.000  (10⁹)
GB/mês  = GB/dia × 30
TB/ano  = GB/dia × 365 ÷ 1.000
```

> **Padrão decimal:** 1 TB = 1.000 GB = 10¹² bytes  
> **EPS/ativo** e **bytes/evento** são referências de mercado editáveis, ajuste conforme o ambiente real do cliente.

---

## 🗂️ Categorias cobertas

| Categoria | Exemplos de tipos de evento |
|---|---|
| Servidores e SO | Windows Server, Linux, Kubernetes, VMware, Mainframe |
| Rede e conectividade | NGFW, WAF, IDS/IPS, SD-WAN, ZTNA, NetFlow, NAC, SASE |
| Endpoint | EDR/XDR, DLP, MDM/UEM, Patch Management, VDI, Browser Isolation |
| Identidade e acesso | Active Directory, Entra ID, Okta, CyberArk PAM, RADIUS, MFA |
| Aplicações e middleware | Web Servers, API Gateway, BD relacional/NoSQL, ERP, SAP, DevOps, ITSM |
| Cloud pública | AWS CloudTrail/VPC/GuardDuty, Azure Monitor/Sentinel, GCP Audit, Workspace |
| Segurança especializada | NDR, CASB, SOAR, Sandbox, DSPM, DAM, API Security, Microsegmentação |
| OT / IoT | SCADA, PLCs, Historian, Claroty, Nozomi, BMS, CFTV, Smart Meters |
| Dados / IA | Data Lake, ETL, ML Platform, GenAI/Copilot, Vector DB, Data Catalog |
| Telecomunicações | PABX, SBC, Contact Center, Unified Communications, Email Gateway |

---

## ⚠️ Recomendações de uso

### ✅ Use para:
- Estimativas iniciais de sizing para cotação do Chronicle SecOps
- Comparação de modelos de licenciamento (EPS vs TB/ano) com clientes
- Discovery técnico — identificar quais fontes de log existem no ambiente
- Geração de evidências documentadas em PDF para propostas comerciais
- Apresentações executivas com gráfico de composição por categoria

### ⚠️ Atenção:
- EPS/ativo são **médias de mercado** — variam por fabricante, versão e configuração de logging
- O cálculo representa **volume bruto ingerido** — sem compressão, filtros ou deduplicação
- Fontes com ingestão **gratuita** no Chronicle (Google Workspace, GCP Audit Logs, Chrome Enterprise) devem ser separadas do volume faturável
- Para propostas formais, valide sempre com dados reais do ambiente (relatórios do SIEM atual)

### ❌ Não use para:
- Cotações definitivas sem validação com dados reais do cliente
- Substituir o processo de sizing oficial do Google Cloud / parceiro autorizado

---

## 📦 Dependências

A ferramenta é um HTML standalone. A única dependência externa é o SheetJS, carregado **somente ao exportar XLSX**:

| Biblioteca | Versão | Uso | Carregamento |
|---|---|---|---|
| [SheetJS](https://sheetjs.com/) | 0.18.5 | Geração do XLSX | Sob demanda via CDN |

O **relatório PDF** usa `window.print()` nativo — zero dependências, 100% offline.  
Para uso completamente offline no XLSX, baixe o SheetJS e ajuste o `src` no código.

---

## 📄 Licença

MIT — veja [LICENSE](./LICENSE).

Os valores de EPS/ativo e bytes/evento são referências técnicas compiladas de documentação pública de fabricantes e benchmarks da indústria. Não representam dados proprietários de nenhum fabricante.

---

## 👤 Autor

**Matheus Damacena**  
Security Cloud Architect | Google Cloud Security Pre-Sales  
[secmath.com](https://secmath.com) · [LinkedIn](https://linkedin.com/in/matheusdamacena)

---

<div align="center">

*Construído para o ecossistema de parceiros Google Cloud Security no Brasil*

**⭐ Se esta ferramenta foi útil, deixe uma estrela no repositório**

</div>
