# Configuração de referência

Exemplos conceituais para um laboratório próprio. Ajuste as chaves, consultas e expressões aos templates e versões instaladas; este arquivo não é um template importável.

| Indicador | Referência | Unidade / observação |
|---|---|---|
| CPU | Item do template Windows | %; confirme a chave disponível |
| Memória | Item do template Windows | %; não misture percentual usado e livre |
| Disco C: | Used e Total ou pused | % usado; proteger divisão por zero |
| Uptime | system.uptime | segundos; formatar como duração |
| Agente respondendo | agent.ping | última amostra válida é 1 |
| Disponibilidade do agente passivo | zabbix[host,agent,available] | 0 desconhecido, 1 disponível, 2 indisponível |
| ICMP | icmpping / icmppingloss / icmppingsec | disponibilidade, %, segundos |
| Tráfego | ifHCInOctets / ifHCOutOctets | contador SNMP de 64 bits |

## Indicador calculado NOC
Referência usada: `1-nodata(//agent.ping,1m)`, com atualização a cada 30 segundos. Representa presença de dados recentes. Não substitui uma avaliação de saúde do servidor nem confirma disponibilidade da aplicação. Valores ausentes devem aparecer como “sem dados”, evitando um falso estado saudável.

## Tráfego SNMP
Colete contadores de octetos das interfaces identificadas no laboratório. Aplique “Change per second” e depois multiplicação por 8, convertendo octetos/s em bits/s. Considere reinicialização do contador e mudança de índice da interface. Os rótulos fictícios são WAN-A e WAN-B, sem relação com portas reais.

## Grafana
Configure a integração Zabbix usando credenciais próprias e privilégio mínimo. Agrupe os hosts do laboratório em `LAB-Servers`. Consulte separadamente CPU, RAM, disco, uptime e status. O HTML incluído é uma referência estática; adapte-o ao painel e ao mecanismo de templates que sua versão suporta. Não habilite HTML sem sanitização apenas para copiar o exemplo.

## Alertas
Exemplo de política: grupo de laboratório, severidades Alta e Desastre, mensagens de problema e recuperação. Ping e agente representam falhas diferentes e podem duplicar notificações; use dependências ou condições revisadas conforme a topologia. Ausência de resposta ICMP não comprova servidor desligado.
