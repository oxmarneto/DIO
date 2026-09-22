# 🎮 DIO — Miniguia de Estudos Interativo: Engenharia de Games 2.5D e 3D com NotebookLM

> Projeto desenvolvido para o desafio **“Treinando uma IA de Aprendizagem: Explore o Poder do NotebookLM”**, da DIO, utilizando Inteligência Artificial como ferramenta de apoio à pesquisa, organização e consolidação do conhecimento técnico.

---

## 📌 Sobre o Projeto

Este repositório documenta um projeto prático de **aprendizagem ativa com auxílio de Inteligência Artificial**, utilizando o **NotebookLM** como ferramenta de pesquisa, síntese e revisão técnica.

O tema central do estudo é o **desenvolvimento de games 2.5D e 3D**, com foco nos fundamentos de:

* Arquitetura híbrida 2D/3D;
* Engenharia de física e colisões;
* Restrições de movimento e graus de liberdade;
* Transformações espaciais;
* Projeção e configuração de câmeras;
* Paralaxe e profundidade;
* Billboarding;
* Boas práticas de desenvolvimento de jogos.

O objetivo foi compreender **como diferentes componentes de um motor de jogos trabalham em conjunto para criar uma experiência 2.5D**, especialmente quando a lógica de gameplay e a representação visual utilizam diferentes dimensões.

---

# 🎯 Objetivos de Aprendizagem

Durante o desenvolvimento do projeto, os principais objetivos foram:

1. Compreender as diferentes arquiteturas utilizadas em jogos 2.5D.
2. Investigar como motores de jogos tratam física e colisões em ambientes híbridos.
3. Entender a aplicação de restrições de movimento em espaços tridimensionais.
4. Estudar conceitos de álgebra linear e transformações espaciais aplicados a jogos.
5. Compreender o funcionamento de câmeras ortográficas e perspectivas.
6. Investigar técnicas como **Deadzone, Paralaxe e Billboarding**.
7. Utilizar o NotebookLM para transformar diferentes fontes técnicas em um material de estudo estruturado.
8. Aprimorar a elaboração de prompts técnicos para obter respostas mais específicas e úteis.

---

# 📚 Curadoria de Fontes

Para reduzir respostas genéricas e minimizar possíveis alucinações, foi realizada uma curadoria de materiais técnicos utilizados como base de conhecimento no NotebookLM.

Ao todo, foram utilizadas **36 fontes**, distribuídas entre:

* 📄 **10 artigos, livros e TCCs em PDF**;
* 🎥 **6 vídeos técnicos do YouTube**;
* 🌐 **6 sites de referência**;
* 🔎 **14 fontes adicionais identificadas com auxílio de mecanismos de Deep Research**.

A curadoria buscou combinar fundamentos teóricos, documentação técnica, tutoriais práticos e materiais relacionados ao desenvolvimento de jogos.

Entre os temas pesquisados estão:

* Pipelines gráficos;
* Unity URP;
* Godot Engine;
* Física de jogos;
* Colisões 2D e 3D;
* Álgebra linear;
* Matrizes e transformações espaciais;
* Câmeras;
* Game Design;
* Arquitetura de jogos 2.5D.

---

# 🧠 Engenharia de Prompts e "Cicatrizes"

Uma das etapas mais importantes do projeto foi observar como a qualidade das respostas do NotebookLM mudava de acordo com a especificidade dos prompts.

## 🔹 Prompt 1 — Abordagem Direta

**Prompt utilizado:**

> "Como criar um jogo 2.5D?"

### Resultado

A resposta apresentou conceitos introdutórios e relativamente genéricos, concentrando-se principalmente em aspectos visuais, ferramentas e conceitos básicos.

### Problema identificado

A resposta não apresentava profundidade suficiente para apoiar decisões relacionadas à **arquitetura, física e implementação técnica**.

---

## 🔹 Prompt 2 — Abordagem Refinada

**Prompt utilizado:**

> "Quais são os passos fundamentais para estruturar e desenvolver um jogo no formato 2.5D dividindo por arquitetura, física e configuração de câmera?"

### Resultado

A abordagem mais específica produziu uma resposta tecnicamente mais direcionada, abordando:

* Restrições de movimento;
* Graus de liberdade;
* Colisores;
* Física;
* Projeção de câmera;
* Transformações espaciais;
* Comportamento geométrico;
* Técnicas de rastreamento de câmera.

### 💡 Lição Aprendida

> **Quanto mais bem definido o problema, maior a capacidade do NotebookLM de direcionar suas respostas para aspectos técnicos específicos.**

No contexto de engenharia de software e desenvolvimento de jogos, utilizar termos como **restrição axial, graus de liberdade, colisão, projeção, interpolação e transformação espacial** ajuda a estabelecer um contexto técnico mais preciso para a pesquisa.

---

# 🎮 Miniguia de Estudo

## 1. Arquitetura do Jogo 2.5D

O conceito de 2.5D pode ser implementado de diferentes maneiras, dependendo de como a lógica do jogo e a representação visual utilizam as dimensões do espaço.

