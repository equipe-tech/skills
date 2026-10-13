# Como contribuir

Obrigado por contribuir com as Skills da Equipe Tech!

## Preparação

- Tenha Git, Node.js e npm (com `npx`) disponíveis.
- Para testar skills que interagem com PRs, instale o GitHub CLI (`gh`) e autentique-se com `gh auth login` em uma conta com acesso ao repositório de teste.
- Abra uma [issue](https://github.com/equipe-tech/skills/issues) para relatar problemas ou discutir mudanças maiores. Inclua comportamento esperado, passos de reprodução e logs relevantes, sem tokens ou informações confidenciais.

## Fluxo de trabalho

1. Faça um fork do repositório, caso não tenha permissão de escrita, e clone sua cópia.
2. Crie uma branch de trabalho a partir de `master`, por exemplo: `git switch -c feat/minha-skill master`. Mantenha a alteração focada em um único objetivo.
3. Altere ou adicione a skill e atualize a lista e os exemplos no [README.md](README.md) quando necessário.
4. Execute as validações abaixo e revise o diff com `git diff --check` e `git diff`.
5. Faça commit com uma mensagem descritiva, como `feat: add example skill` ou `fix: correct CI failure diagnosis`, e publique sua branch.
6. Abra um pull request contra `master`, explicando o problema, a solução, como validou e eventuais riscos. Aguarde a revisão e responda aos comentários; não envie alterações diretamente para `master`.

## Estrutura das skills

Cada skill fica em uma pasta na raiz, contendo um `SKILL.md` com frontmatter YAML:

```text
minha-skill/
└── SKILL.md
```

```yaml
---
name: minha-skill
description: Descreve o objetivo da skill e quando o agente deve utilizá-la.
---
```

- Use nomes curtos em kebab-case; o campo `name` deve coincidir com o nome da pasta e é utilizado por `--skill`.
- Escreva instruções claras, acionáveis e com comandos reproduzíveis. Inclua condições de uso, limites de atuação e resultado esperado.
- Documente ferramentas, autenticação e permissões necessárias. Nunca inclua credenciais, dados privados ou comandos destrutivos sem avisos e condições explícitas.
- Preserve o idioma e o estilo dos arquivos existentes: documentação geral em português e instruções das skills existentes em inglês.
- Ao alterar uma skill, mantenha as referências e exemplos de instalação consistentes.

## Validação

Confirme a descoberta das skills na cópia local:

```bash
npx skills add . --list
```

Verifique se a skill alterada aparece com o nome e a descrição corretos. Teste as instruções em um projeto ou PR de teste adequado e descreva os resultados no pull request. Não use um repositório de produção para testar ações que alteram arquivos ou publicam commits.

Atualmente não há suíte automatizada nem workflow de CI neste repositório. Não declare um teste como aprovado se ele não foi executado; registre limitações e etapas que dependem de autenticação ou serviços externos.

## Configuração do GitHub

O arquivo [.github/settings.yml](.github/settings.yml) descreve metadados, labels e proteção de `master`. A aplicação automática depende da instalação e das permissões do GitHub App [Repository Settings](https://github.com/apps/settings); o arquivo sozinho não altera as configurações do GitHub. As mudanças são sincronizadas após chegarem à branch padrão.

Ao modificar esse arquivo, valide o YAML e evite exigir checks inexistentes, pois isso pode impedir o merge de pull requests.

## Licença

Ao enviar uma contribuição, você concorda que ela seja distribuída sob a [licença MIT](LICENSE) deste projeto. Inclua apenas conteúdo próprio ou compatível com essa licença e preserve os avisos de terceiros quando aplicável.
