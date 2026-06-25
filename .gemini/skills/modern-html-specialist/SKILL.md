---
name: modern-html-specialist
description: Skill especialista em escrever HTML5 semântico, acessível e otimizado para SEO e performance.
---

# Especialista em HTML Moderno

Sempre que atuar utilizando esta skill para refatorar ou criar código, siga as regras abaixo:

1. **Semântica HTML5 Estrita**: 
   - Utilize a estrutura semântica correta: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, e `<footer>`.
   - NUNCA use a tag `<table>` para fins de layout estrutural da página. Tabelas são exclusivas para dados tabulares.
2. **Remoção de Tags Obsoletas (Depreciadas)**: 
   - Elimine completamente o uso de tags legadas como `<center>`, `<font>`, `<b>`, `<i>`, `<marquee>`.
   - Elimine atributos inline de estilo no HTML como `bgcolor`, `text`, `link`, `vlink`, `alink`, `border`, `cellspacing`, `cellpadding`.
   - Substitua todo comportamento visual dessas tags por classes e regras no arquivo CSS.
3. **Acessibilidade (a11y - Web Content Accessibility Guidelines)**:
   - Adicione atributos `alt` text descritivos em todas as tags `<img>`. Para imagens puramente decorativas, use `alt=""`.
   - Garanta que elementos interativos sejam acessíveis via teclado. Use as tags nativas `<button>` ou `<a>` para ações, e não `<div>` ou `<span>` com handlers de click (se precisar usar, implemente `tabindex="0"` e role via ARIA).
   - Mantenha uma hierarquia lógica e sequencial de headings (`<h1>` principal da página, seguido de `<h2>`, `<h3>`).
4. **Boas Práticas de SEO e Head**: 
   - Inclua sempre a tag `<meta charset="UTF-8">`.
   - Inclua sempre a tag viewport responsiva: `<meta name="viewport" content="width=device-width, initial-scale=1.0">`.
   - Configure title tags apropriadas e descrições otimizadas `<meta name="description" content="...">`.
5. **Carregamento e Imagens Modernas**: 
   - Sempre que possível referenciar imagens, considere o uso de formatos modernos (como webp/svg) se disponíveis.
   - Adicione `loading="lazy"` em todas as imagens que estão "below the fold" (fora da tela inicial de rolagem) para melhorar a performance.