### 🔹 Lógica 2D com Grafismo 3D

A física e as regras de movimentação permanecem essencialmente bidimensionais, enquanto o cenário utiliza modelos e elementos gráficos tridimensionais.

**Exemplo:** jogos que utilizam movimentação lateral com cenários 3D.

---

### 🔹 Lógica 3D com Grafismo 2D

O mundo possui física e colisões tridimensionais, enquanto personagens ou outros elementos visuais podem ser representados por sprites ou planos texturizados.

Essa abordagem permite utilizar elementos 2D dentro de um ambiente espacial 3D.

---

### 🔹 Restrição Axial em Espaço Volumétrico

O jogo utiliza um ambiente 3D, mas restringe determinados graus de liberdade do personagem.

Por exemplo, o personagem pode utilizar física 3D, mas permanecer limitado a um determinado plano de movimentação.

Essa abordagem é particularmente útil para jogos **side-scrolling 3D**.

---

### 🔹 Estilo HD-2D

Uma combinação estética na qual elementos 2D, como personagens em pixel art, são inseridos em ambientes tridimensionais com:

* Iluminação dinâmica;
* Sombras;
* Profundidade;
* Efeitos de pós-processamento;
* Profundidade de campo.

O resultado combina elementos visuais bidimensionais com recursos de renderização 3D.

---

# ⚙️ 2. Engenharia de Física e Colisões

A implementação de física em um jogo 2.5D exige atenção especial às restrições de movimento e às configurações dos componentes físicos.

## 🔹 Restrição de Graus de Liberdade

Uma abordagem comum consiste em utilizar um corpo rígido 3D e restringir determinados eixos de movimento e rotação.

Por exemplo, dependendo da orientação adotada pelo projeto, pode-se bloquear:

* Translação no eixo de profundidade;
* Rotação em determinados eixos.

Isso permite que o motor continue utilizando o sistema de física 3D enquanto o gameplay permanece restrito a um plano.

Em uma representação simplificada:

$$
F_{resultante} = m \cdot
\begin{bmatrix}
a_x \\
a_y \\
0
\end{bmatrix}
$$

Nesse caso, a componente de aceleração associada à profundidade permanece restrita.

> **Observação:** o eixo utilizado como profundidade depende do sistema de coordenadas adotado pelo projeto. Portanto, a implementação deve ser adaptada à orientação escolhida no motor.

---

## 🔹 Colisores Volumétricos 3D

Em determinadas implementações 2.5D, utilizar geometrias com volume pode oferecer maior previsibilidade para colisões do que depender exclusivamente de superfícies sem espessura.

Um problema importante em sistemas físicos é o **Tunneling**.

Quando um objeto se desloca rapidamente entre dois passos da simulação, ele pode atravessar uma geometria sem que a detecção discreta de colisão registre o contato.

Além da configuração adequada dos colisores, motores de física oferecem mecanismos de detecção contínua de colisão que podem ser utilizados em objetos de alta velocidade.

---

## 🔹 Fricção Física

Materiais físicos podem ser utilizados para controlar o atrito entre superfícies.

Em determinados projetos, reduzir o atrito lateral do personagem pode evitar que ele fique preso ou desacelere excessivamente ao entrar em contato com superfícies verticais.

A configuração ideal depende da mecânica desejada e do comportamento físico do jogo.

---

# 🎥 3. Configuração de Câmera e Apresentação

A câmera é responsável por transformar coordenadas do mundo em uma representação na tela.

Em um ambiente 3D, essa transformação envolve conceitos de:

* Espaço de mundo;
* Espaço da câmera;
* Projeção;
* Espaço de tela.

---

## 🔹 Alinhamento do Vetor de Visão

Em um jogo 2.5D com movimentação restrita, a câmera normalmente é posicionada de maneira consistente em relação ao plano de gameplay.

Uma configuração adequada evita alterações indesejadas na percepção de profundidade e mantém o personagem dentro da composição visual planejada.

---

## 🔹 Deadzone

A **Deadzone** define uma região da tela na qual pequenas movimentações do personagem não provocam imediatamente o deslocamento da câmera.

Isso pode proporcionar:

* Maior estabilidade visual;
* Menos movimentação desnecessária;
* Melhor controle da composição;
* Sensação de câmera mais natural.

---

## 🔹 Suavização do Rastreamento

A movimentação da câmera pode ser suavizada utilizando técnicas de interpolação e funções de amortecimento.

Um exemplo comum em ambientes de desenvolvimento é o uso de mecanismos equivalentes ao:

```text
SmoothDamp
```

A finalidade é evitar que a câmera acompanhe o personagem de maneira excessivamente rígida.

---

## 🔹 Paralaxe

Em ambientes 3D com câmera em perspectiva, diferentes objetos apresentam deslocamentos aparentes diferentes conforme a câmera se movimenta.

Objetos mais próximos tendem a apresentar maior deslocamento aparente do que objetos mais distantes.

