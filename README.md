# Projeto de sub-amostragem e quantização de imagens digitais

### **Realizando a importação das bibliotecas necessárias para o projeto**:

### **Importando a imagem utilizada no projeto diretamente da biblioteca skimage.data**

### **È necessário verificar as dimensões da imagem, assim como mostrá-la para verificar se a importação funcionou sem erros.**

    (512, 512, 3)

    Text(0.5, 1.0, 'Imagem original')
    
![png](output_7_1.png)
    
### **Para fazer a amostragem da img_data, primeiro é necessário transformá-la em níveis de cinza.**

**A conversão da imagem foi feita ultilizando a biblioteca matplotlib.**

Podemos converter a imagem em tons de cinza usando o padrão RGB para a equação de conversão em tons de cinza mostrada na célula abaixo

Podemos implementar este método usando a biblioteca ``Matplotlib``. primeiro precisamos ler a imagem e em seguida, obter as arrays de dimensão vermelha (R), verde (G) e azul (B) da imagem. 

Após obter as arrays podemos aplicar a equação abaixo para obter a imagem em tons de cinza. Precisamos multiplicar as arrays completas com os valores dados na fórmula para obter a imagem em tons de cinza.

    Text(0.5, 1.0, 'Imagem original em níveis de cinza')

![png](output_10_1.png)
    
## **Nesta etapa serão produzidas 03 (três) imagens decorrentes da sub-amostragem de ``img_data`` em 50%, 25% e 12,5%.**

### **Sub-amostragem da imagem ``img_data`` em 50%**

    (512, 512, 3)

    (256, 256)

### **Sub-amostragem da imagem ``img_data`` em 25%**

### Existem duas possibilidades

- 1ª - Pega-se a imagem sub-amostrada em 50% e utiliza o mesmo raciocínio da sub-amostragem da ``img_data`` para ``img_c1``

- 2ª Pega-se um pixel, intercalando-se outros 03 (três), utilizando apenas 25% da imagem original (``ìmg_data``)

    (512, 512, 3)

    (128, 128)

    (128, 128)


### **Sub-amostragem da imagem ``img_data`` em 12,5%**

### Também é possível utilizar as duas possibilidades mostradas nos casos acima, porém o foco ficará apenas na sub-amostragem da imagem original (``img_data`` para a imagem ``ìmg_c3`` que representa a sub-amostragem em 12,5%.

    (64, 64)

### **Mostrando o resuldado das sub-amostragens de 50%, 25% e 12,5%.**

    Text(0.5, 1.0, 'Sub-amostragem em 12,5%')

![png](output_22_1.png)
    
![png](output_22_2.png)
    
# Nessa sessão serão produzidas três imagens reduzindo a quantização da intensidade dos pixels da imagem original para 4, 32 e 64 bits.

## Quantização da intensidade dos pixels da imagem para 04 tons,

    <matplotlib.image.AxesImage at 0x210c94bfbe0>

![png](output_25_1.png)
    
### A quantização levará em consideração a quantidade de bits da imagem original, sendo proporcional aos casos de 4, 32 e 64 tons, ou seja, o número de bits poderá ser calculado a regra abaixo:

    192

### Nessa etapa deve-se criar uma matriz que servirá para preencher a imagem original ``img_cza`` por meio de ``mk_img`` 

    array([[192, 192, 192, ..., 192, 192, 192],
           [192, 192, 192, ..., 192, 192, 192],
           [192, 192, 192, ..., 192, 192, 192],
           ...,
           [192, 192, 192, ..., 192, 192, 192],
           [192, 192, 192, ..., 192, 192, 192],
           [192, 192, 192, ..., 192, 192, 192]], dtype=uint8)

### Realizando a operação AND para verificação de ``img_cza e mtx_mk`` 

    array([[128,  64,   0, ...,  64,  64,  64],
           [128, 128,  64, ...,  64,  64,  64],
           [192, 128, 128, ...,  64,  64,  64],
           ...,
           [128, 128, 128, ...,   0,   0,   0],
           [128, 128, 128, ...,   0,   0,   0],
           [128, 128, 128, ...,   0,   0,   0]], dtype=uint8)


