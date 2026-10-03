# 🤖 Agente de Análise de Automação

Agente em Python que lê um log de tarefas manuais (computador e plataformas), calcula onde o tempo é gasto e usa o Claude para indicar **o que dá para automatizar e como fazer**.

## ✨ O que ele faz

1. Lê o log de tarefas (CSV ou Excel)
2. Calcula as horas/mês por tarefa e seleciona as mais custosas
3. Envia ao Claude, que avalia o potencial de automação (alto, médio, baixo), a ferramenta recomendada, o passo a passo, o esforço e os riscos
4. Gera um relatório priorizado com economia estimada e payback

## 📁 Estrutura

```
agente-automacao/
├── agente_automacao.py     # código principal
├── data/
│   └── tarefas_exemplo.csv # log de exemplo
├── output/                 # relatórios gerados (ignorado pelo git)
├── requirements.txt
├── .env.example
├── .gitignore
├── LICENSE
└── README.md
```

## 🚀 Como usar

```bash
git clone https://github.com/<seu-usuario>/agente-automacao.git
cd agente-automacao

python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt

cp .env.example .env           # edite e coloque sua ANTHROPIC_API_KEY
python agente_automacao.py data/tarefas_exemplo.csv --top 10
```

Saídas: `output/relatorio_automacao.xlsx` e `output/relatorio_automacao.md`.

## 🧾 Formato do log de tarefas

| Coluna | Obrigatória | Descrição |
|---|---|---|
| `plataforma` | ✅ | Sistema/ferramenta onde a tarefa acontece |
| `tarefa` | ✅ | Nome da tarefa |
| `duracao_min` | ✅ | Minutos por execução |
| `vezes_por_semana` | ✅ | Frequência semanal |
| `descricao` | opcional | Passo a passo da tarefa |
| `ferramentas` | opcional | Ex.: Excel, Power BI, Outlook |

## ⚠️ Observações

- A economia estimada usa fatores fixos (80% alto, 50% médio, 10% baixo); ajuste em `montar_relatorio`.
- Nunca suba o arquivo `.env` para o repositório.

## 🗺️ Próximos passos

- [ ] Importar histórico do ActivityWatch automaticamente
- [ ] Exportar relatório em PDF/DOCX
- [ ] Dashboard em Power BI com o resultado

## 📄 Licença

MIT

