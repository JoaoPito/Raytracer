Aplicar anti-aliasing usando raytracing é apenas calcular a **média de múltiplos raios emitidos do mesmo ponto na câmera mas que cada um tem a direção variada um pouquinho**, isso faz com que os raios batam em lugares levemente diferentes, fazendo com que a cor (mais notável nas bordas dos objectos) fiquem levemente borradas.

## Implementação
Isso é feito usando a variável ***samples_per_pixel*** no arquivo **main.cc**.