
# Introdução à Programação oo em Java

## Tipos de relações entre objetos

- **Associação:** é a relação mais fraca e se refere a objetos que consomem serviços ou funcionalidades de outros. Ela pode ocorrer mesmo quando nenhuma classe possui a outra e cada objeto instanciado tem sua existência independente do outro. Essa relação pode ocorrer com cardinalidade “um para um”, “um para vários”, “vários para um” e “vários para vários”.
- **Agregação:** ocorre entre dois ou mais objetos, com cada um tendo seu próprio ciclo de vida, mas com um objeto (pai) contendo os demais (filhos). Precisamos compreender que, nesse caso, os objetos filhos podem sobreviver à destruição do objeto pai.
- **Composição:** ocorre quando há uma relação de dependência entre o(s) filho(s) e o objeto pai. Caso o pai deixe de existir, necessariamente o filho será destruído.

## O que é referência?

É o endereço na memória do computador que aponta para um objeto. Em vez de guardar o objeto inteiro em uma variável, o programa guarda um "atalho" ou "ponteiro".

## Mecanismos de visibilidade

- **Default:** visibilidade restrita ao pacote do Java.
- **Private**
- **Public**
- **Protected:** restrita ao pacote e a todas as subclasses.