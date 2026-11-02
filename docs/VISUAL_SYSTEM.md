# Sistema visual das interfaces Aetherius

## Referência principal

O **Sistema de Classes é a referência visual para os workspaces e módulos de interface do Aetherius**. Ao criar ou revisar uma tela, use como referência a seleção de classes e a página de detalhes implementadas em [`aetherius-client/client/ui-core/modules/class/class-module.css`](https://github.com/AetheriusRP/aetherius-client/blob/main/client/ui-core/modules/class/class-module.css) e [`class-module.js`](https://github.com/AetheriusRP/aetherius-client/blob/main/client/ui-core/modules/class/class-module.js). Os estilos também estão na origem do módulo em `AetheriusGameplayCore/modules/class-system/ui/class-module.css`. Confira o código da versão em uso antes de extrair novos componentes: os valores abaixo registram o visual atual, e o módulo de Classes é a referência em caso de divergência.

Esta diretriz define o visual **alvo** para novas interfaces e para a evolução das existentes. Ela não afirma que todas as telas atuais do UI Core já foram convertidas. O menu radial, HUD e criação de personagem têm funções próprias; as regras específicas deles aparecem ao final.

## Linguagem visual

- **Atmosfera:** painel escuro translúcido sobre o mundo do jogo, com pouca obstrução fora do workspace. Superfícies internas quase transparentes, profundidade discreta e separadores finos. Evite transformar cada seção em um bloco preto sólido.
- **Hierarquia:** título serifado amplo, subtítulo ou lema, ornamento fino e conteúdo dividido em capítulos. Kicker em caixa alta e com espaçamento entre letras marca contexto; o texto de leitura fica em sans serif.
- **Iconografia:** emblemas e ilustrações vetoriais de aparência heráldica, em tons neutros e com traços finos. Medalhões geométricos, pequenos losangos e linhas ornamentais dão identidade às áreas de destaque. Ícones de domínio comunicam o assunto da tela; não repita os brasões de classes em domínios sem relação com elas.
- **Cor de ação:** verde apenas para seleção, foco, progresso e ação principal. Texto comum, molduras e ilustrações permanecem em branco ou cinza neutro para que o estado ativo seja fácil de localizar.
- **Controles:** botões e cartões de cantos quase retos, borda clara de baixa opacidade e preenchimento sutil. A seleção combina borda e fundo verdes discretos com texto ou marcador verde. Hover altera suavemente fundo e borda; foco de teclado usa contorno verde visível.

## Tokens de referência

Os valores abaixo vêm do módulo de Classes. Use tokens equivalentes no escopo do novo módulo, preservando a distinção entre conteúdo neutro e destaque.

| Uso | Valor de referência |
| --- | --- |
| Painel do workspace | `rgba(0, 0, 0, .73)`, sem borda externa |
| Sombra do painel | `0 22px 60px rgba(0, 0, 0, .32)` |
| Atenuação do mundo na tela de Classes | `rgba(0, 0, 0, .12)` |
| Texto principal | `#f0f1f1` |
| Texto secundário | `#d4d8db` |
| Texto discreto | `#b7bec2` |
| Separador | `#ffffff1c` |
| Verde de estado ativo | `#69cf99` |
| Verde de ação e progresso | `#4fc787` |

O corpo do módulo de Classes usa `Segoe UI, sans-serif`, 16 px, com espaçamento leve entre letras; títulos, nomes de cartões e números de destaque usam `Georgia, serif`. Os títulos principais variam com o viewport (`clamp(...)`), enquanto rótulos e metadados costumam ficar em 12–14 px. Parágrafos têm altura de linha confortável, em torno de `1.7`. A escala base de espaçamento do shell é 4 px; no workspace, ajuste espaços e colunas à densidade do conteúdo seguindo as proporções de Classes.

## Composição de telas

1. **Entrada ou catálogo:** apresente contexto e título centralizados, um ornamento discreto e grupos claros de opções. Em Classes, três arquétipos organizam seis escolhas cada; em outro domínio, agrupe pelo conteúdo real sem forçar essa contagem. Cada escolha traz ilustração, nome, explicação curta e estado selecionado legível.
2. **Página de detalhes:** use um cabeçalho com emblema ou ilustração do domínio, título serifado, resumo curto e, quando útil, um indicador de estado. Em seguida, organize fatos em faixas com divisórias finas e seções de leitura com hierarquia clara.
3. **Navegação interna e progressão:** use abas de texto sobre uma linha sutil; o item ativo recebe verde e um pequeno marcador geométrico. Para marcos sequenciais, a trilha de Classes usa nós e linha fina. Exponha o estado também por texto e sem depender apenas da cor.
4. **Listas e ações:** prefira linhas ou cartões leves, com separadores discretos, ícones consistentes e uma ação principal identificável. Reserve confirmações para mudanças com consequência; estados bloqueados ou indisponíveis precisam de texto explicativo.

O catálogo de Classes usa três colunas largas, reduz elementos em viewports baixos e passa a uma coluna de arquétipos em telas estreitas (`max-width: 700px`). Detalhes, atributos e grimório também se reorganizam em uma coluna nessa faixa. Adapte cada módulo para evitar cortes, rolagem horizontal involuntária e texto comprimido. Preserve o foco visível e a navegação por teclado; `aria-pressed` identifica escolhas e abas no módulo de referência. Respeite `prefers-reduced-motion` nas transições dos componentes.

## Áreas com comportamento próprio

- **Menu radial:** mantém o mundo visível ao fundo. Os círculos usam preto translúcido, sem borda, nomes `#69cf99` e ícones cinza; sua geometria e animação de abertura/retorno seguem a implementação do shell. O radial é navegação, não um workspace de conteúdo.
- **HUD:** permanece uma projeção passiva e segue as restrições de legibilidade e integração descritas em [`HUD_ASSETS.md`](HUD_ASSETS.md).
- **Criação de personagem:** segue sua documentação e fluxo próprios em [`CHARACTER_CREATION.md`](CHARACTER_CREATION.md). Ao harmonizar suas superfícies com o restante da UI, use Classes como referência de cor, tipografia, iconografia e hierarquia.
- **Launcher e legado do shell:** `launcher-theme.css` registra verde profundo `#1d3e2d`, linhas `#2a5a40` e títulos creme `#fffaf0`; o shell atual usa Futura local em partes da navegação. Esses estilos existentes não definem a aparência dos novos workspaces. A fonte local é `frontend/Data/MeridianUI/aetheriusui/fonts/futura-book-bt.ttf` e exige os direitos de uso indicados no README.

## Assets e procedência

Os SVGs de Classes ficam em `aetherius-client/client/ui-core/modules/class/assets/` e na origem do módulo no GameplayCore. `frontend/Data/MeridianUI/aetheriusui/icons/` contém os SVGs atuais do UI Core; `brand/server-logo.png` é a marca fornecida pelo proprietário. `frontend/test-fixtures/ScreenShot112.png` é uma captura de demonstração fora dos assets instalados. Não incorpore imagens dos PDFs de referência nem de outras interfaces sem autorização de uso. Consulte [`HUD_ASSETS.md`](HUD_ASSETS.md) para a procedência dos assets do HUD.
