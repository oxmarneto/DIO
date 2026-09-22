# DIO
# Miniguia de Estudos Interativo: Engenharia de Games 2.5D e 3D com NotebookLM

## Contexto e Objetivos
Este repositório documenta um projeto prático desenvolvido para a DIO (Treinando uma IA de Aprendizagem: Explore o Poder do NotebookLM) focado em aprendizagem ativa auxiliada por inteligência artificial. 

O tema central do caderno de estudos é o Desenvolvimento de Games 2.5D e 3D. O objetivo principal é consolidar as regras de arquitetura híbrida, engenharia de física e as transformações lineares de câmera necessárias para criar jogos com mecânica bidimensional dentro de ambientes tridimensionais.

---

## Curadoria de Fontes
Para mitigar alucinações e fundamentar o aprendizado em boas práticas da indústria, o NotebookLM foi alimentado com materiais técnicos cobrindo:
* Documentação de pipelines gráficos de motores modernos (Unity URP e Godot Engin).
* Tutoriais avançados de matemática vetorial e álgebra linear aplicados a transformações de matrizes espaciais.
* Guias de design de arquitetura para restrição axial e sistemas de colisão 3D.

---

## Engenharia de Prompts e "Cicatrizes" (Troubleshooting)
Esta seção mapeia o processo de iteração técnica para refinar as saídas da inteligência artificial.

### Prompt 1: Abordagem Direta
* **Prompt original:** "Como criar um jogo 2.5D?"
* **Resposta da IA:** Gerou diretrizes superficiais e genéricas, focando em conceitos artísticos superficiais e ferramentas, sem aprofundamento na lógica matemática do motor de jogo.
* **Problema encontrado:** Resposta vaga, inadequada para tomadas de decisão de arquitetura de código.

### Prompt 2: Abordagem Refinada
* **Prompt melhorado:** "Quais são os passos fundamentais para estruturar e desenvolver um jogo no formato 2.5D dividindo por arquitetura, física e configuração de câmera?"
* **Resultado da IA:** Resposta de alto nível técnico, fornecendo as equações vetoriais de restrição física, o comportamento geométrico de colisores e os modelos matemáticos de projeção de câmera.

> Lição Aprendida (Cicatriz):Motores de jogos operam sob lógica matemática rígida. O NotebookLM entrega um resultado infinitamente superior quando o prompt é parametrizado com jargões técnicos da engenharia de software (como restrição axial, graus de liberdade e interpolação).

---

## Miniguia de Estudo (Entrega Final - Gerada pelo NotebookLM)

### Resumos Estruturados dos Pilares Técnicos

#### 1. Arquitetura do Jogo
A arquitetura 2.5D separa de forma estrita a dimensão gráfica da dimensão lógica do espaço do jogo através de quatro abordagens:
* **Lógica 2D com Grafismo 3D:** Física e colisões operam em um plano cartesiano bidimensional (\(X, Y\)), enquanto o cenário e a iluminação utilizam malhas poligonais 3D (Ex: *Inside*).
* **Lógica 3D com Grafismo 2D:** O mundo e as colisões são volumétricos (3D), mas a apresentação visual usa planos bidimensionais (sprites).
* **Restrição Axial em Espaço Volumétrico:** O jogador se move no espaço 3D, mas seus eixos e a câmera são restringidos por curvas ou "trilhos" virtuais.
* **Estilo HD-2D:** Personagens em pixel art bidimensional inseridos em cenários 3D sob iluminação dinâmica e efeitos de profundidade de campo.

#### 2. Engenharia de Física e Colisões
Para evitar comportamentos indeterminados e bugs físicos, aplicam-se as seguintes configurações:
* **Congelamento de Graus de Liberdade:** No "Rigidbody", bloqueia-se a translação no eixo de profundidade \(Z\) e as rotações em \(X\) e \(Y\). Isso força o motor de física a computar vetores estritamente no plano de ação \(XY\) através da equação:
  \[F_{resultante} = m \cdot [a_x, a_y, 0]^T\]
* Uso de Colisores Volumétricos 3D: Evita-se superfícies sem espessura (*Planes*). Em altas velocidades, ocorre o fenômeno de "Tunneling" (quando o motor falha em detectar colisões entre frames). A solução é usar BoxColliders com profundidade tridimensional substancial no eixo \(Z\) (entre 1 e 10 unidades).
* Ajuste de Fricção Física: Atribuição de materiais físicos com atrito zerado ao colisor do personagem, impedindo que ele fique preso ou sofra travamentos ao raspar em superfícies verticais.

