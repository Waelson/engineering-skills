# Revisão de Proteção de Dados

Descubra a classificação dos dados antes de concluir risco ou suficiência. Examine dados pessoais e sensíveis, secrets, exposição, transporte, persistência, retenção e encryption apenas quando relevantes. Não assuma que dados são públicos ou que encryption existe.

Procure secrets hardcoded, em arquivos locais, configuração, respostas e logs; considere source, storage, rotation e acesso. Tokens, credentials e conteúdo sensível em logs podem ser `SECRET_EXPOSURE` ou `DATA_EXPOSURE` conforme evidência e impacto.

Avalie auditabilidade proporcional: actor, resource, action, result, correlation e tamper resistance quando exigida. Logging excessivo também pode criar exposição; logging ausente pode impedir investigação. Não invente política de retenção ou mecanismo criptográfico.
