**POLÍTICA DE SEGURANÇA**

**Diretrizes de segurança e reporte de vulnerabilidades**

**1**. A segurança da informação é um pilar fundamental para a comunidade Galera do TI. Como um projeto de código aberto voltado para o aprendizado e colaboração, buscamos manter um ambiente seguro para todos os nossos usuários e contribuidores.
Este documento estabelece as diretrizes para a identificação, reporte e correção de vulnerabilidades em nossa aplicação web, construída em TypeScript com arquitetura Serverless (AWS Lambda).

**2. Dados sensíveis protegidos**

Nossa aplicação processa informações que exigem níveis rigorosos de proteção. O foco das nossas medidas de segurança recai sobre:

***Credenciais de autenticação:** Senhas (hasheadas), tokens de sessão (JWT) e chaves de API.

***Dados pessoais (PII):** Nomes, endereços de e-mail e informações de perfil social dos usuários.

***Segredos de infraestrutura:** Variáveis de ambiente, chaves de acesso à AWS e segredos de banco de dados.

**Metadados de sessão:** Informações que possam permitir o sequestro de sessão ou personificação de usuários.

**3. Como reportar vulnerabilidades**
Se você identificar uma falha de segurança, pedimos que reporte o problema através do sistema de GitHub Issues do repositório oficial. Para garantir a eficiência do processo, siga estas etapas:

1. Abra uma nova "Issue" no repositório.
2. Utilize o marcador (label) "security" ou "bug".
3. No título, seja conciso (ex: "Falha de validação no endpoint de perfil").
4. No corpo da issue, descreva o impacto potencial da vulnerabilidade.
5. Forneça um passo a passo simplificado para reproduzir o problema.

**Atenção:** Ao reportar via GitHub Issues (público), foque na descrição da falha e **NUNCA** envie dados de usuários


**4. Política de divulgação responsável**

Adotamos o princípio da divulgação responsável para proteger a comunidade enquanto as correções são desenvolvidas. Solicitamos que os pesquisadores e contribuidores:

1. Deem tempo razoável à equipe de mantenedores para analisar e corrigir a falha antes de compartilhar detalhes publicamente.
2. Não utilizem a vulnerabilidade para acessar, modificar ou deletar dados de terceiros.
3. Não realizem ataques de negação de serviço (DoS) ou engenharia social contra os membros da comunidade.

**5. Escopo de segurança**

Código Fonte (Frontend/Backend) Comunidade Galera do TI
Lógica de Autenticação e JWT  Comunidade Galera do TI
Sanitização de Entradas (API) Comunidade Galera do TI
Infraestrutura AWS (Lambda/Gateway) fora de Escopo (aws)
GitHub fora de escopo.

**6. Checklist de Segurança para contribuidores (PRs)**

Antes de submeter um Pull Request, verifique se o seu código atende aos seguintes requisitos básicos de segurança:
Sem Segredos: Verifique se não há senhas, tokens ou chaves de API escritas diretamente no código (hardcoded).
Validação de Tipos: Utilize as interfaces do TypeScript para garantir que os dados recebidos possuem o formato esperado.
Sanitização: Certifique-se de que entradas de usuários sejam tratadas para evitar ataques de Cross-Site Scripting (XSS) e Injeção.
Dependências: Verifique se as novas bibliotecas adicionadas não possuem vulnerabilidades conhecidas.
Princípio do Menor Privilégio: Garanta que as funções Lambda tenham apenas as permissões necessárias para executar sua tarefa.

**7. Ferramentas e processos para auxiliar na manutenção da segurança do projeto:**

npm audit: Executado em cada build para identificar dependências com vulnerabilidades conhecidas.

ESLint (Security Plugin): Análise estática de código para detectar padrões perigosos em TypeScript.

GitHub Dependabot: Alertas automáticos e atualizações de segurança para pacotes desatualizados.

SAST (Static Application Security Testing): Integração contínua que analisa o fluxo de dados em busca de falhas lógicas.

