# Projeto de sub-amostragem e quantização de imagens digitais

### **Realizando a importação das bibliotecas necessárias para o projeto**:

```py
# Bibliotecas utilizadas no projeto.
import matplotlib.pyplot as plt
import numpy as np
import pylab as pb
from skimage import data
```

### **Importando a imagem utilizada no projeto diretamente da biblioteca skimage.data**

```py
img_data = data.astronaut()
```


### **È necessário verificar as dimensões da imagem, assim como mostrá-la para verificar se a importação funcionou sem erros.**
```py
img_data.shape
```
    (512, 512, 3)
```py
# Mostrando a imagem img_data
plt.imshow(img_data)
plt.title("Imagem original")
```
    Text(0.5, 1.0, 'Imagem original')

    
<figure>
<img src='https://github.com/AlanMarquesRocha/Quantizacao-e-Amostragem-Img-DIgitais/blob/master/imgs/output_7_1.png?raw=true'/>
</figure>   
    
### **Para fazer a amostragem da img_data, primeiro é necessário transformá-la em níveis de cinza.**

**A conversão da imagem foi feita ultilizando a biblioteca matplotlib.**

Podemos converter a imagem em tons de cinza usando o padrão RGB para a equação de conversão em tons de cinza mostrada na célula abaixo

Podemos implementar este método usando a biblioteca ``Matplotlib``. primeiro precisamos ler a imagem e em seguida, obter as arrays de dimensão vermelha (R), verde (G) e azul (B) da imagem. 

Após obter as arrays podemos aplicar a equação abaixo para obter a imagem em tons de cinza. Precisamos multiplicar as arrays completas com os valores dados na fórmula para obter a imagem em tons de cinza.

```py
# Arrays da imagem img_data.
R, G, B = img_data[:,:,0], img_data[:,:,1], img_data[:,:,2]

# Equação para conversão da imagem em níveis de cinza.
img_cza = 0.2126 * R + 0.7152 * G + 0.0722 * B
```

```py
# Mostra a imagem em tons de cinza após a conversão.
plt.imshow(img_cza, plt.cm.gray)
plt.title("Imagem original em níveis de cinza")
```
    Text(0.5, 1.0, 'Imagem original em níveis de cinza')

<figure>
<img src='https://github.com/AlanMarquesRocha/Quantizacao-e-Amostragem-Img-DIgitais/blob/master/imgs/output_10_1.png?raw=true'/>
</figure> 

## **Nesta etapa serão produzidas 03 (três) imagens decorrentes da sub-amostragem de ``img_data`` em 50%, 25% e 12,5%.**

### **Sub-amostragem da imagem ``img_data`` em 50%**

```py
# Mostrando as dimensões da imagem original
img_data.shape
```

    (512, 512, 3)

```py
# Através das dimensões da imagem original, devemos gerar uma imagem com redução de 50%, ou seja, (256, 256)

# Pega-se um pixel, intercalando o outro, pegando-se apenas 50% da imagem
img_c1 = np.array(img_cza[np.arange(0,img_cza.shape[0],2)])
img_c1 = np.array(img_c1[:,np.arange(0,img_cza.shape[1],2)])

# Mostra o resultado da redução da imagem (sub-amostragem de 50%)
img_c1.shape
```
    (256, 256)

### **Sub-amostragem da imagem ``img_data`` em 25%**

### Existem duas possibilidades

- 1ª - Pega-se a imagem sub-amostrada em 50% e utiliza o mesmo raciocínio da sub-amostragem da ``img_data`` para ``img_c1``

- 2ª Pega-se um pixel, intercalando-se outros 03 (três), utilizando apenas 25% da imagem original (``ìmg_data``)

```py
# mostrando as dimensões da imagem original para fins de comprovação.
img_data.shape
```
    (512, 512, 3)
    
```py
# 1ª Possibilidade:

# Pega-se um pixel, intercalando o outro, pegando-se apenas 25% da imagem
img_c2 = np.array(img_c1[np.arange(0,img_c1.shape[0],2)])
img_c2 = np.array(img_c2[:,np.arange(0,img_c1.shape[1],2)])

# Mostra o resultado da redução da imagem (sub-amostragem de 25%)
img_c2.shape
```
    (128, 128)

```py
# 2ª Possibilidade:

# Pega-se um pixel, intercalando os outros três, pegando-se apenas 25% da imagem
img_c2_ = np.array(img_cza[np.arange(0,img_cza.shape[0],4)])
img_c2_ = np.array(img_c2_[:,np.arange(0,img_cza.shape[1],4)])

# Mostra o resultado da redução da imagem (sub-amostragem de 25%)
img_c2_.shape
```
    (128, 128)