#### 3. Configuração de Câmera e Apresentação
A câmera realiza a conversão analítica das coordenadas do mundo 3D para a projeção da tela bidimensional:
* **Alinhamento do Vetor de Visão:** O vetor frontal da câmera deve permanecer perpendicular ao plano de movimento, aplicando um deslocamento estático no eixo \(Z\) para estabilizar o plano principal.
* **Zonas de Rastreamento (Deadzone):** Definição de zonas mortas virtuais onde pequenas oscilações do jogador não movem a câmera. A suavização do rastreamento é tratada via funções de atenuação como `SmoothDamp`.
* **Paralaxe Nativo & Billboarding:** Ambientes tridimensionais com câmeras de perspectiva geram o efeito paralaxe de forma natural (objetos distantes em \(Z\) movem-se mais devagar). Para sprites 2D mantendo a ilusão tridimensional, usa-se scripts de *Billboarding* para rotacionar o plano continuamente em direção à lente.

---

### Glossário de Termos Técnicos
* **Tunneling:** Erro de discretização temporal da física onde um objeto atravessa geometrias sólidas devido à alta velocidade entre quadros consecutivos.
* **Graus de Liberdade (DoF):** O número de direções independentes nas quais um corpo rígido pode se mover ou rotacionar no espaço tridimensional.
* **Billboarding:** Técnica de computação gráfica que força um plano poligonal contendo uma textura ou sprite a rotacionar dinamicamente para encarar sempre o vetor de visão da câmera.
* **Deadzone:** Área parametrizada no visor da câmera que delimita uma margem de tolerância para o movimento do personagem antes de ativar o deslocamento de tela.

---

### Prompts Reutilizáveis para Revisão Técnica
```text
1. "Com base nas equações de física e restrição axial do caderno de estudos, crie uma lista de checagem matemática para identificar falhas de Tunneling em colisores dinâmicos."
```
```text
2. "Aja como um Engenheiro de Gráficos e explique como a projeção ortográfica altera a percepção do efeito de Paralaxe Nativo em cenários que usam o estilo HD-2D."
```

---
### Curadoria de Fontes
Para mitigar alucinações e fundamentar o aprendizado em boas práticas da indústria, o NotebookLM foi alimentado com uma curadoria robusta de **36 fontes ao todo** (composta por 10 artigos, livros e TCC em PDF; 6 vídeos técnicos do YouTube; 6 sites de referência e mais 14 fontes mapeadas com o auxílio de mecanismos de Deep Research). 

As principais referências e links de acesso incluem:
* **Wikipedia (Fundamentos e Histórico):** [Artigo Técnico sobre Perspectiva 2.5D](https://en.wikipedia.org/wiki/2.5D)
* **Alura (Ciclo de Produção):** [Guia Completo de Criação de Jogos](https://www.alura.com.br/artigos/como-criar-um-jogo?srsltid=AU7gw4UVg7NFtYhYR3WEsuQGgGClsxiqn53t1VBBBp-n_kwAu_2zIT_A)
* **Scott Rogers (Game Design):** [Level Up! The Guide to Great Video Game Design (PDF)](https://eclass.uoa.gr/modules/document/file.php/DI413/%CE%94%CE%B9%CE%AC%CF%86%CE%BF%CF%81%CE%B1/Rogers_LevelUp_2010videogame-design.pdf)
* **IFTO (Motores Livres e Educação):** [TCC: Godot Game Engine como ferramenta para criação de Apps Educacionais](https://portal.ifto.edu.br/porto/campus-porto/ensino/biblioteca/acervo/trabalho-de-conclusao-de-curso-tcc/licenciatura-em-computacao/2018/tcc-elisama-martins-goncalves.pdf)
* **Clecio Espíndola (YouTube):** [Curso Completo Godot 4.2 - Criando seu Primeiro Jogo](https://www.youtube.com/watch?v=ovxGPmmVl6k)
* **PW Muniz (YouTube Live):** [Programando um Jogo 2.5D (Side Scrolling 3D) com Cinemachine](https://www.youtube.com/watch?v=FxiRmd8MF6k)
* **Caderno Oficial do Projeto:** [Acesso ao meu NotebookLM Customizado](https://notebook.google.com/notebook/c1cc2869-c927-4fea-b59d-68770c6630a7)

---

Feito com auxilio do NotebookLM no Desafio DIO.
