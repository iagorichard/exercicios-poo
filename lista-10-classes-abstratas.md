# Lista - Classes Abstratas
## Programação Orientada a Objetos

**Observações gerais para todas as questões:**
- Em **todas as 7 questões**, as classes devem:
  - Ter **encapsulamento de atributos** (uso de `private` e métodos `get` e `set`);
  - Possuir **dois construtores**: um **vazio** e um que **inicializa todos os atributos**;
  - Os métodos `set` devem realizar **validações** e **lançar `Exception`** (genérica mesmo) em caso de valores inválidos;
  - Em todos os exercícios, criar uma Main para validar o uso das classes codificadas.
  
---

## Exercício 1

Uma empresa deseja modelar seus diferentes tipos de trabalhadores para realizar uma análise interna sobre salários e funções desempenhadas. Cada tipo de trabalhador possui uma lógica distinta para o cálculo do salário final e para a descrição de suas atividades. O sistema precisa representar essas variações e aplicar regras de bonificação e adicionais conforme o tipo de contrato.

Crie uma hierarquia de classes que represente **trabalhadores** de uma empresa.

- A classe abstrata `Trabalhador` possui os atributos:
  - `nome` (não pode ser nulo ou vazio),
  - `salarioBase` (deve ser maior que zero).

- Os métodos abstratos:
  - `calcularSalarioMensal()`: retorna o salário final do trabalhador.
  - `descricaoTrabalho()`: retorna uma string com a descrição do trabalho.

- Crie duas subclasses:
  - `TrabalhadorCLT`: recebe um bônus fixo de R$ 500 se o salário base for maior que R$ 3000.
  - `TrabalhadorAutonomo`: recebe 80% do salário base como valor final, mas se for menor que R$ 1500, recebe um adicional de R$ 200.

---

## Exercício 2

Um aplicativo de pets está sendo desenvolvido para registrar informações e simular comportamentos de animais de estimação. O objetivo é permitir que tutores e cuidadores possam "interagir" virtualmente com seus animais através de respostas programadas com base em ações humanas, além de identificar o som característico de cada espécie.

Crie uma hierarquia para representar **animais de estimação**.

- A classe abstrata `Pet` deve ter:
  - `nome` (não pode ser nulo ou vazio),
  - `idade` (deve ser maior ou igual a zero).

- Métodos abstratos:
  - `emitirSom()`: retorna uma `String` com o som que o animal faz.
  - `reagir(String acao)`: retorna uma reação com base na ação recebida.

- Crie duas classes concretas:
  - `Cachorro`: late e reage a "carinho" abanando o rabo.
  - `Gato`: mia e reage a "barulho" se escondendo.

---

## Exercício 3

Uma startup está criando uma solução para cálculo de rotas e previsão de tempo de viagem com base no meio de transporte utilizado. A aplicação precisa representar diferentes veículos, calcular o tempo de deslocamento e identificar o tipo de combustível consumido. O sistema precisa ser flexível para receber novos tipos de transporte futuramente.

Crie uma hierarquia de classes que represente **meios de transporte**.

- A classe abstrata `Transporte` deve ter:
  - `velocidadeMaxima` (deve ser maior que 10),
  - `marca` (não pode ser nula nem vazia).

- Métodos abstratos:
  - `calcularTempoViagem(double distancia)`: retorna o tempo estimado.
  - `tipoCombustivel()`: retorna uma string com o tipo de combustível.

- Subclasses:
  - `Carro`: considera velocidade média como 80% da velocidade máxima.
  - `Bicicleta`: sempre retorna “nenhum” como tipo de combustível e calcula tempo como `distância / (velocidadeMaxima * 0.5)`.

---

## Exercício 4

Uma escola de música quer informatizar o sistema de cadastro de músicos e seus instrumentos. Cada músico pode tocar diversos instrumentos, e cada instrumento possui comportamentos próprios de afinação e sonoridade. O objetivo é permitir que o sistema simule o ensaio de um músico com seus instrumentos e avalie os custos e características sonoras envolvidos.

