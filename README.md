# Tutorial Prático: Refatorando Sistemas Legados com Agentes de IA

Este guia é um tutorial passo a passo para desenvolvedores que desejam aprender a utilizar **Agentes de IA (Antigravity/Gemini CLI)** para modernizar sistemas legados de ponta a ponta — do código à nuvem.

Vamos usar como exemplo prático a refatoração de "Pacific Northwest X-Ray Inc.", um site de raio-X dos anos 90 (`<table>`, `<font>`, `<center>`, GIFs), transformando-o em um site responsivo de padrão "Premium", com infraestrutura Docker/Nginx, revisão de código automatizada e deploy em Cloud Run — tudo isso orquestrado via chat com a IA. O roteiro completo, com os prompts exatos usados na apresentação ao vivo, está em [`DEMO_GUIDE.md`](./DEMO_GUIDE.md); este documento explica o *porquê* de cada etapa.

---

## Passo 1: O Segredo do Sucesso (Preparando o Contexto)

A diferença entre a IA gerar um "código genérico" e um "código excepcional" está no contexto que você fornece a ela. Antes de iniciar o chat, crie regras claras num arquivo `GEMINI.md` na raiz do projeto e configure agentes/skills especializados em `.gemini/`.

**Exemplo do que passamos para o Agente neste projeto:**
- **Regra de Ouro (Aesthetics First):** *O design final tem que causar um efeito WOW. Proibido usar cores primárias secas, use paletas modernas (HSL). Use Google Fonts, glassmorphism e sombras elegantes.* (`.gemini/skills/modern-design-specialist/SKILL.md`)
- **Arquitetura Front:** *HTML5 semântico rigoroso. Proibido o uso de `<table>` para layout ou tags como `<font>` e `<center>`.* (`.gemini/skills/modern-html-specialist/SKILL.md`)
- **Agentes dedicados por responsabilidade:** `frontend_developer` (HTML semântico), `frontend_designer` (CSS, não toca HTML) e `devops_engineer` (Docker/Nginx) — cada um com seu próprio `AGENT.md` em `.gemini/agents/`.

> **Dica Pro:** Trate o agente de IA como um Desenvolvedor Sênior recém-contratado. Quanto mais clara a diretriz da empresa, melhor o resultado — e quanto mais especializados os agentes/skills, menos genérica a saída.

---

## Passo 2: O Mega-Prompt (Mapeamento + Refatoração + Infraestrutura)

Em vez de pedir as coisas fragmentadas ("faça o css", depois "faça o docker"), você pode e deve agrupar tarefas relacionadas num mesmo prompt para economizar tempo. Como o contexto (passo 1) já tem as regras de design e de HTML, basta focar no "o quê" precisa ser feito. Esta etapa é conduzida em 3 ações, nesta ordem: abrir o Planning Mode explicitamente, enviar o mega-prompt com o objetivo e revisar/aprovar o plano via `/artifact`.

💬 **Prompt 1 — entrar em Planning Mode:**
> *"/planning"*

💬 **Prompt 2 — mega-prompt (objetivo):**
> *"refatore o projeto aplicando as diretrizes de design do GEMINI.md e logo em seguida já crie a infraestrutura DevOps para subir isso num container docker (usando nginx)"*

💬 **Prompt 3 — revisar o plano gerado:**
> *"/artifact"*

🤖 **Como a IA vai agir:**
1. Com `/planning`, entra explicitamente em **Planning Mode** antes de qualquer ação no código.
2. Recebe o objetivo (mega-prompt) e mapeia o contexto (`/init` implícito): varre o diretório, indexa o `index.html` legado e localiza o `GEMINI.md`.
3. Cria um plano detalhado com a proposta técnica para ambas as frentes.
4. Com `/artifact`, exibe o plano/diff gerado; a UI oferece **Open / Approve / Decline** — clique em **Approve**.
5. Após o Approve, programa as duas frentes sozinha:
   - **Frontend:** Cria o arquivo `style.css`, usa `CSS Grid`/`Flexbox`, responsividade, cores curadas (HSL) e animações de hover.
   - **Infraestrutura:** Gera o `Dockerfile` (usando `nginx:alpine`), `.dockerignore` e `docker-compose.yml` com template Nginx pronto para ler a variável `$PORT` (compatível com Cloud Run).

---

## Passo 3: Rodar Localmente & Validar

Agentes de desenvolvimento avançados não só cospem texto, eles interagem com a máquina via terminal. Vamos pedir para a IA subir o nosso container recém-criado e já abrir o resultado.

💬 **Prompt que você deve usar:**
> *"suba para teste e abra o chrome"*

🤖 **Como a IA vai agir:**
1. Abre um shell em _background_ e executa `docker-compose up -d --build`.
2. Lê o log para garantir que o container não deu erro.
3. Usa comandos do sistema operacional (ex.: `open -a "Google Chrome" http://localhost:8080` no Mac) para abrir o navegador literalmente na sua tela com o projeto rodando, causando o efeito "WOW".

---

## Passo 4: Iteração e Ajustes Finos (Live Tweaking)

A vantagem de trabalhar com um servidor local já no ar é poder pedir ajustes visuais pontuais e ver o resultado quase em tempo real, sem reabrir todo o fluxo de refatoração.

💬 **Prompt que você deve usar:**
> *"mude o gradiente de fundo da página de azul escuro para um tema dark violeta clínico, e mude o efeito de hover dos cards para acender com uma borda neon roxa"*

