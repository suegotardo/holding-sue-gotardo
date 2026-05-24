# SUE HOLDING — Dashboard de Investimentos

> Carteira pessoal consolidada com cotações ao vivo, proventos, notícias, pontos de atenção e plano de independência financeira 2036.

---

## 🚀 Como hospedar no GitHub Pages (passo a passo)

### 1. Criar o repositório

1. Acesse [github.com](https://github.com) e faça login
2. Clique em **"New repository"** (botão verde no canto superior direito)
3. Preencha:
   - **Repository name:** `sue-holding` (ou o nome que preferir)
   - **Visibility:** ✅ Public
   - Deixe os demais campos em branco
4. Clique em **"Create repository"**

### 2. Fazer upload dos arquivos

1. Dentro do repositório recém-criado, clique em **"Add file" → "Upload files"**
2. Arraste os dois arquivos: `index.html` e `README.md`
3. Clique em **"Commit changes"**

### 3. Ativar o GitHub Pages

1. Vá em **Settings** (aba no menu do repositório)
2. No menu lateral, clique em **Pages**
3. Em **"Source"**, selecione **"Deploy from a branch"**
4. Branch: `main` / Pasta: `/ (root)`
5. Clique em **Save**
6. Aguarde **1 a 2 minutos**

Seu dashboard estará em:
```
https://SEU_USUARIO.github.io/sue-holding/
```

---

## 📁 Arquivos do projeto

```
sue-holding/
├── index.html   ← dashboard completo (único arquivo necessário)
└── README.md    ← este arquivo
```

---

## 📡 Cotações ao vivo — Brapi.dev

O dashboard usa a [Brapi.dev](https://brapi.dev) para cotações em tempo real.
A versão `token=demo` funciona com limite reduzido.

**Para aumentar o limite (recomendado):**

1. Crie conta gratuita em [brapi.dev](https://brapi.dev) e copie seu token
2. No `index.html`, localize (~linha 720):
   ```javascript
   const r = await fetch('https://brapi.dev/api/quote/'+ALL_TK.join(',')+'?token=demo');
   ```
3. Substitua `token=demo` pelo seu token:
   ```javascript
   const r = await fetch('https://brapi.dev/api/quote/'+ALL_TK.join(',')+'?token=SEU_TOKEN');
   ```
4. Salve e faça commit no GitHub

---

## ✏️ Como atualizar seus dados

Abra o `index.html` em qualquer editor de texto e edite as variáveis no início do script.

### Adicionar ativo novo

```javascript
// Em FIIS:
{ticker:'MXRF11', nome:'Maxi Renda', qtd:100, pm:10.50, dy:0.13,
 teto:12, seg:'Papel', nota:'Comprar', cor:'#16a34a'},

// Em ACOES:
{ticker:'ITUB4', nome:'Itaú Unibanco', qtd:50, pm:35.00, dy:0.06,
 teto:42, setor:'Banco', nota:'Segurar', cor:'#0ea5e9'},
```

| Campo | Descrição |
|---|---|
| `ticker` | Código do ativo (ex: `BTLG11`) |
| `qtd` | Quantidade de cotas/ações |
| `pm` | Preço médio de compra |
| `dy` | Dividend Yield anual (ex: `0.13` = 13%) |
| `teto` | Preço teto para Margem de Segurança |
| `nota` | `Comprar`, `Segurar` ou `Aguardar` |
| `cor` | Cor do ícone (hex, ex: `#2563eb`) |

### Registrar provento recebido

```javascript
{data:'2026-06-17', ticker:'BTLG11', tipo:'Provento', vUnit:0.79, qtd:87, total:68.73},
```

| Campo | Descrição |
|---|---|
| `data` | Data no formato `AAAA-MM-DD` |
| `tipo` | `Dividendo`, `Provento` ou `JCP` |
| `vUnit` | Valor por cota/ação |
| `total` | Valor total recebido |

---

## 📊 Abas do Dashboard

| Aba | Conteúdo |
|---|---|
| **Carteira** | KPIs gerais, composição, projeção 2036 |
| **Notícias** | Últimas notícias dos seus ativos |
| **FIIs** | Cards com cotação ao vivo, M.S., métricas |
| **Ações** | Cards com cotação ao vivo, M.S., métricas |
| **Proventos** | Histórico completo + gráficos |
| **Pontos de Atenção** | Alertas automáticos |
| **Desempenho** | Resultado anual e evolução patrimonial |

---

## 🔄 Atualização automática

- Dados estáticos carregam **imediatamente** ao abrir
- Cotações ao vivo chegam em ~1 segundo
- Atualização automática a cada **60 segundos**

> ⚠️ Cotações ao vivo funcionam somente no GitHub Pages (ou servidor).
> Ao abrir o arquivo localmente (`file://`), o navegador bloqueia requisições externas — isso é normal.

---

## 🎯 Plano de Independência Financeira 2036

| Ano | Evento | Renda Est. |
|---|---|---|
| 2026 | Base + aporte R$ 25k | R$ 369/mês |
| 2028 | Selic 1 migra → RV | R$ 800/mês |
| 2029 | Selic 2 migra → RV | R$ 1.174/mês |
| 2032 | IPCA+ migra → RV | R$ 2.060/mês |
| 2033 | Selic 3 migra → RV | R$ 2.396/mês |
| **2036** | **Meta atingida 🎯** | **R$ 6.407/mês** |

---

*Cotações: [Brapi.dev](https://brapi.dev) · Hospedagem: GitHub Pages · Criado com Claude (Anthropic)*