Crie uma hierarquia com **instrumentos musicais** e relacione-a com a classe `Musico` por **agregação**.

- Classe abstrata `Instrumento`:
  - `modelo` (não pode ser nulo ou vazio),
  - `custo` (maior que zero).

- Métodos abstratos:
  - `afinar()`: retorna uma string descrevendo a afinação.
  - `tocar()`: retorna uma string com o som do instrumento.

- Subclasses:
  - `Violao` e `Piano`, com comportamentos distintos.

- A classe `Musico` deve conter uma lista de instrumentos e um método `ensaiarTodos()` que chama o `tocar()` de cada instrumento.

---

## Exercício 5

Um sistema educacional de matemática visual está sendo desenvolvido para ensinar conceitos de geometria de forma prática. O sistema deve representar diferentes figuras geométricas e permitir que o usuário calcule áreas e perímetros por meio de uma calculadora integrada. Cada figura possui regras distintas de validação e comportamento.

Modele uma hierarquia de **figuras geométricas** e relacione com `CalculadoraGeometrica` via **composição**.

- Classe abstrata `FiguraGeometrica`:
  - `cor` (não pode ser nula ou vazia),
  - `espessura` (entre 1 e 10).

- Métodos abstratos:
  - `calcularArea()`: retorna a área da figura.
  - `calcularPerimetro()`: retorna o perímetro.

- Subclasses:
  - `Retangulo` e `Circulo`, com validações próprias.

- Classe `CalculadoraGeometrica` deve conter uma figura fixa (composição) e métodos `areaTotal()` e `perimetroTotal()` que apenas chamam os métodos da figura.

---

## Exercício 6

Uma empresa está organizando suas tarefas internas e quer criar um sistema para auxiliar na distribuição e acompanhamento das atividades de seus funcionários. As tarefas possuem níveis de prioridade distintos, e os funcionários precisam visualizar um resumo das atividades sob sua responsabilidade com base em critérios como duração e complexidade.

Crie uma hierarquia de **tarefas** e relacione com a classe `Funcionario` por **agregação**.

- Classe abstrata `Tarefa`:
  - `descricao` (não pode ser nula ou vazia),
  - `duracaoHoras` (entre 1 e 24).

- Métodos abstratos:
  - `executar()`: retorna uma string sobre a execução.
  - `prioridade()`: retorna a prioridade baseada na duração.

- Subclasses:
  - `TarefaSimples` e `TarefaComplexa`.

- Classe `Funcionario` possui uma lista de tarefas e método `resumoTarefas()` que imprime a descrição e prioridade de cada uma.

---

## Exercício 7

Uma loja de eletrônicos está desenvolvendo um sistema de controle de produtos para gestão de estoque e informações de garantia. Cada produto eletrônico possui um fabricante e regras próprias para a garantia estendida. O sistema precisa gerar descrições detalhadas dos produtos, considerando suas características e origem.

Crie uma hierarquia de **produtos eletrônicos**, utilizando **composição** com a classe `Fabricante`.

- Classe abstrata `ProdutoEletronico`:
  - `modelo` (não pode ser vazio),
  - `preco` (maior que R$ 100).

- Métodos abstratos:
  - `calcularGarantiaEstendida()`: retorna um valor baseado no preço.
  - `descricaoDetalhada()`: junta modelo, fabricante e garantia.

- Subclasses:
  - `Notebook` e `Smartphone`, com regras distintas para cálculo de garantia.

- Classe `Fabricante`:
  - `nome` e `paisOrigem` (ambos obrigatórios).
  - Classe `ProdutoEletronico` possui uma composição com `Fabricante`.

---

## Exercício 8 — Sistema de Gestão de Restaurantes

**Contextualização:**  
Um sistema completo de **gestão de restaurantes** está sendo desenvolvido para controlar o funcionamento de cozinhas, pratos, pedidos e funcionários. O sistema deve garantir integridade nos dados (ex: valores positivos, campos obrigatórios) e oferecer diversas formas de operação.

