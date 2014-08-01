---
layout: post
title: Iniciando com Swift
---

Finalmente resolvi instalar o XCode 6 - atualmente no Beta 4 - e poder brincar com a nova linguagem da Apple, anunciada no último WWDC: Swift. Embora minha experiência com Objective-C seja praticamente nula, a Swift parece-me bem interessante por alguns promessas:

  * Sintaxe nova, buscando facilitar a vida do programador
  * Eficiente, gerando código nativo com LLVM por baixo (nada de VMs ou coisa parecida)
  * "Interativa", através do Playground no XCode 6 é possível brincar, quase como se fosse uma linguagem interpretada

Dando apenas uma pincelada inicial, o trecho a seguir é um programa completo em Swift:

{% highlight objective-c linenos %}
let name = "Batima"
println("\(name), que porra é essa?")
{% endhighlight %}

Saída:

{% highlight tex %}
Batima, que porra é essa?
{% endhighlight %}

Se compararmos com o código necessário para fazer a mesma operação em C:

{% highlight c linenos %}
#include <stdio.h>

int
main (int argc, char argv*[]) {
  char* name = "Batima";

  printf("%s, que porra e essa?", name);

  return 0;
}
{% endhighlight %}

A primeria coisa que curti logo de cara foi poder chamar funções e variáveis diretamente na String, sem precisar dessas variáveis de formatação e de um sprintf, por exemplo.