### **Sub-amostragem da imagem ``img_data`` em 12,5%**

### Também é possível utilizar as duas possibilidades mostradas nos casos acima, porém o foco ficará apenas na sub-amostragem da imagem original (``img_data`` para a imagem ``ìmg_c3`` que representa a sub-amostragem em 12,5%.

```py
img_c3 = np.array(img_cza[np.arange(0,img_cza.shape[0], 8)])
img_c3 = np.array(img_c3[:,np.arange(0,img_cza.shape[1], 8)])

# Mostra o resultado da redução da imagem (sub-amostragem de 25%).
# O resultado da imagem deve ser igual a 128/2 = (64, 64)
img_c3.shape
```

    (64, 64)

### **Mostrando o resuldado das sub-amostragens de 50%, 25% e 12,5%.**

```py
# PLota as duas imagens img_cza e img_c1:
fig, (ax1, ax2) = plt.subplots(1, 2, figsize = (9,9), gridspec_kw = {'hspace': 0.3})

# Carrega a imagem img_cza e informa o título por meio da função set_title
ax1.imshow(img_cza, plt.cm.gray) 
ax1.set_title('Imagem original')

# Carrega a imagem img_c1 e informa o título por meio da função set_title
ax2.imshow(img_c1, plt.cm.gray)
ax2.set_title('Sub-amostragem em 50%')

# PLota as duas imagens img_cza e img_c1:
fig, (ax3, ax4) = plt.subplots(1, 2, figsize = (9,9), gridspec_kw = {'hspace': 0.3})

# Carrega a imagem img_c2 e informa o título por meio da função set_title
ax3.imshow(img_c2, plt.cm.gray) 
ax3.set_title('Sub-amostragem em 25%')

# Carrega a imagem img_c3 e informa o título por meio da função set_title
ax4.imshow(img_c3, plt.cm.gray)
ax4.set_title('Sub-amostragem em 12,5%')
```
    Text(0.5, 1.0, 'Sub-amostragem em 12,5%')
    
<figure>
<img src='https://github.com/AlanMarquesRocha/Quantizacao-e-Amostragem-Img-DIgitais/blob/master/imgs/output_22_1.png?raw=true'/>
</figure> 

<figure>
<img src='https://github.com/AlanMarquesRocha/Quantizacao-e-Amostragem-Img-DIgitais/blob/master/imgs/output_22_2.png?raw=true'/>
</figure> 

# Nessa sessão serão produzidas três imagens reduzindo a quantização da intensidade dos pixels da imagem original para 4, 32 e 64 bits.

## Quantização da intensidade dos pixels da imagem para 04 tons,

```py
# Realizando a convrsão da imagem para uint8 (8 bits)
conv_img = np.array(img_cza, dtype = "uint8")
conv_img

# Mostra novamente a imagem img_cza de 8 bits em 256 tons de cinza
plt.imshow(conv_img, plt.cm.gray)
```
    <matplotlib.image.AxesImage at 0x210c94bfbe0>
    
<figure>
<img src='https://github.com/AlanMarquesRocha/Quantizacao-e-Amostragem-Img-DIgitais/blob/master/imgs/output_25_1.png?raw=true'/>
</figure>     

    
### A quantização levará em consideração a quantidade de bits da imagem original, sendo proporcional aos casos de 4, 32 e 64 tons, ou seja, o número de bits poderá ser calculado a regra abaixo:

```py
# 256(2^n) = 2^8(4) -->
# 2^8(2^n) = 2^8(2^2) -->
# 2^n = 2^2 -> n = 2

# número de bits conforme calculado acima:
n_bit = 2
```
```py
# Encontra-se o valor da camada que será utilizada nas próximas operações.
mk_img = 256 - pow(2, (8 - n_bit))

# mostra o valor encontrado para mk_img:
mk_img
```
    192

### Nessa etapa deve-se criar uma matriz que servirá para preencher a imagem original ``img_cza`` por meio de ``mk_img`` 

```py
# Criando a matriz do mesmo tramanho da imagem img_cza:
mtx_ones = np.ones_like(conv_img)

# Fazendo o produto de mk_img e mtx_ones para a criação da máscara:
mtx_mk = mtx_ones * mk_img

# Mostrando a matriz resultante:

type(mtx_mk)
mtx_mk
```
    array([[192, 192, 192, ..., 192, 192, 192],
           [192, 192, 192, ..., 192, 192, 192],
           [192, 192, 192, ..., 192, 192, 192],
           ...,
           [192, 192, 192, ..., 192, 192, 192],
           [192, 192, 192, ..., 192, 192, 192],
           [192, 192, 192, ..., 192, 192, 192]], dtype=uint8)

