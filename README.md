# Coleção de Exercícios em Java

Este repositório contém uma coleção de três exercícios de programação em Java, desenvolvidos para praticar e demonstrar diferentes conceitos da linguagem, desde o básico até tópicos mais avançados como Programação Orientada a Objetos, Generics e tratamento de exceções.

## Tecnologias Utilizadas

- **Java 17**
- **Maven** (para gerenciamento de dependências e build)
- **Lombok** (para reduzir código boilerplate como getters e setters)

## Estrutura do Projeto

O projeto é organizado em pacotes, onde cada pacote representa um exercício independente:

- `exercise01`: Análise estatística de um array de números.
- `exercise02`: Calculadora de tempo de viagem para diferentes veículos.
- `exercise03`: Sistema de repositório genérico para gerenciamento de entidades.

---

## Exercício 1: Análise de Array Numérico

### Objetivo
Gerar um array de inteiros com tamanho e valores aleatórios e, em seguida, calcular e exibir o valor máximo, o valor mínimo e a média de seus elementos.

### Como Funciona
A classe `Calculation` herda de `ArrayClass`, que é responsável por criar um array com tamanho (entre 1 e 20) e elementos (entre 1 e 50) aleatórios. A classe `Calculation` então implementa as interfaces `Max`, `Min`, e `Average` para realizar os cálculos necessários. O programa principal instancia `Calculation` e imprime os resultados.

### Como Executar
Execute o método `main` na classe `exercise01.aplication.Program`.

---

## Exercício 2: Calculadora de Tempo de Viagem

### Objetivo
Calcular o tempo necessário (em dias, horas, minutos e segundos) para percorrer uma distância informada pelo usuário, com base no tipo de veículo escolhido.

### Como Funciona
O programa apresenta um menu de console onde o usuário pode escolher entre veículos com velocidades pré-definidas (Bicicleta, Carro, Moto) ou definir um veículo customizado com tipo e velocidade próprios. Após o usuário inserir a distância em metros, a classe `CalculationTime` realiza o cálculo e exibe o resultado formatado.

O projeto demonstra:
- **Herança e Polimorfismo**: Com a classe abstrata `RacingVehicles` e suas subclasses.
- **Tratamento de Exceções**: Utiliza exceções customizadas como `DistanceInMetersException` e `SpeedException` para validar a entrada do usuário.
- **Interação com o Usuário**: Através de um menu de console gerenciado pela classe `UX`.

### Como Executar
Execute o método `main` na classe `exercise02.aplication.Program`.

---

## Exercício 3: Sistema de Repositório Genérico

### Objetivo
Demonstrar o uso de **Generics** em Java através de um sistema de repositório que pode armazenar e gerenciar diferentes tipos de objetos (Produtos, Países, Usuários).

### Como Funciona
Este é o exercício mais completo. O usuário escolhe com qual tipo de repositório deseja trabalhar (Produtos, Países ou Usuários). Em seguida, um segundo menu permite realizar operações de CRUD (Adicionar, Buscar, Contar, Listar e Deletar) nos elementos do repositório.

Destaques da implementação:
- **Generics**: A classe `Repository<T>` é totalmente genérica e pode operar com qualquer tipo de objeto que herde da classe abstrata `Element`.
- **Interfaces**: O projeto define contratos claros para as funcionalidades do repositório (`Save`, `Find`, `Count`, `DeleteElement`, etc.).
- **Validação de Dados**: A classe `Util` usa expressões regulares (`regex`) para validar as entradas do usuário, como nomes, códigos ISO de países e nomes de usuário.
- **Estrutura de Dados**: Utiliza `ArrayList` como a estrutura de dados subjacente para o repositório.

### Como Executar
Execute o método `main` na classe `exercise03.aplication.Program`.

---

## Como Compilar e Executar o Projeto

### Pré-requisitos
- **JDK 17** ou superior.
- **Apache Maven**.

### Passos para Execução

1. **Clone o repositório:**
   ```bash
   git clone <URL_DO_SEU_REPOSITORIO>
   cd Java-Exercicio01
   ```

2. **Compile o projeto com Maven:**
   ```bash
   mvn clean install
   ```

3. **Execute um dos exercícios:**
   Você pode executar qualquer um dos programas principais através do seu IDE (IntelliJ, Eclipse, etc.) ou via linha de comando com o Maven.

   **Exemplo (executando o Exercício 2):**
   ```bash
   mvn exec:java -Dexec.mainClass="exercise02.aplication.Program"
   ```

   **Para executar outros exercícios, substitua o valor de `-Dexec.mainClass`:**
   - Exercício 1: `exercise01.aplication.Program`
   - Exercício 3: `exercise03.aplication.Program`

## Observações sobre a Qualidade do Código

O projeto demonstra uma boa aplicação de princípios de design de software. No entanto, há uma oportunidade de melhoria no gerenciamento do recurso `Scanner`.

- **Gerenciamento do `Scanner`**: As classes `Utils` (em `exercise02`) e `Util` (em `exercise03`) utilizam um `Scanner` estático que é fechado (`SC.close()`) no final de cada programa. Fechar um `Scanner` que lê de `System.in` também fecha o `System.in`, o que impede que ele seja lido novamente por qualquer outra parte da aplicação na mesma sessão da JVM. Uma abordagem mais robusta seria instanciar o `Scanner` no método `main` e passá-lo como dependência para as classes que precisam dele, ou usar um bloco `try-with-resources` para garantir seu fechamento adequado apenas no final da execução completa do programa.