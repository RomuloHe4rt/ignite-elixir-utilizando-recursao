List Length

O projeto `list_length` é o primeiro desafio da @Rocketseat da Trilha de [Elixir](https://elixir-lang.org/).

O desafio é criar um módulo `ListLength` contendo uma função `call/1` que recebe como argumento uma [Lista](https://hexdocs.pm/elixir/List.html) de números. Essa função deve retornar o tamanho dessa lista.

Iniciando o projeto

```bash
mix new list_length
```

Criando o teste

```elixir
defmodule ListLengthTest do
  use ExUnit.Case

  describe "call/1" do
    test "count list elements" do
      list1 = [1, 2, 3, 4, 5, 6]
      list2 = [1, 2]
      list3 = [1, 2, 3, 4]

      assert ListLength.call(list1) == 6
      assert ListLength.call(list2) == 2
      assert ListLength.call(list3) == 4
    end

    test "passing an empty list" do
      list = []

      assert ListLength.call(list) == 0
    end
  end
end

```

Criando a função usando [recursão](https://elixir-lang.org/getting-started/recursion.html) e com o conceito de _Tail Call Optimization_ ([wikipedia](https://en.wikipedia.org/wiki/Tail_call)):

```elixir
defmodule ListLength do
  def call(list), do: length(list, 0)

  defp length([], acc), do: acc

  defp length([_head | tail], acc) do
    acc = 1 + acc
    length(tail, acc)
  end
end
```

Executando o projeto no terminal:

```bash
iex -S mix
```

Executando a função:

```elixir
ListLength.call([1, 3, 6, 43, 6])
#..> 5
```

Até o próximo desafio! 💜