- Crie a interface `OperacoesCardapio` com métodos:
  - `adicionarIngrediente(String nome, double quantidade)`,
  - `removerIngrediente(String nome)`,
  - `listarIngredientes()`.

- Crie a interface `Preparavel` com métodos:
  - `prepararPrato()`,
  - `verificarTempoPreparo()`.

- Crie a classe abstrata `Prato` com atributos:
  - `nome` (não pode ser nulo ou vazio),
  - `preco` (deve ser maior que R$ 10),
  - `tempoPreparo` (em minutos, deve ser maior que 0).

- Subclasses:
  - `PratoSimples`: implementa `Preparavel`, tem lista de ingredientes simples (String).
  - `PratoEspecial`: implementa `Preparavel` e `OperacoesCardapio`, mantém ingredientes com quantidade e possui métodos de verificação de custo e operação dinâmica do cardápio.

- Classe `Cozinha`: possui composição com uma lista de `Prato` e um método `cozinharTudo()` que chama `prepararPrato()` de todos os pratos.

- Lançar `Exception` nos `set` se `preco <= 10` ou `nome` estiver vazio.

---

## Exercício 9 — Sistema de Monitoramento de Animais em Zoológico

**Contextualização:**  
Um zoológico precisa automatizar o controle e o monitoramento de seus animais, cuidadores e áreas específicas. O sistema também deve calcular custos de manutenção e responder a eventos programados.

- Crie a interface `Monitoravel` com:
  - `registrarComportamento(String observacao)`,
  - `relatorioDiario()`,
  - `emiteAlerta()`.

- Crie a interface `Custeavel` com:
  - `calcularCustoManutencao()`,
  - `calcularCustoAlimentacao()`.

- Classe abstrata `Animal` com atributos:
  - `especie`, `idade`, `peso`, `alimentacaoDiaria`, `identificador` (nenhum pode ser nulo ou <= 0).

- Subclasses:
  - `Ave` e `Mamifero`, ambas implementam `Monitoravel` e `Custeavel`, e possuem lógica distinta de custo de alimentação.

- Classe `Cuidador` (associação com os animais):
  - `nome`, `turno`, `animaisDesignados`.

- Classe `Setor` (composição de animais e cuidadores):
  - `nome`, `responsavel`, `capacidade`, lista fixa de `animais` e `cuidadores`.

- Lançar `Exception` se peso for menor que 0 ou idade maior que 100.

---

## Exercício 10 — Sistema de Viagens e Reservas Inteligente

**Contextualização:**  
Você está desenvolvendo uma solução para uma empresa de **turismo inteligente**, onde é necessário modelar pacotes, clientes e atividades com alto nível de personalização. O sistema deve validar dados e possibilitar a análise de experiências anteriores.

- Crie a interface `Reservavel`:
  - `reservar()`,
  - `cancelarReserva()`,
  - `statusReserva()`.

- Interface `Analisavel`:
  - `avaliar(int nota)`,
  - `historicoAvaliacoes()`,
  - `mediaAvaliacoes()`.

- Classe abstrata `Atividade`:
  - `titulo`, `descricao`, `duracaoHoras`, `preco`, `nivelDificuldade`.

- Subclasses:
  - `PasseioHistorico` (implementa `Reservavel`, `Analisavel`), valida se o preço é ao menos R$50 e limita a nota de avaliação entre 1 e 5.
  - `TrilhaEcologica` (implementa ambas também, mas adiciona atributos extras como altitude e tipo de terreno).

- Classe `Cliente` com:
  - `nome`, `email`, `listaReservas`, métodos para listar, cancelar e avaliar.

- Classe `PacoteTuristico` com:
  - composição de múltiplas atividades e cliente responsável.

- Lançar `Exception` se a nota for inválida, se o preço for abaixo de R$50 ou se o email do cliente não contiver `@`.

---
