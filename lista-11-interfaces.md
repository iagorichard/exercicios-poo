# Lista - Interfaces, Herança e Composição
## Programação Orientada a Objetos

**Observações gerais para todas as questões:**
- Em **todas as 10 questões**, as classes devem:
  - Ter **encapsulamento de atributos** (uso de `private` e métodos `get` e `set`);
  - Possuir **dois construtores**: um **vazio** e um que **inicializa todos os atributos**;
  - Os métodos `set` devem realizar **validações** e **lançar `Exception`** (genérica mesmo) em caso de valores inválidos;
  - Criar uma `Main` para validar o uso das classes codificadas.

---

## Exercício 1

**Contextualização:**  
Uma empresa de entregas deseja padronizar os meios de entrega disponíveis, seja por transporte terrestre ou aéreo. Cada tipo deve seguir um contrato com métodos obrigatórios que descrevem a rota e o custo da entrega.

- Crie uma **interface** `Entrega` com dois métodos:
  - `calcularFrete(double distancia)` e `descricaoRota()`.

- Implemente em duas classes:
  - `EntregaTerrestre`: considera R$ 0.75 por km.
  - `EntregaAerea`: considera R$ 2.50 por km, mas entrega em metade do tempo estimado.

---

## Exercício 2 — Interfaces com múltiplas capacidades (nível médio)

**Contextualização:**  
Uma empresa está desenvolvendo uma aplicação para **gestão de conteúdo digital** com foco em diferentes perfis de usuários criadores. A plataforma permite que os usuários produzam conteúdos, gerenciem seus perfis, acompanhem estatísticas e se comuniquem com outros usuários.

- Crie as interfaces:
  - `Publicador`, com métodos `criarPost(String conteudo)` e `removerPost(int idPost)`;
  - `Estatistico`, com métodos `visualizarEstatisticas()` e `compararDesempenhoComOutro(Estatistico outro)`;  
  - `Comunicador`, com métodos `enviarMensagem(String usuarioDestino, String mensagem)` e `responderMensagem(int idMensagem, String resposta)`.

- Crie as classes:
  - `CriadorBasico`: implementa `Publicador`;
  - `Influencer`: implementa `Publicador` e `Comunicador`;
  - `AnalistaDeConteudo`: implementa apenas `Estatistico`;
  - `CriadorPremium`: implementa as três interfaces e possui métodos personalizados para priorizar respostas a mensagens com mais curtidas.

---

## Exercício 3 

**Contextualização:**  
Um sistema de **agendamento e prestação de serviços autônomos** está sendo desenvolvido. Os prestadores podem executar serviços, avaliar clientes, além de manterem um histórico de atividades e receberem pagamentos.

- Crie a interface `PrestadorServico`, com os métodos:
  - `realizarServico(String descricao)`,
  - `calcularValor(double horas, double taxaPorHora)`,
  - `avaliarCliente(String nomeCliente, int nota)`.

- Crie a interface `Historico`, com métodos:
  - `adicionarRegistro(String registro)` e `listarRegistros()`.

- Crie a interface `Recebivel`, com:
  - `registrarPagamento(double valor)` e `saldoAtual()`.

- Crie a classe abstrata `PessoaAutonoma` com atributos:
  - `nome` (não pode ser nulo ou vazio),
  - `email` (deve conter "@"),
  - `cpf` (11 dígitos).

- Crie as classes:
  - `Diarista`: herda `PessoaAutonoma` e implementa `PrestadorServico` e `Recebivel`;
  - `Eletricista`: herda `PessoaAutonoma` e implementa todas as interfaces, utilizando o `Historico` para log de atendimentos;
  - Ambas devem conter lógica para não permitir avaliação com nota inferior a 1 ou superior a 5 e registrar valores recebidos com validação mínima de R$50.

---


## Exercício 4 

**Contextualização:**  
Um sistema bancário está sendo projetado e cada **conta bancária** precisa exibir o saldo e emitir extratos em diferentes formatos.

- Crie uma interface `ImpressoraExtrato` com o método `gerarExtrato()`.

- Crie a classe `ContaBancaria` com atributos:
  - `titular`, `saldo` (saldo deve ser >= 0).

- Crie duas implementações de `ImpressoraExtrato`:
  - `ExtratoSimples` e `ExtratoDetalhado`, cada uma exibindo o saldo de forma diferente.

- A classe `ContaBancaria` deve ter composição com `ImpressoraExtrato` e delegar a ela o método `gerarExtrato()`.

---

## Exercício 5 

**Contextualização:**  
Uma empresa de construção civil quer monitorar **equipamentos** e **funcionários** responsáveis.

- Classe abstrata `Equipamento`:
  - `codigo` e `nome` (obrigatórios),
  - método abstrato `custoManutencao()`.

- Interface `Operavel` com método `operar()`.

- Classes `Escavadeira` e `Betoneira` devem implementar `Operavel` e herdar `Equipamento`.

- Classe `Funcionario` deve ter nome e cargo e conter uma lista de equipamentos atribuídos.

- `Funcionario` pode imprimir o resumo dos equipamentos operados.

---

## Exercício 6 

**Contextualização:**  
Você está desenvolvendo um sistema para um hospital, com foco em **profissionais de saúde** e **atendimentos**.

- Crie uma interface `Atendente` com o método `realizarAtendimento(Paciente p)`.

- Classe abstrata `ProfissionalSaude` com:
  - `nome`, `registro`, `especialidade` (todos obrigatórios),
  - método abstrato `resumoProfissional()`.

- Crie as classes:
  - `Medico` e `Enfermeiro`, que implementam `Atendente` e herdam `ProfissionalSaude`.

- Crie `Paciente` com nome, idade e histórico médico.

- A classe `Hospital` contém lista de profissionais e pacientes, e pode listar todos os atendimentos realizados.

---

## Exercício 7

**Contextualização:**  
Uma plataforma de **cursos online** precisa modelar usuários, cursos e a interação entre eles.

- Interface `Avaliavel` com `avaliar(int nota)` (nota entre 1 e 5).
- Interface `Inscrevivel` com `inscreverCurso(Curso c)`.
- Interface `Certificavel` com `emitirCertificado()`.

- Classe abstrata `Pessoa` com `nome`, `email`.

- Classe `Aluno` herda `Pessoa` e implementa `Inscrevivel` e `Avaliavel`.
- Classe `Instrutor` herda `Pessoa` e implementa `Certificavel`.

- Classe `Curso` com nome, carga horária, nota média (calculada a partir das avaliações feitas pelos alunos).
- `Aluno` deve poder avaliar cursos que está inscrito.
- `Instrutor` pode emitir certificados se a carga horária for > 20h.

## Exercício 8

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

## Exercício 9

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

## Exercício 10 

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


---