### É necessário criar uma variável que servirá como referência para a obtenção dos valoriza quantizados da imagem ``img_cza`` em 4 tons.

    6

    array([[74, 52, 31, ..., 60, 58, 59],
           [86, 70, 57, ..., 59, 58, 58],
           [97, 89, 82, ..., 60, 58, 57],
           ...,
           [86, 86, 85, ...,  0,  0,  0],
           [86, 85, 84, ...,  0,  0,  0],
           [85, 84, 83, ...,  0,  0,  0]], dtype=uint8)

## Quantização da intensidade dos pixels da imagem para 32 tons,

    248
    
    array([[248, 248, 248, ..., 248, 248, 248],
           [248, 248, 248, ..., 248, 248, 248],
           [248, 248, 248, ..., 248, 248, 248],
           ...,
           [248, 248, 248, ..., 248, 248, 248],
           [248, 248, 248, ..., 248, 248, 248],
           [248, 248, 248, ..., 248, 248, 248]], dtype=uint8)

### Realizando a operação AND para verificação de ``img_cza e mtx_mk`` 


    array([[144, 104,  56, ..., 120, 112, 112],
           [168, 136, 112, ..., 112, 112, 112],
           [192, 176, 160, ..., 120, 112, 112],
           ...,
           [168, 168, 168, ...,   0,   0,   0],
           [168, 168, 168, ...,   0,   0,   0],
           [168, 168, 160, ...,   0,   0,   0]], dtype=uint8)



### É necessário criar uma variável que servirá como referência para a obtenção dos valoriza quantizados da imagem ``img_cza`` em 32 tons.




    3






    array([[18, 13,  7, ..., 15, 14, 14],
           [21, 17, 14, ..., 14, 14, 14],
           [24, 22, 20, ..., 15, 14, 14],
           ...,
           [21, 21, 21, ...,  0,  0,  0],
           [21, 21, 21, ...,  0,  0,  0],
           [21, 21, 20, ...,  0,  0,  0]], dtype=uint8)



## Quantização da intensidade dos pixels da imagem para 128 tons,

    254

    array([[254, 254, 254, ..., 254, 254, 254],
           [254, 254, 254, ..., 254, 254, 254],
           [254, 254, 254, ..., 254, 254, 254],
           ...,
           [254, 254, 254, ..., 254, 254, 254],
           [254, 254, 254, ..., 254, 254, 254],
           [254, 254, 254, ..., 254, 254, 254]], dtype=uint8)

### Realizando a operação AND para verificação de ``img_cza e mtx_mk`` 


    array([[148, 104,  62, ..., 120, 116, 118],
           [172, 140, 114, ..., 118, 116, 116],
           [194, 178, 164, ..., 120, 116, 114],
           ...,
           [172, 172, 170, ...,   0,   0,   0],
           [172, 170, 168, ...,   0,   0,   0],
           [170, 168, 166, ...,   0,   0,   0]], dtype=uint8)

### É necessário criar uma variável que servirá como referência para a obtenção dos valoriza quantizados da imagem ``img_cza`` em 128 tons.

    1

    array([[74, 52, 31, ..., 60, 58, 59],
           [86, 70, 57, ..., 59, 58, 58],
           [97, 89, 82, ..., 60, 58, 57],
           ...,
           [86, 86, 85, ...,  0,  0,  0],
           [86, 85, 84, ...,  0,  0,  0],
           [85, 84, 83, ...,  0,  0,  0]], dtype=uint8)


### Mostrando o resultado das imagens quantizadas em 4, 32 e 128 tons.

    Text(0.5, 1.0, 'Imagem quantizada em 128 tons')


![png](output_55_1.png)
        
![png](output_55_2.png)
    