🤖 **Como a IA vai agir:**
1. Edita o `style.css` de forma precisa, alterando apenas as variáveis de cor e o comportamento das transições — sem tocar no HTML.
2. Mantém o servidor local rodando para você atualizar o Chrome (F5) e mostrar a alteração instantaneamente.

---

## Passo 5: Swarm de Design — Delegação para um Subagente Especialista

Esta etapa não é "o CLI chamando uma ferramenta de imagem" como um chat comum conectado a um gerador externo — é orquestração multi-agente. O agente principal percebe que a tarefa exige uma competência fora do seu forte (codificação) e delega, de forma invisível e paralela, para um subagente especialista em design.

💬 **Prompt que você deve usar:**
> *"substitua a imagem de fundo skyimge.jpg por uma imagem médica abstrata e moderna gerada por você, e os botões ButtonSkull.jpg por ícones modernos de raio-X de tórax"*

🤖 **Como a IA vai agir:**
1. Identifica que a tarefa exige design gráfico e delega para um **subagente especialista em imagem**, rodando em paralelo ao fluxo principal.
2. O subagente invoca a ferramenta de geração de imagem com prompts especializados no contexto clínico de radiologia, validando tamanho e formato dos arquivos.
3. Devolve os assets prontos ao agente principal, que os salva no repositório sobrescrevendo os arquivos legados (`skyimge.jpg`, `ButtonSkull.jpg`).
4. Atualiza o layout se necessário — basta atualizar o Chrome local para ver as novas imagens aplicadas.

> **Dica Pro:** Destaque para o público que o agente certo (design) foi escolhido para a tarefa certa — isso é o conceito de Swarm Multi-Agente na prática, não apenas "um chat com mais um botão".

---

## Passo 6: Code Review Automático — A Fricção Controlada

Code review por IA não deve ser um carimbo de aprovação automático. O valor real aparece quando o agente encontra algo concreto — neste projeto, o formulário de busca legado (`/Search/`) costuma ficar sem tratamento de erro depois da refatoração.

💬 **Prompt que você deve usar:**
> *"faça um code review detalhado do novo index.html e do style.css usando a sua skill de code-review-specialist"*

🤖 **Como a IA vai agir:**
1. Ativa e segue estritamente a skill **Code Review Specialist** (`.gemini/skills/code-review-specialist/SKILL.md`).
2. Analisa o código sob as lentes de corretude, segurança, performance, acessibilidade e boas práticas, usando os níveis oficiais de severidade: `🔴 [blocking]`, `🟡 [important]`, `🟢 [nit]`, `💡 [suggestion]`, `🎉 [praise]`.
3. Propõe a correção diretamente no terminal; você revisa e aprova com `Y`.
4. Só depois da correção aplicada, devolve o relatório completo de revisão.

> **Dica Pro:** Esse momento de fricção é o que prova o valor da skill — não é decoração, é governança encontrando um problema real antes da nuvem.

---

## Passo 7: Deploy Automático no Google Cloud Run

Com o código revisado e aprovado, peça o deploy contínuo em serverless.

⚠️ **Pré-requisito:** Execute o Passo 6 (Code Review) antes desta etapa, para garantir que só código validado vá para a nuvem.

💬 **Prompt que você deve usar:**
> *"faça o deploy disso no cloud run"*

🤖 **Como a IA vai agir:**
1. Identifica o projeto ativo do GCP.
2. Ajusta as portas dinâmicas usando o template Nginx configurado para ler a variável `$PORT` do Cloud Run.
3. Executa o build no Cloud Build e faz o deploy, entregando uma URL pública funcional e segura (HTTPS).

---

## Passo 8: Teardown (Desmontando o ambiente)

Ao finalizar a validação, use a IA para limpar a sujeira e manter seu ambiente — local e na nuvem — organizado.

💬 **Prompt que você deve usar:**
> *"pare os containers de teste, limpe os recursos locais e delete o serviço criado no cloud run"*

🤖 **Como a IA vai agir:**
1. Remove os containers locais de teste (`docker-compose down`).
2. Exclui o serviço ativo no Cloud Run para evitar cobranças na nuvem.
3. Reporta que a porta 8080 foi liberada e a network de teste removida com segurança.

Para repetir a demo do zero (voltar ao `index.html` original de 1997), rode no terminal:
```
git stash && git stash drop && rm -f Dockerfile .dockerignore docker-compose.yml style.css default.conf.template
```

---

## 🎯 Conclusão

Trabalhar com **Agentic AI Coding** muda a dinâmica de escrever linha a linha para atuar como um Arquiteto de Software que orquestra um time de agentes. O ciclo completo demonstrado aqui é:
1. Definir o padrão de qualidade (Contexto, Agentes e Skills).
2. Delegar o problema via um mega-prompt claro (refatoração + infraestrutura).
3. Revisar o plano (Planning Mode) e validar as execuções (código, comandos, browser).
4. Iterar com ajustes finos em tempo real.
5. Confiar em delegação multi-agente (Swarm) para competências fora do core do agente principal, como design gráfico.
6. Exigir governança real via skills especializadas (Code Review) antes de qualquer deploy.
7. Publicar com deploy automatizado em nuvem.
8. Encerrar com teardown disciplinado, local e remoto.

Experimente aplicar essa estrutura nos seus próximos sistemas legados!
