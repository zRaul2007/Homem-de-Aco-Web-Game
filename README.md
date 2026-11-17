# Homem de Aço: Metrópole em Perigo 3D

Jogo 3D de ação em terceira pessoa com voo livre, feito em **um único arquivo HTML**, direto no navegador. Você é um super-herói voador que patrulha uma metrópole procedural, enfrenta ameaças, resgata civis e derrota chefes ao longo de 6 missões, mais um Modo Sobrevivência com ondas infinitas.

> **Projeto de fã, sem fins comerciais.** Veja a seção [Aviso legal](#aviso-legal) antes de publicar este repositório.

<!-- Adicione capturas de tela em docs/ e referencie aqui:
![Tela inicial](docs/titulo.png)
![Voo sobre a cidade](docs/voo.png)
-->

## Sumário

- [Como jogar](#como-jogar)
- [Controles](#controles)
- [Missões e vilões](#missões-e-vilões)
- [Mecânicas](#mecânicas)
- [Configurações e acessibilidade](#configurações-e-acessibilidade)
- [Detalhes técnicos](#detalhes-técnicos)
- [Como ajustar o jogo](#como-ajustar-o-jogo)
- [Problemas comuns](#problemas-comuns)
- [Aviso legal](#aviso-legal)
- [Ideias futuras](#ideias-futuras)
- [Créditos](#créditos)

## Como jogar

1. Baixe o arquivo `homem-de-aco-3d.html` (sugestão: renomeie para `index.html`).
2. Abra no navegador (Chrome, Edge, Firefox ou Safari recentes, com WebGL ativo).
3. É preciso **internet** na primeira abertura, porque o Three.js r128 é carregado pela CDN da Cloudflare.
4. Clique na tela inicial, escolha uma missão e **clique no jogo para travar o mouse**.

Não há instalação, build ou servidor. Para publicar no **GitHub Pages**, deixe o arquivo como `index.html` na raiz do repositório e ative Pages em *Settings > Pages*.

### Jogar offline

Baixe `three.min.js` na versão **r128** e troque a linha abaixo do arquivo HTML pelo caminho local:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
```

## Controles

Todas as teclas podem ser remapeadas em **Configurações > Remapear teclas**. Os valores abaixo são os padrões.

| Ação | Teclado e mouse |
|---|---|
| Direção | Mouse (com o ponteiro travado) ou setas |
| Acelerar / frear | `W` / `S` |
| Deslocamento lateral | `A` / `D` |
| Super velocidade | `Shift` (gasta energia) |
| Pairar | `C` |
| Visão de calor | `Q` ou botão esquerdo do mouse |
| Soco supersônico | `E` ou `Espaço` |
| Sopro congelante | `R` ou botão direito do mouse |
| Super sopro | `G` (a partir da missão 3 e no Modo Sobrevivência) |
| Pegar ou soltar civil | `F` |
| Travar alvo | `T` (repetir troca de alvo) |
| Câmera em primeira pessoa | `V` |
| Pausa | `P` ou `Esc` |
| Mudo | `M` |
| Reiniciar (na derrota ou resultado) | `R` |

**Celular e tablet:** joystick virtual à esquerda, arrastar à direita para a câmera e botões na tela para os poderes, com mira automática.

## Missões e vilões

| # | Missão | Ameaças |
|---|---|---|
| 1 | Centro de Dia | Drones e soldados de telhado. Tutorial integrado. |
| 2 | Porto ao Pôr do Sol | Helicópteros armados e mísseis teleguiados. Porto com água, navios e guindastes em chamas. |
| 3 | Tempestade sobre a Cidade | Caças a jato com passadas de ataque, raios com aviso e o chefe **Doomsday**. |
| 4 | Distrito Industrial Noturno | Zonas de kryptonita, torres laser e a Torre LexCorp. |
| 5 | Órbita da Terra | Meteoros, drones espaciais e o chefe **Lex Luthor** em armadura de batalha. |
| 6 | Invasão Alienígena | Sondas, torres laser e o chefe **Brainiac**, em sua nave. |
| ∞ | Modo Sobrevivência | Ondas infinitas, chefe a cada 5 ondas, ranking local. Libera ao concluir a missão 1. |

### Chefes

- **Doomsday:** anda pelas ruas da cidade. Ataca com soco, pisão com onda de choque e, abaixo de 50% de vida, com um salto que derruba prédios. Fica vulnerável por 4 s após o salto.
- **Lex Luthor:** 3 estágios. Tiros em leque e drones de apoio, depois escudo de energia (quebre refletindo as esferas roxas com o soco, ou espere o escudo se esgotar), e por fim um raio de satélite com aviso longo e chuva de meteoros.
- **Brainiac:** 3 estágios. Raio trator que puxa o herói, depois leques de espinhos e mísseis, e por fim 3 raios de dissolução, após os quais o núcleo fica exposto e recebe dano dobrado.

## Mecânicas

- **Voo com inércia**, colisão com prédios e chão, câmera com braço de mola que nunca atravessa construções e FOV dinâmico em alta velocidade.
- **Poderes:** visão de calor (mira assistida), soco supersônico (reflete tiros, quebra mísseis), sopro congelante, super sopro e passiva Pele de Aço.
- **Resgates:** aproxime-se de um civil em um prédio em chamas, pegue-o e leve ao feixe verde do heliporto. Capacidade de 1 a 3 civis com melhorias. Cada civil tem 90 s antes de ser perdido.
- **Itens:** cristais (moeda), Orbe Solar (+40 de energia), Kit de Reparo (+25 de vida), Escudo Dourado (5 s de invulnerabilidade) e Ímã de Cristais.
- **Combo** de x1 a x5, pontuação por bônus de tempo e de missão sem dano.
- **Estrelas por missão:** 1) concluir, 2) resgatar 80% ou mais dos civis, 3) terminar com 50% ou mais de vida ou sem usar Kit de Reparo.
- **Loja:** 6 melhorias em 5 níveis (vida, energia, regeneração, dano da visão de calor, recarga do soco, capacidade de civis).
- **Cidade viva:** trânsito, pedestres que fogem de explosões e comemoram resgates, helicópteros de imprensa, luzes de aviso nos prédios altos e fumaça nos incêndios.
- **Destruição:** bombas, mísseis e os ataques dos chefes danificam prédios, que escurecem e desabam parcialmente. Os prédios-símbolo resistem.
- **Manchetes:** ao fim de cada missão, uma capa do jornal da cidade resume seu desempenho. Os 5 melhores resultados de cada missão ficam salvos no navegador (`localStorage`).

## Configurações e acessibilidade

- Sensibilidade do mouse, volume de música e de efeitos separados.
- Qualidade **Baixa, Média ou Alta** (a Alta ativa sombras reais). Há qualidade adaptativa: se o FPS cair, a resolução é reduzida sozinha.
- Dificuldade **Normal, Difícil** (+30% de vida dos inimigos, -20% de regeneração) e **Lendário** (libera ao zerar o jogo, +25% de dano recebido e sem Kits de Reparo).
- **Modo Assistido:** oferecido após 3 derrotas seguidas na mesma missão (+25% de vida, -20% de dano recebido).
- Reduzir efeitos (sem tremor, flashes e relâmpagos), câmera estável e FOV fixo contra enjoo.
- Modo daltônico (formas no radar, números nas barras), alto contraste e legendas visuais para sons importantes.
- Escolha entre a trilha embutida e a música procedural.

## Detalhes técnicos

- **Tecnologia:** HTML5 + JavaScript puro + [Three.js](https://threejs.org) **r128** (build global `THREE`), sem módulos, bundler ou dependências além da CDN.
- **Tudo procedural:** a cidade (grade de quarteirões com semente fixa), os modelos (primitivas), as texturas (`CanvasTexture`) e os efeitos sonoros e a música alternativa (Web Audio API).
- **Desempenho:** prédios, carros, pedestres e luzes com `InstancedMesh`, *object pooling* para inimigos, projéteis e partículas, grade espacial para colisão, DPR limitado e qualidade adaptativa.
- **Áudio:** `AudioContext` iniciado após o primeiro clique. Trilha embutida em MP3 base64 com plano B (decodificação por `decodeAudioData`) e, se falhar, música procedural.
- **Persistência:** `localStorage`, sempre em `try/catch`.

### Organização do código

Um único script, dividido em seções comentadas, nesta ordem aproximada:

1. `CONFIG` e dados das missões (`MISSIONS`, lista declarativa de eventos)
2. Utilidades (vetores temporários, RNG com semente, colisão)
3. Renderer, céu e luzes
4. Geração procedural: cidade, porto, espaço, prédios-símbolo e vida na cidade
5. Herói (modelo montado por primitivas, capa animada)
6. Entrada (teclado, mouse com Pointer Lock, toque)
7. Áudio (efeitos, trilha, música procedural)
8. Partículas e entidades (inimigos, projéteis, civis, itens)
9. Chefes e sistemas (IA, colisão, câmera, destruição)
10. Interface (HUD, radar, menus, loja, configurações)
11. Máquina de estados e *game loop* (`requestAnimationFrame`, delta limitado a 50 ms)

## Como ajustar o jogo

Quase tudo fica no objeto `CONFIG`, no topo do script:

| Quero mudar | Onde |
|---|---|
| Velocidades de voo | `CONFIG.fly` (mínima 15, cruzeiro 45, máxima 70, super 130 m/s) |
| Dano, alcance e custo dos poderes | `heat`, `punch`, `frz`, `blow` |
| Vida e dano de inimigos | `drone`, `sol`, `heli`, `msl`, `jet`, `laser`, `meteor` |
| Chefes | `titan` (Doomsday), `vex` (Lex Luthor), `brain` (Brainiac) |
| Kryptonita | `kr` |
| Preços da loja | `shop` |
| Câmera e sensibilidade | `cam`, `sens` |
| Ondas, tempos e quantidades de uma missão | lista `events` dentro de `MISSIONS` |

Exemplo de evento: `{t:12, k:'civ', n:3, wait:1}` cria 3 civis aos 12 s, esperando o campo estar limpo.

## Problemas comuns

- **O mouse não trava:** clique na tela do jogo. Se o navegador recusar (por exemplo, após apertar `Esc` e clicar em "Continuar" muito rápido), o aviso "Clique na tela para travar o mouse" aparece e um novo clique resolve. Dentro de alguns visualizadores incorporados o travamento é bloqueado, então abra o arquivo direto no navegador. Sem travar, o cursor funciona como manche.
- **Sem som:** o áudio só inicia depois do primeiro clique. Confira o botão de mudo (`M`) e os volumes nas configurações.
- **Queda de FPS:** reduza a qualidade para Média ou Baixa e ative "Reduzir efeitos".
- **Tela preta:** confirme que o WebGL está ativo e que há internet para carregar o Three.js.

## Aviso legal

Este é um **projeto de fã, para uso pessoal e sem fins comerciais**, sem qualquer vínculo com a DC, a Warner Bros. ou seus licenciados.

Superman, Lex Luthor, Doomsday, Brainiac, Planeta Diário, LexCorp e o emblema do Superman são marcas e propriedades de seus respectivos donos. A **trilha sonora** usada na versão do autor (tema de John Williams e uma versão emotiva) e a **logo** também pertencem a terceiros.

**Antes de tornar este repositório público**, remova do arquivo HTML os três blocos abaixo. O jogo continua funcionando e passa a usar a música procedural e o emblema original (escudo dourado com raio vermelho):

```html
<script type="text/plain" id="mus0">...</script>
<script type="text/plain" id="mus1">...</script>
<script type="text/plain" id="logoimg">...</script>
```

Considere também trocar os nomes e personagens por criações originais caso o projeto vá além do uso pessoal.

## Ideias futuras

- Novos vilões e missões, como Metallo (coração de kryptonita) e Livewire (eletricidade).
- Modo desafio e manchetes do jornal entre as missões em quadrinhos.
- Mais habilidades do herói (pouso com onda de choque, voo rasante, visão de raios-X).
- Conquistas e modo foto.
- Colisão dos chefes e das arenas mais detalhada, com mais cenários.

## Créditos

- Código, design e ajustes: Raul Pedrogan de Moura, com apoio do Claude (Anthropic).
- [Three.js](https://threejs.org), licença MIT.
- Inspiração: jogos de voo livre, combate aéreo e super-heróis dos quadrinhos.

### Licença

A definir pelo autor. Se for abrir o código, uma licença permissiva como MIT para o **código** costuma bastar, mantendo fora dela os materiais de terceiros descritos acima.
