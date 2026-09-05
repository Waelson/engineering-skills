# Revisão de Autenticação e Autorização

Autenticação estabelece identidade; autorização decide se o subject pode executar uma action sobre um resource. Não trate uma como prova da outra.

Quando aplicável, identifique subject, resource, action, policy enforcement point, decision source, ownership, tenant boundary e bypass paths. Verifique lifecycle e validação de credentials/tokens, service identity, checks inconsistentes, indirect object reference, tenant escape, privilege escalation, operações administrativas e diferenças entre paths síncronos, assíncronos e workers.

“Internal” não torna uma boundary confiável. Exija contexto ou constraint que sustente confiança e considere identidade de serviço, origem forjada e movimento lateral.

Não presuma fail-open ou fail-closed. Se a indisponibilidade do policy service tiver semântica indefinida e afetar segurança, crie pergunta `BLOCKING`. Confirme controles no routing e path efetivo, não apenas na declaração arquitetural.
