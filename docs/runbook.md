# Roteiro de triagem NOC

| Sintoma | Verificação | Próximo passo |
|---|---|---|
| Ping e agente sem resposta | Compare outros hosts e o caminho de rede | Verifique link, firewall e energia |
| Ping responde, agente não | Serviço do agente, porta e política de acesso | Valide logs, modo ativo/passivo e configuração |
| CPU elevada | Duração e processos responsáveis | Correlacione com tarefas e alterações |
| Memória elevada | Tendência, processos e paginação | Confirme impacto antes de intervir |
| Disco próximo do limite | Crescimento, logs e retenção | Encaminhe limpeza ou expansão aprovada |
| Uptime ausente | Estado e erro do item no Zabbix | Verifique suporte da chave e permissões |
| Tráfego inesperado | Unidade, contador e interface | Confirme coleta antes de investigar consumo |

1. Confirme a atualização da última amostra.
2. Identifique o alcance: um host, um segmento ou vários serviços.
3. Correlacione alertas de infraestrutura com falhas de aplicação.
4. Registre evidências, hipótese, ação e responsável.
5. Após recuperação, valide novas amostras e serviço funcional.

## Exercício fictício
`LAB-APP01` deixa de enviar dados enquanto `LAB-DC01` continua disponível. Verifique primeiro o alcance e a conectividade. Se o ping responder, investigue o agente e seu caminho de comunicação. Finalize somente após confirmar retomada da coleta e disponibilidade da aplicação.
