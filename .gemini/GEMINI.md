# Pacific Northwest X-Ray Inc. (PNWX) Modernization Project

## Objetivos
Reconstruir e modernizar o site legado `index.html` (atualmente com um visual estruturado em tabelas típico dos anos 90) para um padrão web de ponta, mantendo todo o conteúdo, estrutura de links de pesquisa/categorias e informações de contato.

## Stack Tecnológica
- **Estrutura:** HTML5 Semântico.
- **Estilização:** CSS3 Vanilla moderno (CSS Variables, Flexbox, CSS Grid). Sem frameworks pesados a não ser que estritamente necessário.
- **Interatividade:** JavaScript Vanilla (focado em interações, se necessário).

## Diretrizes de Design (Aesthetics)
- **Visual Premium ("WOW Effect"):** O design deve impressionar. Fuja de estilos genéricos e básicos.
- **Cores e Temas:** Paleta de cores harmoniosa focada no contexto clínico/radiológico (tons de azul moderno, cinza e branco limpo). Implemente suporte a Dark Mode ou um visual muito polido, com contrastes bem definidos e gradientes sutis.
- **Tipografia Moderna:** Uso de fontes sem serifa modernas (ex: Inter, Roboto, ou Outfit) via Google Fonts. Remoção completa de tags `<font>`.
- **Layout Responsivo (Mobile First):** O layout em tabela (`<table>` para estrutura) e as tags `<center>` devem ser totalmente substituídos por um Grid ou Flexbox moderno que se adapte perfeitamente a celulares, tablets e desktops.
- **Animações e Micro-interações:** A interface deve parecer "viva". Adicione efeitos de hover nos cards de categoria, transições suaves (`transition: all 0.3s ease`) e botões atrativos.
- **Sombras e Profundidade:** Use sombras sutis para destacar produtos e seções.

## SEO, Estrutura e Acessibilidade (a11y)
- Substituir tags obsoletas por HTML5 semântico (`<main>`, `<header>`, `<footer>`, `<section>`).
- Incluir as tags `meta` modernas (viewport, description).
- Garantir contrastes adequados e `alt` text em todas as imagens para leitores de tela.

## Instruções para a IA (Gemini)
- Leia e aplique rigorosamente as skills locais configuradas neste repositório (`modern-html-specialist` e `modern-design-specialist`).
- Qualquer alteração de UI deve ser testada e focar num resultado premium.
- Use a ferramenta `generate_image` caso precise de mockups ou assets modernos de imagens temporárias para substituir os gifs/jpgs antigos.
