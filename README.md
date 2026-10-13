# Skills da Equipe Tech

Skills para agentes de programação, instaláveis com o CLI [skills](https://github.com/vercel-labs/skills).

## Instalação

Requer Node.js e npm (com `npx`) disponíveis no ambiente.

Instale `fix-ci` no projeto atual:

```bash
npx skills add https://github.com/equipe-tech/skills --skill fix-ci
```

Instale `ci-watcher`:

```bash
npx skills add https://github.com/equipe-tech/skills --skill ci-watcher
```

Liste as skills disponíveis sem instalar:

```bash
npx skills add https://github.com/equipe-tech/skills --list
```

Para instalação global, adicione `--global`. Para escolher um agente e evitar perguntas interativas, use, por exemplo, `--agent claude-code --yes`.

## Skills disponíveis

| Skill | Descrição |
| --- | --- |
| [fix-ci](fix-ci/SKILL.md) | Diagnostica falhas de CI de um PR e aplica correções focadas até os checks passarem. |
| [ci-watcher](ci-watcher/SKILL.md) | Monitora os checks de CI de um PR e reporta resultados e links de falhas. |

Essas skills usam Git e o GitHub CLI (`gh`), autenticado e com acesso ao repositório do PR. `fix-ci` também precisa das ferramentas utilizadas nos checks para reproduzir falhas localmente.

## Estrutura e publicação

Mantenha uma pasta por skill na raiz do repositório, contendo um `SKILL.md` com frontmatter YAML e os campos `name` e `description`. O valor de `name` é o identificador usado em `--skill`.

```text
fix-ci/SKILL.md
ci-watcher/SKILL.md
```

Não é necessário publicar um pacote npm: `npx skills` executa o instalador, que busca as skills diretamente no repositório Git. Para os comandos acima funcionarem, publique estes arquivos no repositório `https://github.com/equipe-tech/skills`. Se ele for privado, quem instalar precisa ter autenticação Git com acesso.

Para conferir a descoberta a partir de uma cópia local:

```bash
npx skills add . --list
```
