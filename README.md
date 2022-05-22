# Estudo do Efeito da Quantização e Amostragem na Construção das Imagens Digitais.


### Para que uma imagem possa ser armazenada e/ou processada em um computador, torna-se necessária sua discretização tanto em nível de coordenadas espaciais quanto de valores de brilho. Este projeto tem como objetivo observar o efeito da quantização e amostragem na construção das imagens digitais visualizadas no dia a dia.

## Objetivos do projeto:

Pegar uma imagem em 256 níveis de cinza (8 bits), tamanho N x M para realizar as seguintes operações:

- Produzir três imagens reduzindo a **amostragem espacial** da imagem original em 50%, 25% e 12,5%

- Produzir três imagens reduzindo a **quantização da intensidade dos pixels** da imagem original para 4, 32 e 64 bits.

## Informações e Links Importantes:

Foi necessário a utilização de uma imagem em 256 níveis de cinza (8 bits) 2⁸ = 256 níveis. A imagem utilizada no projeto faz parte do módulo **data** da biblioteca ``scikit-image``

A biblioteca ``scikit-image`` é uma coleção de algoritmos para processamento de imagens e está disponível [**nesse link.**](https://scikit-image.org/)

Já o módulo **data** da biblioteca ``scikit-image`` de onde foi retirada a imagem pode ser visualizada [**aqui.**](https://scikit-image.org/docs/dev/api/skimage.data.html?highlight=data#module-skimage.data)
