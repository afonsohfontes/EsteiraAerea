# Manual Técnico do Transportador Power And Free e seu Supervisório

Esse documento trata-se de um manual técnico, onde nele você pode encontrar algumas informações sobre a Linha de Transporte Aéreo do  Laboratório de Sistemas de Automação (L-04) na Unifor. Dentre tais informações, encontram-se informações técnicas dos componentes, informações de segurança dos componentes, como manusear a bancada e como manusear o supervisório.

# Índice

1.	Introdução
2.	Manuseio da Bancada
3.	Manuseio do Supervisório
4.	Desenvolvimento
5.	Conclusão

# 1. Introdução

O objeto de estudo trata-se de uma linha de transporte aéreo Power and Free (foto 1 - planta do transportador). Os transportadores Power e Free também são chamados de transportadores assíncronos. Este tipo de transportador consiste em um sistema de duas pistas (foto 2 - duas pista do transportador) e é considerado assíncrono devido ao fato de que as cargas penduradas no carrinho (foto 3 - carrinho) podem se mover em dois ritmos diferentes. Além disso, as cargas podem ser programadas para parar e iniciar de forma independente, quando as travas são acionadas (foto 4 - carrinho + trava) ou para alterar as trilhos quando necessário (foto 5 - desvio).

O nome power e free vem da configuração única da pista. Há uma corrente ligada em uma pista motorizada (foto 6 - motor) e ao lado dela há carrinhos que correm livremente em uma outra pista. Na pista motorizada, pode-se encontrar os cachorros, estrutura responsável por movimentar os carrinhos (foto 7 - cachorro) (foto 8 - carrinho + cachorro). (https://www.youtube.com/watch?v=rih_SJqUuIA)

O acionamento da trava e do desvio é feito de forma pneumática utilizando eletroválvulas 5/2 vias (foto 9 - válvula pneumática) e cilindros de dupla ação (foto 10 - cilindro pneumático). Além disso, existem algumas chaves de fim de curso espalhadas na linha de transpote aéreo (foto 11 - chave de fim de curso). Elas, quando acionadas, mandam sinal para o CLP que controla todo o transportador (foto 12 - interior da bancada/CLP). Através desse sinal, pode-se saber aonde estão os carrinhos ou implementar um contador e ter um controle da produção.

# 2. Manuseio da Bancada

Como mostrado na foto anterior, o CLP fica no interior de uma bancada (foto 13 - bancada de comando). É através dessa bancada que o usuário pode controlar as travas e os desvios, ligar e desligar o sistema, selecionar entre manual e automático, resetar falhas ou acionar uma parade emergência em casos mais extremos.

Para abrir ou fechar as travas, primeiro você seleciona a trava através de uma chave seletora e acompanha nas luzes acima, qual trava está selecionada. Após selecionar a trava desejada, apertar nos botões abrir trava ou fechar trava. Para mudar os sentidos dos desvios, tem duas chaves com trava, uma para cada desvio. A posição do desvio depende da posição da chave. O mesmo serve para selecionar entre manual e automático, depende da posição da chave. Para ligar e desligar o sistema, basta pressionar os botões liga sistema ou desliga sistema. O mesmo serve para resetar falhas, basta pressionar o botão reset falhas.

Além disso, existem algumas luzes que são acionadas dependendo de algumas mudanças feitas na bancada ou na esteira. Para habilitar o uso da bancada e do sistema é necessário ligar a chave geral, localizada na parte lateral esquerda da mesa de comando (foto 14 - chave geral). Depois deve ser acionado o disjuntor (foto 15 - disjuntor do inversor de frequência) do inversor de frequência (foto 16 - inversor de frequência), este é responsável por controlar o motor. Por último ligar o quarto disjuntor unipolar (foto 17 - conjunto de disjuntores), responsável por liberar energia para as luzes, chaves e botões da bancada. Ao finalizar o uso da bancada, o usuário deve desacionar os componentes supracitados, na ordem inversa. Primeiro, o quarto disjuntor unipolar. Depois, o disjuntor do do inversor de frequência. E por último, a chave geral.

# 3. Manuseio do Supervisório

O manuseio do supervisório é bem mais simples, a primeira tela é apenas uma tela de login, onde é informado usuário e senha. Caso o usuário se logue, será redirecionado a outra tela. Nessa segunda tela, vemos a planta da linha de transporte aéreo (foto 18 - layout do supervisório). Para realizar a abertura de alguma válvula basta clicar no retângulo à esquerda de onde a válvula está representada no supervisório. Para o fechamento, basta clicar no retângulo à direita de onde a válvula está representada no supervisório. As lâmpadas da bancada também estão representadas no supervisório, para que o usuário possa acompanhar em tempo real, o que ocorre na bancada.

# 4. Desenvolvimento

Para denselvolver o projeto, foram necessários os seguintes softwares: RSLinx, RSLogix, Elipse Software e além desses, foi necessário instalar os drivers para o conversor DB-9/USB (os instaladores encontram-se nessa pasta do GitHub, assim como os drivers do conversor). Depois de instalar todos os softwares, deve-se abrir o RSLinx e seguir o passo-a-passo descrito nesse tutorial (https://www.youtube.com/watch?v=nk5KzV3UXA0).


Após o RSLinx configurado, incluir o driver DF-1 no elipse e colocá-lo com as mesmas configurações que o RSLinx auto-configurou através da porta COM selecionada (foto 19 - configuração do driver DF-1 no elipse). Como não é possível acionar uma entrada pelo supervisório, é necessário criar um bit em paralelo (foto 20 - inserção do bit auxiliar no código do CLP) ao código do CLP para bypassar o comando vindo da bancada. Dessa forama conseguimos acionar o bit via supervisório e acionar qualquer saída via sistema SCADA (foto 21 - tags e endereços de tags necessários para a comunicação). Para acionar uma saída do supervisório, foi feita uma associação digital com o bit relacionado àquela saída que devemos acionar (foto 22 - associação dos bits entre CLP e SCADA).


# 5. Conclusão

Os pré-requesitos do trabalho foram amplamente solucionados. Para um melhor desenolvimento de um supervisório, faltam apenas escrita em um banco de dados, e consulta no mesmo banco de dados. Dessa forma o usuário pode ter o total controle, supervisão e aqusição de dados da produção/aplicação.
