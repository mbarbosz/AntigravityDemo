---
name: modern-design-specialist
description: Skill especialista em aplicar diretrizes de design moderno, UI/UX premium, animações e responsividade.
---

# Especialista em Design Moderno

Sempre que atuar utilizando esta skill, siga as regras abaixo:

1. **Aesthetics First (O Efeito "WOW")**: Seu objetivo primário é encantar o usuário final. O design nunca pode parecer amador, cru ou como um "Produto Mínimo Viável" (MVP) básico. Ele deve transmitir profissionalismo e ser "state-of-the-art".
2. **Cores e Temas**: 
   - Evite cores primárias brutas (vermelho puro, azul puro).
   - Use paletas de cores curadas (ex: usando HSL ou paletas modernas tipo Tailwind/Material como referência).
   - Utilize gradientes suaves para fundos e botões.
   - Sempre que possível, considere um visual limpo (Clean UI) ou um Dark Mode sofisticado.
3. **Tipografia**: 
   - Nunca confie nas fontes padrão do navegador (Times New Roman, Arial padrão sem fallback adequado).
   - Importe fontes modernas do Google Fonts, como 'Inter', 'Outfit', 'Poppins' ou 'Roboto'.
   - Ajuste o espaçamento de linhas (`line-height`) e kerning (`letter-spacing`) para máxima legibilidade.
4. **Layout Avançado**: 
   - Use CSS Grid e Flexbox para todos os layouts.
   - Elimine layouts baseados em tabelas (`<table>` usado para estrutura) ou `float` clássicos.
   - Tudo deve ser 100% responsivo (Mobile-First approach).
5. **Micro-interações e Animações**: 
   - Elementos interativos não devem ser estáticos. Use `transition: all 0.3s ease;` para mudanças de estado (hover, focus, active).
   - Efeitos de escala sutil (`transform: translateY(-2px)`) e mudança de sombras ao passar o mouse criam uma interface "viva".
6. **Sombras, Bordas e Profundidade**: 
   - Evite bordas pretas secas.
   - Use `box-shadow` modernos, com alta dispersão (blur) e baixa opacidade (ex: `rgba(0,0,0,0.05)`).
   - Considere efeitos de Glassmorphism (`backdrop-filter: blur(10px)`) para cabeçalhos fixos ou modais, se agregar ao design.
