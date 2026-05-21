<div align="center">

<img src="https://img.shields.io/badge/SecOps-Sizing%20Tool-00e8c8?style=for-the-badge&logoColor=white" alt="SecOps Sizing Tool"/>

# SecOps Ingestion Sizing Tool

**Ferramenta de pré-venda técnica para dimensionamento de volume de ingestão do Google SecOps**

[![Version](https://img.shields.io/badge/versão-1.0.0-blue?style=flat-square)](https://github.com/)
[![Lang](https://img.shields.io/badge/idiomas-PT%20%7C%20EN%20%7C%20ES-green?style=flat-square)](https://github.com/)
[![License](https://img.shields.io/badge/licença-MIT-orange?style=flat-square)](./LICENSE)
[![Standalone](https://img.shields.io/badge/standalone-HTML%20único-purple?style=flat-square)](https://github.com/)

</div>

---

## 📌 Sobre

O **SecOps Ingestion Sizing Tool** resolve um problema crítico de pré-venda:

> *Algumas ferramentas de mercado são dimensionadas utilizando **EPS** (eventos por segundo). O Google Chronicle SecOps é licenciado por **TB/ano** (volume de dados ingeridos). Não existe conversão direta - e cotar sem entender o ambiente gera estimativas incorretas.*

Esta ferramenta permite calcular o volume estimado de ingestão de logs a partir do inventário real de ativos do cliente, produzindo a métrica correta para cotação do Chronicle SecOps.

---

## ✨ Funcionalidades

| Funcionalidade | Descrição |
|---|---|
| **110 fontes de log catalogadas** | Cobertura de Servidores, Rede, Endpoint, Identidade, Apps, Cloud, Segurança, OT/IoT, Dados/IA e Telecom |
| **Cálculo em tempo real** | EPS total → Eventos/dia → GB/dia → GB/mês → **TB/ano** |
| **Calculadora Rápida** | Converte GB/dia, GB/hora, GB/mês ou EPS direto para TB/ano |
| **Export XLSX profissional** | Planilha formatada com dados preenchidos, totais e fórmulas |
| **Nome do projeto** | Identifica a cotação no título e no nome do arquivo exportado |
| **Tema claro / escuro** | Alternância com persistência via localStorage |
| **Multilíngue** | Português 🇧🇷 · English 🇺🇸 · Español 🇪🇸 |
| **Redimensionamento de colunas** | Arraste a borda das colunas para ajustar |
| **Sidebar retrátil** | Expande o espaço da tabela quando necessário |
| **Zero dependências** | Arquivo HTML único, roda localmente ou em qualquer hospedagem estática |

---

## 🚀 Como usar

### Opção 1 — Direto no browser

Baixe o arquivo `secops_calculator.html` e abra no browser. Nenhuma instalação necessária.

### Opção 2 — GitHub Pages

1. Faça um fork deste repositório
2. Vá em **Settings → Pages**
3. Selecione a branch `main` e a pasta `/root`
4. Acesse via `https://seu-usuario.github.io/nome-do-repo`

### Opção 3 — Qualquer hospedagem estática

Basta hospedar o arquivo `secops_calculator.html` em qualquer servidor web estático (Netlify, Vercel, S3, etc.).

---

## 📋 Fluxo de uso recomendado

```
1. Informe o nome do projeto / cliente no campo do header
        ↓
2. Na aba "Sizing por Fonte", navegue pelas categorias
   e preencha a coluna "Qtde" com o número de ativos do ambiente
        ↓
3. Os totais atualizam em tempo real na barra de métricas
        ↓
4. Use a barra de métricas para verificar:
   ✓ EPS total estimado
   ✓ GB/dia de ingestão
   ✓ TB/ano → base para cotação Chronicle SecOps
        ↓
5. Clique "EXPORTAR XLSX" para gerar a planilha de evidência
   com todos os dados e cálculos formatados
```

---

## 📐 Como o cálculo funciona

```
Volume diário (bytes) = Qtde de ativos × EPS por ativo × tamanho médio do evento (bytes) × 86.400 s/dia

GB/dia  = Volume diário ÷ 1.000.000.000
GB/mês  = GB/dia × 30
TB/ano  = GB/dia × 365 ÷ 1.000
```

> **Padrão decimal:** 1 TB = 1.000 GB = 10¹² bytes  
> Os valores de **EPS/ativo** e **bytes/evento** são referências de mercado editáveis — ajuste conforme os dados reais do ambiente do cliente.

---

## 🗂️ Categorias de fontes cobertas

| Categoria | Fontes |
|---|---|
| Servidores e sistemas operacionais | Windows Server, Linux, Kubernetes, VMware, Mainframe... |
| Rede e infraestrutura | NGFW, WAF, IDS/IPS, SD-WAN, ZTNA, NetFlow, NAC... |
| Endpoint e proteção | EDR/XDR, DLP, MDM, Patch Management, VDI... |
| Identidade e acesso | Active Directory, Entra ID, Okta, CyberArk, PAM, RADIUS... |
| Aplicações e middleware | Web Servers, API Gateway, Bancos de dados, ERP, SAP, DevOps... |
| Cloud pública | AWS, Azure, GCP — CloudTrail, VPC Flow, GuardDuty, Sentinel... |
| Segurança especializada | NDR, CASB, SOAR, Sandbox, DSPM, DAM, Microsegmentação... |
| OT / IoT | SCADA, PLCs, Historian, Claroty, Nozomi, BMS, CFTV... |
| Dados / IA | Data Lake, ETL, ML Platform, GenAI, Vector DB... |
| Telecom | PABX, SBC, Contact Center, Unified Communications... |

---

## ⚠️ Recomendações de uso

### ✅ Use esta ferramenta para:
- Estimativas iniciais de sizing para cotação do Chronicle SecOps
- Comparação de modelos de licenciamento (EPS vs TB/ano) com clientes
- Discovery técnico — identificar quais fontes de log existem no ambiente
- Geração de evidências documentadas para propostas comerciais

### ⚠️ Atenção:
- Os valores de **EPS/ativo** são **médias de mercado** — variam por fabricante, versão e configuração
- O cálculo representa o **volume bruto ingerido**, sem considerar compressão, filtros de descarte ou deduplicação
- Fontes com ingestão **gratuita** no Chronicle SecOps (Google Workspace, GCP Audit Logs, Chrome Enterprise) devem ser separadas do volume faturável na cotação final
- Para propostas formais, valide sempre com dados reais do ambiente (relatórios de ingestão do SIEM atual)

### ❌ Não use para:
- Cotações definitivas sem validação com dados reais do cliente
- Substituir o processo de sizing oficial do Google Cloud / parceiro autorizado

---

## 📦 Dependências externas

A ferramenta é um HTML standalone. A única dependência externa é carregada **somente no momento do export**:

| Biblioteca | Versão | Uso | CDN |
|---|---|---|---|
| [SheetJS (xlsx)](https://sheetjs.com/) | 0.18.5 | Geração do arquivo XLSX | cdnjs.cloudflare.com |

> A ferramenta funciona **completamente offline** — a biblioteca SheetJS só é necessária ao clicar em "Exportar XLSX".  
> Para uso 100% offline, baixe o SheetJS e ajuste o `src` no código.

---

## 📄 Licença

```
MIT License

Copyright (c) 2026 Matheus Damacena

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

> **Nota sobre dados:** os valores de EPS/ativo e bytes/evento são referências técnicas de mercado compiladas de documentação pública de fabricantes e benchmarks de indústria. Não representam dados proprietários de nenhum fabricante.

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
