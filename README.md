# Controle-de-estoque-em-Java

Aplicação simples em Java, via linha de comando, para cadastrar um produto e controlar a movimentação (entrada e saída) da sua quantidade em estoque.

## O que o programa faz

1. Pede ao usuário os dados de um produto: nome, preço e quantidade em estoque.
2. Exibe os dados cadastrados, formatados, incluindo o valor total em estoque (preço x quantidade).
3. Pede uma quantidade a ser **adicionada** ao estoque e atualiza o produto.
4. Exibe os dados atualizados.
5. Pede uma quantidade a ser **removida** do estoque e atualiza o produto.
6. Exibe os dados atualizados novamente.

## Estrutura do projeto

```
src/
├── application/
│   └── Programa.java     -> classe principal, interage com o usuário
└── entities/
    └── Product.java      -> classe que representa o produto
```

### `entities/Product.java`

Representa um produto com três atributos públicos:

- `name` (String): nome do produto
- `price` (double): preço unitário
- `quantity` (int): quantidade em estoque

E os seguintes métodos:

- `totalValueInStock()`: calcula o valor total em estoque (`price * quantity`).
- `addProducts(int quantity)`: soma uma quantidade ao estoque atual.
- `removeProducts(int quantity)`: subtrai uma quantidade do estoque atual.
- `toString()`: sobrescreve a exibição padrão do objeto, retornando uma string formatada com nome, preço (duas casas decimais), quantidade e valor total em estoque.

### `application/Programa.java`

Classe com o método `main`, responsável por toda a interação com o usuário via `Scanner`:

- Define `Locale.setDefault(Locale.US)` para garantir que números decimais usem ponto (`.`) em vez de vírgula, evitando erros de leitura com `nextDouble()`.
- Cria um objeto `Product` e preenche seus dados a partir da entrada do usuário.
- Imprime o produto (chamando implicitamente o `toString()`).
- Solicita e aplica uma adição de estoque, depois uma remoção, mostrando o estado do produto após cada operação.
- Fecha o `Scanner` ao final.

## Como executar

Compile e rode a partir da pasta `src`:

```bash
javac application/Programa.java entities/Product.java
java application.Programa
```

## Exemplo de uso

```
Enter product data: 
Name: Mouse
Price: 89.90
Quantity in stock: 20

Product data: Mouse, $ 89.90, 20 units, Total: $ 1798.00

Enter the number of products to be added in stock: 
10

Update data: Mouse, $ 89.90, 30 units, Total: $ 2697.00

Enter the number of products to be removed in stock: 
5

Update data: Mouse, $ 89.90, 25 units, Total: $ 2245.00
```


