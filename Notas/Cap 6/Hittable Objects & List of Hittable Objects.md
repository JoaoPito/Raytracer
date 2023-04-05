Inicialmente no livro, os objetos (só esferas por enquanto) eram colocados um a um no código no arquivo **main.cc**.
Foi criada uma abstração para todos os objetos em que o ray caster pode atingir, a classe **Hittable**.

Depois, foi criado uma outra classe para representar todos os objetos de uma cena, o **hittable_list**, nesse capítulo todos os objetos da cena são adicionados em um objeto dessa classe.

Essas classes fazem uso das bibliotecas de C++ [[vector]] e [[shared_ptr]].