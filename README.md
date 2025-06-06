# ⚡ REDE-LUZ - Detecção Inteligente de Apagões com Python e MediaPipe

## 🧠 Descrição do Problema

A falta de energia elétrica é um desafio recorrente em diversas regiões do Brasil, afetando diretamente a qualidade de vida da população e a operação de serviços essenciais como hospitais, sistemas de transporte e comunicação.

Durante apagões, principalmente em áreas sem internet, a comunicação entre cidadãos e autoridades se torna ineficiente. Isso atrasa diagnósticos de falha e reduz a capacidade de resposta rápida das concessionárias de energia.

---

## 💡 Visão Geral da Solução

**REDE-LUZ** é uma solução local, desenvolvida em **Python com MediaPipe**, que monitora ambientes em tempo real e detecta **apagões** com base em:

- Baixa **luminosidade** (indicador de possível falta de energia);
- Gesto de **mão aberta**, sinalizado por um usuário.

Esses eventos são automaticamente **registrados localmente** em um arquivo `.csv` com:

- Data e hora do alerta;
- Intensidade da luz;
- Região monitorada;
- Duração do evento.

Além disso, ao final da execução, um **relatório completo em `.txt`** é gerado com o resumo dos apagões detectados.

> 🧭 Ideal para locais onde a comunicação com a internet pode ser interrompida. Os dados ficam armazenados localmente e podem ser compartilhados entre dispositivos via Bluetooth para formar uma rede descentralizada de reportes.

---

## 🖼️ Exemplos Visuais

**Execuções disponíveis em:**  
- `assets/prints/apagao.png` → Exemplo com apagão detectado  
- `assets/prints/normal.png` → Exemplo com ambiente claro  
- `assets/prints/csv.png` → Log de alertas em `.csv`  

---

## 🚀 Instruções de Uso

### ✅ Requisitos

- Python 3.10+
- `mediapipe`
- `opencv-python`
- `numpy`

Instale com:

```bash
pip install -r requirements.txt
```

### 📦 Estrutura do Projeto

```
rede-luz/
├── assets/
│   └── videos/
│       └── teste_gestos.mp4        # Vídeo de teste simulado
│   └── prints/
│       ├── print_apagao.png
│       ├── print_normal.png
│       └── print_csv.png
├── alertas_log.csv                 # Log dos eventos detectados
├── relatorio_apagoes.txt          # Relatório final automático
├── main.py                        # Código principal
├── requirements.txt
└── README.md
```

### ▶️ Execução

```bash
python main.py
```

Você pode alterar para webcam ao invés de vídeo editando esta linha no código:

```python
VIDEO_PATH = 0  # Para usar webcam ao vivo
```

---

## 📈 Saída Exemplo (CSV)

```
data_hora,aviso,luminosidade,regiao,duracao
2025-05-29 23:17:32,Alerta de apagão confirmado,33,São Paulo - Zona Sul,4.5s
```

---

## 🧾 Saída Exemplo (Relatório `.txt`)

```
=== RELATÓRIO DE APAGÕES DETECTADOS ===

Data da geração: 2025-05-29 23:48:14
Região monitorada: São Paulo - Zona Sul
Total de apagões detectados: 2

Detalhes dos apagões:
Data/Hora Início | Duração (s) | Luminosidade Média
-------------------------------------------------
2025-05-29 23:44:18 | 4.5 | 33
2025-05-29 23:45:12 | 3.9 | 31

=== FIM DO RELATÓRIO ===
```

---

## 🔗 Integração com Rede Descentralizada via Bluetooth

Durante quedas de energia com ausência total de internet, o **REDE-LUZ** permite que os alertas registrados localmente por diferentes cidadãos sejam **compartilhados automaticamente via Bluetooth** com dispositivos próximos da **mesma região**.

### 📡 Coleta Colaborativa Offline:

1. O sistema detecta o apagão e salva os dados localmente.
2. Outros dispositivos próximos são identificados automaticamente via Bluetooth.
3. Os arquivos `.csv` e `.txt` são trocados entre os dispositivos.
4. Se os registros forem da mesma região, o sistema gera um **relatório consolidado** (`relatorio_unificado.txt`).

---

## 🤖 Envio Automático para as Autoridades

Quando qualquer dispositivo volta a ter acesso à internet:

- O sistema detecta a conectividade;
- Verifica se o dispositivo está na mesma região dos alertas consolidados;
- **Envia automaticamente** o relatório às autoridades (via API, e-mail ou outro canal).

---

## ✅ Vantagens

- Totalmente funcional **offline**;
- Comunicação **colaborativa e descentralizada** via Bluetooth;
- **Automação completa**: detecção, registro, unificação e envio;
- Sem necessidade de intervenção do usuário após instalação.

---

## 🧩 Expansão Futura

- Interface gráfica com botão de envio manual;
- Geolocalização via GPS;
- Aplicativo mobile sincronizado com a versão desktop;
- Visualização de mapa com áreas mais afetadas;
- Painel de controle para órgãos públicos.

---

## 📌 Fluxo Final do REDE-LUZ

1. Detecção automática (gesto + baixa luz);  
2. Registro local no CSV e relatório `.txt`;  
3. Compartilhamento automático via Bluetooth;  
4. Consolidação automática dos dados recebidos;  
5. Envio automático ao restabelecer conexão.

---

## 👨‍💻 Desenvolvido por

**Enzo Luiz Goulart** – RM99666  
**Gustavo Henrique Santos Bonfim** – RM98864  
**Lucas Yuji Farias Umada** – RM99757  

Curso: Engenharia de Software – 3º Ano  
Disciplina: Sistemas Inteligentes / Visão Computacional

---

## 📄 Licença

Projeto acadêmico — uso educacional.