Esse fenômeno contribui para a percepção de profundidade e pode ser utilizado como recurso visual em jogos 2.5D.

---

## 🔹 Billboarding

**Billboarding** é uma técnica na qual um plano contendo uma textura ou sprite é orientado para acompanhar a direção da câmera.

É particularmente útil quando elementos 2D precisam permanecer visualmente voltados para o jogador dentro de um ambiente tridimensional.

---

# 📖 Glossário Técnico

| Termo                        | Definição                                                                                                        |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **2.5D**                     | Abordagem que combina características de representação ou gameplay 2D e 3D.                                      |
| **Tunneling**                | Falha na detecção de colisão que pode ocorrer quando um objeto se desloca rapidamente entre passos da simulação. |
| **Graus de Liberdade (DoF)** | Quantidade de movimentos e rotações independentes disponíveis para um corpo.                                     |
| **Billboarding**             | Técnica que orienta um plano ou sprite em direção à câmera.                                                      |
| **Deadzone**                 | Região da tela em que pequenas movimentações do personagem não deslocam imediatamente a câmera.                  |
| **Paralaxe**                 | Diferença aparente no deslocamento de objetos em diferentes profundidades durante o movimento da câmera.         |
| **Colisor**                  | Componente utilizado pelo sistema de física para representar a geometria de interação de um objeto.              |
| **Interpolação**             | Técnica utilizada para produzir transições suaves entre valores ou estados.                                      |
| **Projeção Ortográfica**     | Projeção na qual objetos não diminuem de tamanho conforme se afastam da câmera.                                  |
| **Projeção em Perspectiva**  | Projeção que representa a diminuição aparente dos objetos conforme aumenta sua distância da câmera.              |

---

# 🧪 Prompts Reutilizáveis para Revisão Técnica

### Prompt 1 — Análise de Tunneling

```text
Com base nas equações de física e nas restrições axiais apresentadas no caderno de estudos, crie uma lista de verificação matemática e técnica para identificar possíveis falhas de Tunneling em colisores dinâmicos de um jogo 2.5D.
```

### Prompt 2 — Câmera e Paralaxe

```text
Aja como um Engenheiro de Gráficos e explique como a projeção ortográfica altera a percepção do efeito de paralaxe em cenários que utilizam o estilo HD-2D. Compare com uma câmera em perspectiva e apresente exemplos práticos.
```

---

# 🔗 Principais Referências

Abaixo estão algumas das principais fontes utilizadas na construção do caderno de estudos.

### 📚 Fundamentos e Game Design

* **Wikipedia — 2.5D**
  https://en.wikipedia.org/wiki/2.5D

* **Scott Rogers — Level Up! The Guide to Great Video Game Design**
  https://eclass.uoa.gr/modules/document/file.php/DI413/%CE%94%CE%B9%CE%AC%CF%86%CE%BF%CF%81%CE%B1/Rogers_LevelUp_2010videogame-design.pdf

### 🎮 Desenvolvimento de Jogos

* **Alura — Como criar um jogo**
  https://www.alura.com.br/artigos/como-criar-um-jogo

* **IFTO — Godot Game Engine como ferramenta para criação de Apps Educacionais**
  https://portal.ifto.edu.br/porto/campus-porto/ensino/biblioteca/acervo/trabalho-de-conclusao-de-curso-tcc/licenciatura-em-computacao/2018/tcc-elisama-martins-goncalves.pdf

### ▶️ Conteúdo Técnico

* **Clecio Espíndola — Curso Completo Godot 4.2: Criando seu Primeiro Jogo**
  https://www.youtube.com/watch?v=ovxGPmmVl6k

* **PW Muniz — Programando um Jogo 2.5D (Side Scrolling 3D) com Cinemachine**
  https://www.youtube.com/watch?v=FxiRmd8MF6k

### 🤖 NotebookLM

* **Caderno Oficial do Projeto — NotebookLM Customizado**
  https://notebook.google.com/notebook/c1cc2869-c927-4fea-b59d-68770c6630a7

---

# 🚀 Resultado do Projeto

O projeto demonstrou, na prática, como uma ferramenta de IA pode ser utilizada não apenas para gerar respostas, mas como **instrumento de apoio à pesquisa, organização e revisão do conhecimento técnico**.

O principal aprendizado foi perceber que a qualidade da resposta está diretamente relacionada à qualidade do problema apresentado à ferramenta.

A combinação de:

**Curadoria de fontes → Engenharia de prompts → Validação técnica → Síntese do conhecimento**

permite transformar uma ferramenta de IA em um ambiente de estudo mais estruturado e orientado a objetivos.

---

## 🏆 Desafio DIO

Projeto desenvolvido como parte do desafio:

> **Treinando uma IA de Aprendizagem: Explore o Poder do NotebookLM**

Desenvolvido com auxílio do **NotebookLM**, utilizando pesquisa, curadoria de fontes e engenharia de prompts como ferramentas de aprendizagem.

---

⭐ **Se este projeto foi útil para você, considere deixar uma estrela no repositório!**
