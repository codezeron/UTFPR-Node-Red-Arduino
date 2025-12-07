# 🚀 Projeto IoT: Controle de LED com Node-RED e Arduino

## 📋 Sobre o Projeto
Sistema de controle remoto para LED com capacidade de enviar alertas via SMS quando ativado. O projeto demonstra a integração entre Arduino (hardware), Node-RED (automação) e Twilio (comunicação).

## 🛠️ Como Preparei o Hardware

### Componentes Necessários:
- Arduino Uno
- LED
- Resistor de 220Ω
- Cabos jumper

### Montagem do Circuito:
```
Arduino Pin 12 → Resistor 220Ω → LED (ânodo) → LED (cátodo) → GND
```

**Nota:** O resistor em série limita a corrente para proteger o LED.

## 💻 Configuração do Software

### 1. Preparação do Arduino
- Abra o **Arduino IDE**
- Vá em `File → Examples → Firmata → StandardFirmata`
- Conecte o Arduino via USB
- Faça upload do código para a placa

### 2. Configuração do Node-RED
```bash
# Inicie o Node-RED
node-red
```

Acesse: `http://localhost:1880`

### 3. Fluxo Node-RED
O fluxo contém:
- Dois botões injetores (Ligar/Desligar)
- Função para processar comandos
- Saída para Arduino (controle do LED)
- Conexão com Twilio para alertas

## 🔌 Conexões do Sistema
```
[Interface Node-RED] → [Arduino via Serial] → [LED no pino 12]
                    ↘ [Twilio API] → [SMS para celular]
```

## 📱 Funcionalidades

### Botão "LIGAR" (true):
1. ✅ Acende o LED no pino 12
2. 📨 Envia SMS de alerta via Twilio
3. 🖥️ Exibe mensagem de alerta no debug

### Botão "DESLIGAR" (false):
1. 🔴 Apaga o LED no pino 12
2. ❌ **NÃO** envia SMS

## 🧪 Testando sem Custos
**Importante:** Para testes iniciais sem gastar créditos do Twilio:

1. Substitua o nó `twilio out` por `debug`
2. Configure o debug para mostrar:
   ```
   🚨 ALERTA SIMULADO: Porta aberta!
   📱 SMS seria enviado para: +5511999999999
   ```

3. Teste alternando os botões
4. Verifique se o LED responde corretamente
5. Confirme as mensagens no painel debug

## ⚙️ Configuração do Twilio (Opcional)
Quando estiver pronto para enviar SMS reais:

1. Crie conta em [twilio.com](https://www.twilio.com)
2. Obtenha:
   - Account SID
   - Auth Token
   - Número Twilio
3. Configure no nó `twilio-api`
4. Adicione números de destino autorizados

## 🔍 Verificação do Funcionamento

### Teste 1: Hardware
- LED acende ao clicar "LIGAR"?
- LED apaga ao clicar "DESLIGAR"?
- Nenhum componente esquenta excessivamente?

### Teste 2: Software
- Mensagens aparecem no debug?
- Conexão com Arduino permanece estável?
- Botões respondem imediatamente?

### Teste 3: Integração
- Fluxo executa sem erros?
- Timing entre ações é adequado?
- Sistema pode ser reiniciado sem problemas?

## 🐛 Solução de Problemas Comuns

### LED não acende:
- Verifique polaridade do LED
- Confirme resistor de 220Ω
- Teste com pino 10 (LED interno)

### Arduino não conecta:
- Feche Arduino IDE durante uso do Node-RED
- Verifique porta COM correta
- Reinicie o Node-RED

### SMS não envia:
- Confirme créditos na conta Twilio
- Verifique números no formato internacional
- Teste com debug primeiro

## 📈 Expansões Possíveis

1. **Dashboard Web**: Adicione `node-red-dashboard`
2. **Controle por Voz**: Integre com Alexa/Google Assistant
3. **Registro de Eventos**: Salve logs em banco de dados
4. **Controle por Botão Físico**: Adicione entrada digital
5. **Agendamento**: Acione em horários específicos

## 🎯 Pontos de Atenção

- ⚡ **Sempre** use resistor com LED
- 🔒 Mantenha credenciais do Twilio em variáveis de ambiente
- 📊 Monitore o uso da API Twilio para evitar custos excessivos
- 🔌 Desconecte a alimentação antes de modificar o circuito

## 📄 Licença
Projeto educacional - livre para uso e modificação

## 👥 Contribuição
Sugestões e melhorias são bem-vindas!

---

**Pronto para usar!** 🎉 
Clone, ajuste conforme suas necessidades e comece a automatizar!

---