### Realizando a operação AND para verificação de ``img_cza e mtx_mk`` 

```py
# Operação AND entre k e mtx_mk
mtx_and = conv_img & mtx_mk

# Mostrando o tipo da variável mtx_and
type(mtx_and)

# Mostrando a matriz resultante (mtx_and):
mtx_and_mk)
mtx_mk
```

    array([[128,  64,   0, ...,  64,  64,  64],
           [128, 128,  64, ...,  64,  64,  64],
           [192, 128, 128, ...,  64,  64,  64],
           ...,
           [128, 128, 128, ...,   0,   0,   0],
           [128, 128, 128, ...,   0,   0,   0],
           [128, 128, 128, ...,   0,   0,   0]], dtype=uint8)


### É necessário criar uma variável que servirá como referência para a obtenção dos valoriza quantizados da imagem ``img_cza`` em 4 tons.

```py
# Criando a variável d_bits que representa o deslocamento dos pixels para a quantização da imagem em 04 tons.
d_bits = 8 - n_bit

type(d_bits)

d_bits
```
    6

```py
# Desloca d_bits para a direita, obtendo-se os valores quantizados na imagem img_t4:
img_t4 = mtx_and >> d_bits

type(img_t4)

# Array que representa a imagem img_t4 quantizada em 04 tons.
img_t4
```
    array([[74, 52, 31, ..., 60, 58, 59],
           [86, 70, 57, ..., 59, 58, 58],
           [97, 89, 82, ..., 60, 58, 57],
           ...,
           [86, 86, 85, ...,  0,  0,  0],
           [86, 85, 84, ...,  0,  0,  0],
           [85, 84, 83, ...,  0,  0,  0]], dtype=uint8)

## Quantização da intensidade dos pixels da imagem para 32 tons,

```py
# 256(2^n) = 2^8(32) =
# 2^8(2^n) = 2^8(2^5) =
# 2^n = 2^5 -> n = 5

# Para a quantização da intensidae da imagem em 32 tons, teremos n_bit = 5
n_bit = 5
```
```py
# Encontra-se o valor da camada que será utilizada nas próximas operações.
mk_img = 256 - pow(2,(8-n_bit))

# mostra o valor encontrado para mk_img:
mk_img
```
    248
    
```py
# Criando a matriz do mesmo tramanho da imagem img_cza:
mtx_ones = np.ones_like(conv_img)

# Fazendo o produto de mk_img e mtx_ones para a criação da máscara:
mtx_mk = mtx_ones * mk_img

# Mostrando a matriz resultante:
type(mtx_mk)

mtx_mk
```    
    array([[248, 248, 248, ..., 248, 248, 248],
           [248, 248, 248, ..., 248, 248, 248],
           [248, 248, 248, ..., 248, 248, 248],
           ...,
           [248, 248, 248, ..., 248, 248, 248],
           [248, 248, 248, ..., 248, 248, 248],
           [248, 248, 248, ..., 248, 248, 248]], dtype=uint8)

### Realizando a operação AND para verificação de ``img_cza e mtx_mk`` 

```py
# Operação AND entre k e mtx_mk
mtx_and = conv_img & mtx_mk

# Mostrando o tipo da variável mtx_and
type(mtx_and)

# Mostrando a matriz resultante (mtx_and):
mtx_and
```  
    array([[144, 104,  56, ..., 120, 112, 112],
           [168, 136, 112, ..., 112, 112, 112],
           [192, 176, 160, ..., 120, 112, 112],
           ...,
           [168, 168, 168, ...,   0,   0,   0],
           [168, 168, 168, ...,   0,   0,   0],
           [168, 168, 160, ...,   0,   0,   0]], dtype=uint8)

### É necessário criar uma variável que servirá como referência para a obtenção dos valoriza quantizados da imagem ``img_cza`` em 32 tons.

```py
# Criando a variável d_bits que representa o deslocamento dos pixels 
# para a quantização da imagem em 32 tons.
d_bits = 8 - n_bit

type(d_bits)

d_bits
``` 
    3

```py
# Desloca d_bits para a direita, obtendo-se os valores quantizados na imagem img_t32:
img_t32 = mtx_and >> d_bits

type(img_t32)

# Array que representa a imagem img_t4 quantizada em 32 tons.
img_t32
``` 
    array([[18, 13,  7, ..., 15, 14, 14],
           [21, 17, 14, ..., 14, 14, 14],
           [24, 22, 20, ..., 15, 14, 14],
           ...,
           [21, 21, 21, ...,  0,  0,  0],
           [21, 21, 21, ...,  0,  0,  0],
           [21, 21, 20, ...,  0,  0,  0]], dtype=uint8)

