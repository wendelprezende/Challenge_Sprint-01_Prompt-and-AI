ChargeGrid Assistant
EV Challenge 2026 | FIAP | Sprint 1 — Prompt and Artificial Intelligence | Equipe 03

- Integrantes -
Nomes | RM
Anna Karla | 569604
Arthur Araújo | 573308
Beatriz da Silva | 570619
Daniel Alejandro | 573075
Victor Hugo Lavaqui | 573838
Wendel Pedro | 573126

- Problema Abordado -

   Os eletropostos comerciais modernos carecem de mecanismos integrados de comunicação com o usuário final. O motorista de veículo elétrico (EV) frequentemente enfrenta dificuldades para iniciar sessões de carregamento, compreender o valor cobrado, acompanhar o progresso da recarga e resolver problemas técnicos no local, sem nenhum canal de suporte imediato e inteligente disponível.
   Conforme identificado no estudo do ChargeGrid Intelligence, o Problema 3 aponta diretamente para a "experiência do usuário comprometida": falta de instruções claras, ausência de previsão de encerramento da sessão e inexistência de canal de suporte acessível no próprio eletroposto. A Solução 3 propõe exatamente o que este chatbot implementa: uma interface transparente com canal de suporte atendido por IA integrada ao sistema, capaz de traduzir dados técnicos em linguagem simples para o usuário final.

- Proposta do Chatbot -

O ChargeGrid Assistant é um chatbot conversacional voltado ao usuário final (motorista do EV), disponível diretamente na interface do eletroposto (totem touchscreen) e via aplicativo mobile. Seu objetivo é guiar o usuário em todas as etapas da sessão de carregamento, responder dúvidas sobre tarifação e oferecer suporte de primeiro nível em linguagem simples e acessível, sem exigir nenhum conhecimento técnico prévio.

- Persona Atendida: Motorista de EV -

Justificativa da escolha: O motorista de EV é o usuário com maior frequência de interação direta com o eletroposto e o principal afetado por falhas de experiência. Diferentemente do operador comercial ou do técnico de manutenção, o motorista não possui treinamento técnico sobre o sistema e depende completamente de orientações claras e imediatas para utilizar o serviço com autonomia. Atender essa persona com IA conversacional resolve o Problema 3 do ChargeGrid de forma direta, gerando impacto imediato na satisfação, retenção e inclusão de usuários de todos os perfis, incluindo aqueles com pouca familiaridade com tecnologia.

- Escopo de Atuação -

*Orientação sobre início e encerramento de sessão de carregamento
*Informações em tempo real sobre progresso de recarga (% de carga, tempo restante, kWh consumidos)
*Esclarecimentos sobre tarifação dinâmica e formas de pagamento (PIX, cartão de crédito e débito)
*Suporte a dúvidas frequentes (FAQ operacional)
*Escalamento automático para suporte técnico presencial em casos de falhas físicas (cabo com defeito, conector travado, falha de autenticação no totem)

- Tecnologias Selecionadas -

| Tecnologia | Função | Justificativa |
OpenAI API (GPT-4o) | Modelo de linguagem principal | Alta capacidade de compreensão contextual em português, fidelidade a system prompts detalhados e latência aceitável para interações em tempo real
Python + FastAPI | Backend do chatbot | Leveza, performance em APIs REST e ampla integração com o SDK da OpenAI
OCPP (WebSocket) | Leitura de dados da sessão em tempo real | Protocolo aberto padrão para comunicação entre eletroposto e sistema de gestão, já adotado no projeto do ChargeGrid Intelligence
PostgreSQL | Armazenamento de histórico de sessões e logs | Confiabilidade, suporte a queries complexas e integração nativa com o stack Python
React (frontend) | Interface do totem e do aplicativo mobile | Componentização, responsividade e facilidade de atualização para diferentes telas

- Justificativa Técnica -

O GPT-4 foi escolhido pela sua superioridade na compreensão de linguagem natural em português, capacidade de seguir system prompts detalhados com alto grau de fidelidade e qualidade de resposta consistente. Comparado a modelos open source como o Meta LLaMA, o GPT-4 via API elimina a necessidade de infraestrutura própria de GPU — reduzindo o custo inicial de operação e acelerando o desenvolvimento, o que é especialmente viável para o escopo do EV Challenge 2026. A escolha pelo FastAPI garante que o backend seja leve o suficiente para rodar próximo ao eletroposto sem exigir servidores de alto custo, e a integração com OCPP permite que o chatbot acesse dados reais da sessão em tempo real, tornando-o uma ferramenta operacional genuína.

- Fluxograma -

O fluxograma do funcionamento do chatbot está disponível no repositório.

- Resumo da lógica do fluxo: -

1. O usuário envia uma mensagem via totem touchscreen ou aplicativo mobile
2. A mensagem passa por pré-processamento (normalização e limpeza do texto)
3. O contexto é injetado no modelo: system prompt base + dados reais da sessão via OCPP
4. A OpenAI API (GPT-4) processa a mensagem contextualizada e gera uma resposta
5. O sistema verifica a natureza do problema:
   - Não é físico/técnico: a resposta é exibida diretamente ao usuário no totem ou app
   - É físico/técnico: o sistema escala automaticamente para a equipe de suporte técnico presencial

- Modelo de Teste -

O modelo de teste com perguntas esperadas e respostas ideais está disponível no repositório.

- System Prompt -

O contexto-base utilizado para condicionar o modelo GPT-4 está disponível no repositório.

- Referências -

- GoodWe: https://en.goodwe.com
- OCPP — Open Charge Point Protocol: https://www.openchargealliance.org
- MODBUS: https://modbus.org
- OpenAI API: https://platform.openai.com/docs
- FIAP EV Challenge 2026: https://www.fiap.com.br
