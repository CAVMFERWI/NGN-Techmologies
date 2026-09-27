# NGN Technologies — Frontend

Camada web (login/cadastro, jogo e ranking) do projeto NGN Technologies. O jogo em si (Godot Engine/GDScript) entra como export HTML5 dentro da `div.jogo-embed` em `index.html` — veja o comentário no código.

## Como rodar

Abra `index.html` direto no navegador, ou publique a pasta no GitHub Pages / Vercel / Netlify (sem build, é HTML/CSS/JS puro).

## Checklist dos 5 critérios de avaliação

| Critério | Atende? | Por quê |
| --- | --- | --- |
| 1. Deploy e Funcionamento | ✅ | Site estático (sem build), pronto para GitHub Pages/Vercel/Netlify. Ao adicionar o export do Godot, manter os caminhos relativos dos arquivos `.wasm`/`.pck`. |
| 2. Interatividade sem Recarregamento | ✅ | O formulário de login/cadastro usa `e.preventDefault()` (`script.js`); navegação entre telas (Jogo/Ranking) troca `classList`, sem `<a href>` nem reload. |
| 3. Persistência de Dados | ✅ | Jogadores e sessão atual ficam em `localStorage` (`ngn_players`, `ngn_current_user`). Ao dar F5, a sessão é restaurada automaticamente. |
| 4. Estabilidade do Console | ✅ | Todo `JSON.parse` de `localStorage` está em `try/catch`; nenhuma chamada depende de elementos que possam não existir. Testar console (F12) depois de plugar o export do Godot, que costuma gerar warnings próprios. |
| 5. Adaptabilidade e Responsividade | ✅ | Media query em `styles.css` empilha a navegação e a tabela de ranking em telas pequenas, sem scroll horizontal. Uso de `aria-label`, `role="status"`, `<caption>` e `scope` nas tabelas para leitor de tela. |

## Pendências para produção

- Trocar a `div.jogo-embed` pelo `<iframe>` ou canvas do export HTML5 do Godot.
- `localStorage` cobre o critério de persistência do protótipo; para ranking real entre escolas, sincronizar com Firebase (ver seção 5.9.4 do projeto de pesquisa), mantendo o `localStorage` como cache local.
