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

> *O QRadar é licenciado por **EPS** (eventos por segundo). O Google Chronicle SecOps é licenciado por **TB/ano** (volume de dados ingeridos). Não existe conversão direta — cotar sem entender o ambiente gera estimativas incorretas e perda de negócio.*

Esta ferramenta permite calcular o volume estimado de ingestão a partir do inventário real do cliente, produzindo a métrica correta para cotação do Chronicle SecOps — com relatório exportável em PDF e XLSX.

---

## ✨ Funcionalidades

| # | Funcionalidade | Descrição |
|---|---|---|
| 1 | **146 tipos de evento catalogados** | 10 categorias: Servidores, Rede, Endpoint, Identidade, Apps, Cloud, Segurança, OT/IoT, Dados/IA, Telecom |
| 2 | **Cálculo em tempo real** | EPS × bytes/evt × 86.400 s/dia → GB/dia → GB/mês → **TB/ano** |
| 3 | **Barra de progresso** | Contador de tipos de evento configurados vs. total disponível |
| 4 | **Badge TOP** | Identifica automaticamente os eventos com maior impacto no volume (>5% do total) |
| 5 | **Tooltip de cálculo** | Hover sobre GB/dia mostra a conta completa por linha |
| 6 | **Calculadora Rápida** | Converte MB/GB/TB por dia, hora, mês ou EPS direto para TB/ano |
| 7 | **Evento Customizado** | Adiciona tipos de evento personalizados com fórmula padrão |
| 8 | **Duplicar Evento** | Copia qualquer tipo de evento para usar com quantidades diferentes (ex: dois fabricantes de NGFW) |
| 9 | **Coluna de Observação** | Campo de nota livre por linha, exportado no XLSX |
| 10 | **Cenários A / B** | Compare dois sizing diferentes com delta de TB/ano |
| 11 | **Gráfico de Composição** | Donut chart interativo com participação % por categoria |
| 12 | **Relatório PDF** | Aba dedicada com layout A4: métricas, gráfico e tabela detalhada — exportável via print do browser |
| 13 | **Export XLSX** | Planilha profissional com formatação, cores e totais |
| 14 | **Nome do projeto** | Aparece no header, no PDF e no nome do arquivo XLSX |
| 15 | **Persistência local** | Estado salvo automaticamente no `localStorage` — nenhum dado perdido ao fechar |
| 16 | **Compartilhar link** | Codifica o sizing na URL (base64) para enviar para um colega |
| 17 | **Tema claro / escuro** | Google Material Design — tipografia Google Sans + Roboto Mono |
| 18 | **Multilíngue** | Português 🇧🇷 · English 🇺🇸 · Español 🇪🇸 |
| 19 | **Zero dependências** | HTML único — SheetJS carregado só ao exportar XLSX |

---

## 🚀 Como usar

### Opção 1 — Direto no browser (sem instalação)

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
2. Aba "Sizing por Fonte" → navegue pelas categorias na sidebar
   → preencha a coluna "Qtde" com o número de ativos do ambiente
        ↓
3. Métricas atualizam em tempo real (EPS total, GB/dia, TB/ano)
   Badges TOP identificam os eventos de maior impacto
        ↓
4. Se necessário:
   · Adicionar tipos de evento não listados → "+ Evento Customizado"
   · Cliente com múltiplos fabricantes → "Duplicar Evento"
   · Comparar dois escopos → Cenário A vs B
        ↓
5. Aba "Relatório" → revise o PDF com gráfico e tabela completa
   → botão "Imprimir / Salvar PDF" para exportar
        ↓
6. Botão "Exportar XLSX" na sidebar → planilha formatada para proposta
```

---

## 📐 Fórmula de cálculo

```
Volume diário = Qtde × EPS/ativo × bytes/evento × 86.400 s/dia

GB/dia  = Volume diário ÷ 10⁹
GB/mês  = GB/dia × 30
TB/ano  = GB/dia × 365 ÷ 1.000
```

> **Padrão decimal:** 1 TB = 1.000 GB = 10¹² bytes  
> **EPS/ativo** e **bytes/evento** são referências de mercado — ajuste conforme o ambiente real do cliente.

---

## 🗂️ Categorias cobertas

| Categoria | Exemplos de tipos de evento |
|---|---|
| Servidores e SO | Windows Server, Linux, Kubernetes, VMware, Mainframe |
| Rede e conectividade | NGFW, WAF, IDS/IPS, SD-WAN, ZTNA, NetFlow, NAC, SASE |
| Endpoint | EDR/XDR, DLP, MDM/UEM, Patch Management, VDI |
| Identidade e acesso | Active Directory, Entra ID, Okta, CyberArk PAM, RADIUS |
| Aplicações e middleware | Web Servers, API Gateway, BD relacional/NoSQL, ERP, SAP, DevOps |
| Cloud pública | AWS CloudTrail/VPC/GuardDuty, Azure Monitor/Sentinel, GCP Audit, Workspace |
| Segurança especializada | NDR, CASB, SOAR, Sandbox, DSPM, DAM, API Security |
| OT / IoT | SCADA, PLCs, Historian, Claroty, Nozomi, BMS, CFTV |
| Dados / IA | Data Lake, ETL, ML Platform, GenAI/Copilot, Vector DB |
| Telecomunicações | PABX, SBC, Contact Center, Unified Communications |

---

## ⚠️ Recomendações de uso

### ✅ Use para:
- Estimativas iniciais de sizing para cotação do Chronicle SecOps
- Comparação de modelos de licenciamento (EPS vs TB/ano) com clientes
- Discovery técnico — identificar quais fontes de log existem no ambiente
- Geração de evidências documentadas em PDF para propostas comerciais

### ⚠️ Atenção:
- EPS/ativo são **médias de mercado** — variam por fabricante, versão e configuração de logging
- O cálculo representa **volume bruto ingerido** — sem compressão, filtros ou deduplicação
- Fontes com ingestão **gratuita** no Chronicle (Google Workspace, GCP Audit Logs, Chrome Enterprise) devem ser separadas do volume faturável
- Para propostas formais, valide com dados reais (relatórios do SIEM atual do cliente)

### ❌ Não use para:
- Cotações definitivas sem validação com dados reais
- Substituir o processo de sizing oficial do Google Cloud / parceiro autorizado

---

## 📦 Dependências

A ferramenta é um HTML standalone. Dependência externa carregada **apenas ao exportar XLSX**:

| Biblioteca | Versão | Uso | Carregamento |
|---|---|---|---|
| [SheetJS](https://sheetjs.com/) | 0.18.5 | Geração do XLSX | Sob demanda via CDN |

O **relatório PDF** usa `window.print()` nativo — zero dependências, funciona 100% offline.

---

## 📄 Licença

MIT — veja [LICENSE](./LICENSE).

Os valores de EPS/ativo e bytes/evento são referências técnicas de mercado compiladas de documentação pública de fabricantes e benchmarks da indústria. Não representam dados proprietários de nenhum fabricante.

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
