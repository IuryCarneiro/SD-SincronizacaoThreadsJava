# Atividade 1
## Diferenças entre os logs

### Log 1 


- **Repetições no consumo**:
  - Consumidor leu o mesmo valor `0` e `12` várias vezes consecutivas.
  - Máximo de repetições no consumo: **5 vezes (valor `25`)**.
- **Alternância**:
  - Alternância frequente entre produtor e consumidor.

---

### Log 2


- **Repetições no consumo**:
  - Consumidor leu o valor `29` até **10 vezes consecutivas**.
- **Menos alternância**:
  - O produtor produziu vários valores consecutivamente, como `10` a `13`, antes do consumidor agir.

---

### Comparação Geral

| Característica           | Log 1                            | Log 2                          |
|--------------------------|-----------------------------------|--------------------------------|
| **Repetições no consumo** | Máximo 5 vezes (`25`)            | Máximo 10 vezes (`29`)         |
| **Alternância**           | Mais equilibrada                | Menos alternância (produtor ativo por mais tempo) |
| **Execução**              | Consumidor menos ativo em alguns momentos | Consumidor mais ativo (leitura repetitiva em alguns momentos) |

---

### Explicação das Diferenças

As diferenças nos logs se devem a:
- **Agendamento das threads pelo sistema operacional**, que pode variar em cada execução.
- **Falta de sincronização** entre as threads, permitindo leituras repetidas de valores sem controle.

# Atividade 2
# Comparação de Execuções: Sem Sincronização vs. Com Monitor

## Descrição das Execuções

### Execuções Sem Sincronização (Log 1 e Log 2)

Nas execuções anteriores, **não havia sincronização** entre o produtor e o consumidor, o que resultou em:

- **Repetição de valores**: O consumidor frequentemente lê o mesmo valor várias vezes consecutivas.
- **Alternância desordenada**: A troca entre produtor e consumidor é imprevisível, dependendo do agendamento das threads pelo sistema operacional.
- **Condições de corrida**: Ocorreram inconsistências no acesso à variável compartilhada, causando comportamento caótico.

#### Execução Com Monitor

Nesta execução, o uso de monitor (com synchronized) garantiu **controle eficiente** entre produtor e consumidor:

**-Coordenador com flags**: As variáveis Pronto e Ocupado garantem que as threads não acessem o recurso simultaneamente.
**Sem repetição de valores**: O consumidor só lê o valor produzido mais recentemente.
**Comportamento previsível**: O programa segue uma alternância organizada entre produzir e consumir.

# Atividade 3
## Comparação de Execuções: Sem Sincronização, Com Monitor e Com Eventos

### Descrição das Execuções

#### Atividade Prática 01: Sem Sincronização
- **Problemas Observados**:
  - O **consumidor lê valores repetidos**, indicando condições de corrida.
  - A **alternância entre produtor e consumidor é desordenada**, causada pela falta de controle explícito.
  - **Condições de corrida** frequentemente resultam em comportamento inconsistente. 
 ##### Atividade Prática 02: Com Monitor
**Melhorias Observadas**:
- **Sincronização** explícita elimina condições de corrida.
- O consumidor lê apenas **valores atualizados** pelo produtor.
- A alternância entre produtor e consumidor é **ordenada** e segue o fluxo lógico. 
###### Atividade Prática 03: Com Eventos (wait e notify)
**Melhorias Adicionais**:
O uso de eventos (wait e notify) introduz um **mecanismo eficiente** de controle entre threads.
As threads entram em espera ativa controlada, reduzindo o **uso desnecessário da CPU**.
Assim como na execução com monitor, o consumidor lê **valores atualizados** pelo produtor.
Comportamento previsível e **consistente**.