## Quantização da intensidade dos pixels da imagem para 128 tons,

```py
# 256(2^n) = 2^8(128) =
# 2^8(2^n) = 2^8(2^7) =
# 2^n = 2^7 -> n = 7

# Para a quantização da intensidae da imagem em 32 tons, teremos n_bit = 5
n_bit = 7
``` 
```py
# Encontra-se o valor da camada que será utilizada nas próximas operações.
mk_img = 256 - pow(2,(8-n_bit))

# mostra o valor encontrado para mk_img:
mk_img
``` 
    254

```py
# Criando a matriz do mesmo tramanho da imagem img_cza:
mtx_ones = np.ones_like(conv_img)

# Fazendo o produto de mk_img e mtx_ones para a criação da máscara:
mtx_mk = mtx_ones * mk_img

# Mostrando a matriz resultante:
type(mtx_mk)

mtx_mk
``` 
    array([[254, 254, 254, ..., 254, 254, 254],
           [254, 254, 254, ..., 254, 254, 254],
           [254, 254, 254, ..., 254, 254, 254],
           ...,
           [254, 254, 254, ..., 254, 254, 254],
           [254, 254, 254, ..., 254, 254, 254],
           [254, 254, 254, ..., 254, 254, 254]], dtype=uint8)

### Realizando a operação AND para verificação de ``img_cza e mtx_mk`` 

```py
# Operação AND entre k e mtx_mk
mtx_and = conv_img & mtx_mk

# Mostrando o tipo da variável mtx_and
type(mtx_and)

# Mostrando a matriz resultante (mtx_and):
mtx_and
```

    array([[148, 104,  62, ..., 120, 116, 118],
           [172, 140, 114, ..., 118, 116, 116],
           [194, 178, 164, ..., 120, 116, 114],
           ...,
           [172, 172, 170, ...,   0,   0,   0],
           [172, 170, 168, ...,   0,   0,   0],
           [170, 168, 166, ...,   0,   0,   0]], dtype=uint8)

### É necessário criar uma variável que servirá como referência para a obtenção dos valoriza quantizados da imagem ``img_cza`` em 128 tons.

```py
# Criando a variável d_bits que representa o deslocamento dos pixels 
# para a quantização da imagem em 32 tons.
d_bits = 8 - n_bit

type(d_bits)

d_bits
```
    1

```py
# Desloca d_bits para a direita, obtendo-se os valores quantizados na imagem img_t4:
img_t128 = mtx_and >> d_bits

type(img_t128)

# Array que representa a imagem img_t4 quantizada em 32 tons.
img_t128
```
    array([[74, 52, 31, ..., 60, 58, 59],
           [86, 70, 57, ..., 59, 58, 58],
           [97, 89, 82, ..., 60, 58, 57],
           ...,
           [86, 86, 85, ...,  0,  0,  0],
           [86, 85, 84, ...,  0,  0,  0],
           [85, 84, 83, ...,  0,  0,  0]], dtype=uint8)


### Mostrando o resultado das imagens quantizadas em 4, 32 e 128 tons.

```py
# PLota as duas imagens img_cza e img_c1:
fig, (ax1, ax2) = plt.subplots(1, 2, figsize = (9,9), gridspec_kw = {'hspace': 0.3})

# Carrega a imagem img_cza e informa o título por meio da função set_title
ax1.imshow(conv_img, plt.cm.gray) 
ax1.set_title('Imagem convertida em unit8')

# Carrega a imagem img_c1 e informa o título por meio da função set_title
ax2.imshow(img_t4, plt.cm.gray)
ax2.set_title('Imagem quantizada em 04 tons')

# PLota as duas imagens img_cza e img_c1:
fig, (ax3, ax4) = plt.subplots(1, 2, figsize = (9,9), gridspec_kw = {'hspace': 0.3})

# Carrega a imagem img_c2 e informa o título por meio da função set_title
ax3.imshow(img_t32, plt.cm.gray) 
ax3.set_title('Imagem quantizada em 32 tons')

# Carrega a imagem img_c3 e informa o título por meio da função set_title
ax4.imshow(img_t128, plt.cm.gray)
ax4.set_title('Imagem quantizada em 128 tons')
```
    Text(0.5, 1.0, 'Imagem quantizada em 128 tons')


<figure>
<img src='https://github.com/AlanMarquesRocha/Quantizacao-e-Amostragem-Img-DIgitais/blob/master/imgs/output_55_1.png?raw=true'/>
</figure>    

<figure>
<img src='https://github.com/AlanMarquesRocha/Quantizacao-e-Amostragem-Img-DIgitais/blob/master/imgs/output_55_2.png?raw=true'/>
</figure>  
        
---
