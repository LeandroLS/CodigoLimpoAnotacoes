# Anotações do Livro Código Limpo 📖
Esse repositório passagens interessantes que achei no livro Código Limpo do autor Robert Cecil Martin.

## Código Limpo
### A Regra do Escoteiro
Deixe a área do acampamento mais limpa do que como você a encontrou.
A ideia é deixar o código mais limpo do que quando começamos. A limpeza não precisa ser algo grande. Pode ser algo como a troca de nome de uma variável por um melhor, dividir uma função que tem muitas responsabilidades, remover instrução if aninhada e etc.

## Nomes Significativos
### Use Nomes que Revelem seu Propósito
Escolher bons nomes leva tempo, mas economiza mais. Portanto, cuide de seus nome e troque-os quando encontrar melhores. 
O nome de uma variável, função ou classe deve responder a todas as grandes questões. Deve lhe dizer porque existe, o que faz e como é usado. Se um nome requer um comentário, então ele não revela seu propósito.

## Evite Informações Erradas
Devemos evitar palavras cujos significados podem se desviar daquele que desejamos.
Não se refira a um grupo de conta como accountArray a menos que realmente seja um Array. A palavra Array significa algo específico para programadores. Se o que armazena as contas não for um Array de verdade, poderá confundir os outros.

## Nomes de Classes
Nomes de classes devem ser substantivo(s) e não devem ser palavras de verbo.

## Nomes de Métodos
Nomes de métodos devem ter verbos, como Post Payment, Delete Page ou Save.

## Selecione uma Palavra por Conceito
Por exemplo, é confuso ter fetch(), get(), retrieve() como métodos equivalentes de classes diferentes. Mantenha um padrão pra esses nomes.

## Adicione um Contexto Significativo
Imagine que você tenha as seguintes variáveis, firstname, lastName, street, houseNumber, city, state e zipCode. Vendo essas variáveis juntas, fica claro que elas formam um endereço. Mas e se você visse uma dessas variáveis sozinhas num método ? Você iria assimilar que faz parte de um endereço ?

Podemos usar prefixos para adicionar um contexto, por exemplo: addrStatate, addrStreet e etc. Pelo menos os leitores entenderão que essas variáveis são parte de uma estrutura maior. Mas a melhor solução seria criar uma classe chamada Adress com as propriedades de um endereço.

## Funções
### Pequenas
Funções devem ser pequenas

### Faça Apenas uma Coisa
As funções devem fazer uma coisa. Devem fazê-la bem. Devem fazer apenas ela.

### Ler o código de Cima para Baixo
Queremos que o código seja lido de cima para baixo, como uma narrativa. Desejamos que cada função seja seguida pelas outras no próximo nível de abstração de modo que possamos ler o programa descendo um nível de abstração de cada vez conforme percorremos a lista de funções.

### Parâmetros de Funções
A quantidade ideal de parâmetros para uma função é zero. Um a dois parâmetros é aceitável. Devemos evitar sempre que puder três parâmetros. Quatro parâmetros não devem ser usados. 

### Evite Efeitos Colaterais
Efeitos colaterais são mentiras. Sua função promete fazer apenas uma coisa, mas ela também faz outras coisas escondidas. Considere essa função:

    function checkPassword(user, password){
        if(user.password == password){
            session.start();
            return true;
        } else {
            return false;
        }
    }

O efeito colateral dessa função está em session.start(), essa função deveria apenas checar a senha do usuário, não iniciar a sessão. Se iniciar a sessão realmente for necessário, a função deveria ser renomeada para checkPassowrdAndStartSessio(), embora isso violaria a regra de "fazer apenas uma coisa".

## Comentários
Comentários é o resultado da nossa incapacidade de escrever um código expressivo.  Um código que não precise de comentários para entende-lo. Toda vez que você pensar em criar um comentário, pense bem e veja se não consegue expressar aquela ideia de comentário no código em si.

### Explique-se no código
Ruim: 

    //verifica se o usuário é admin
    if(employe.rule_id == 1 && employe.group_id == 1){}
    
Bom:

    if(emplye.isAdmin){}

### Murmúrio
Se optar por criar um comentário, então gaste o tempo necessário para fazê-lo bem feito.

### Código como comentários
Poucas práticas são tão condenáveis quanto colocar o código como comentário. Não faça isso!
Exemplo:

    public function index(){
        var a = 1;
        var b = 2;    
        return a + b;
       //return (a - 2) + b;
    }

Outros que verão esse código, não terão coragem de excluir os comentários. Eles achariam que estão lá por algum motivo e são importante demais para serem apagados.

## Formatação
### Espaçamento vertical entre conceitos
Quase todo código é lido da esquerda pra direita e de cima para baixo. Cada linha representam uma expressão ou uma estrutura, e cada grupo de linhas representa um pensamento completo. Esses pensamentos devem ficar separados por linhas em branco.

Exemplo:

Ruim:

    public function getUserData(){
        return this.user.data;
    }
    public function logout(){
        this.user.logout();
    }

Bom:

    public function getUserData(){
        return this.user.data;
    }

    public function logout(){
        this.user.logout();
    }

### Distância vertical
Os conceitos intimamente relacionados deve ficar juntos verticalmente. 
Para os conceitos que são tão intimamente relacionados e que estão no mesmo arquivo-fonte, a separação vertical deles deve ser uma medida do quão importante eles são para a integibilidade um do outros.

Declaração de variáveis. Deve-se declarar as variáveis o mais próximo possível de onde serão usadas. 

Funções dependentes. 


## Tratamento de Erro
### Não retorne null
Uma das coisas que fazemos que levam a erros é o retorno de null
Se você ficar tentado a retornar null em um método, em vez disso, considere lançar uma exceção. 

### Não Passe null
Retornar null dos métodos é ruim, mas passar null pra eles é pior. Você deve evitar passá-lo em seu código sempre que possível.

### Classes
As classes devem ser pequenas
As classes devem ser pequenas. Mas o que é uma classe pequena ? Pra medir se uma classe é pequena ou não, você deve observar se ela está com muitas responsabilidades. 
O nome de uma classe deve descrever quais responsabilidades ela faz. Selecionar um nome é a primeira forma de ajudar determinar o tamanho da classe. Se derivarmos um nome conciso pra ela, então provavelmente ela ficará grande. 

## Emergência
### Efetue todos os testes
Um sistema pode ter um projeto perfeito no papel, mas se não há uma maneira simples de verificar se ele realmente funciona como planejado, então o que está escrito é dubitável. Os sistemas que não podem ser testados não podem ser verificados.

### Sem repetição de código
A repetição de código é o inimigo principal para um sistema bem desenvolvido. Ela representa trabalho, ricos e complexidade desnecessária. A duplicação se apresenta de várias formas.

### Expressividade
Escrever códigos que nós entendamos é fácil, pois quando fazemos, possuímos um conhecimento profundo do problema que desejamos resolver. Mas outras pessoas que pegarem esse mesmo código não terão esse mesmo grau de conhecimento.
Quanto mais claro o autor tornar seu código, menos tempo outras pessoas terão de gastar para compreendê-lo. 
Você pode se expressar melhor através da escolha de bons nomes. 
Você pode se expressar melhor mantendo pequenas  suas classes e funções.

### Múltiplas linguagens em um arquivo fonte
Os ambientes modernos de programação atuais possibilitam colocar muitas linguagens distintas em um único arquivo fonte. Na melhor das hipóteses, isso é confuso, e na pior, negligentemente desleixado.
O ideal para um arquivo fonte é ter uma, apenas uma, linguagem. Mas na vida real, provavelmente teremos de usar mais de uma. Devido a isso, devemos minimizar tanto a quantidade como o uso de linguagens extras em nossos arquivos-fonte.

### Seguranças Anuladas
Chernobyl derreteu porque o gerente da planta anulou cada um dos mecanismos de segurança, uma a um. Os dispositivos de segurança estavam tornando inconveniente a execução de um experimento. O resultado era que o experimento não executava,  e o mundo viu a maior catástrofe civil nuclear.
É arriscado anular as seguranças. Desabilitar certos avisos (ou todos!) do compilador talvez ajude a fazer a compilação funcioanr com êxito, mas com o risco de infindáveis sessões de depuração. Desabilitar os testes de falhar e dizer a si mesmo que os aplicará depois é tão ruim quanto fingir que seus cartões de crédito sejam dinheiro gratuito.

### Parâmetros seletores
Dificilmente há algo mais abominável do que um parâmetro false pendurado no final da chamada de uma função. O que ele significa ? O que mudaria se ele fosse true ? Não bastava ser difícil lembrar o propósito de uma parâmetro seletor, cada um agrupo muitas funções em uma única. Os parâmetros seletores são uma maneira preguiçosa de não ter de dividir uma função grande em várias outras menores.

### Siga as convenções Padrões
Cada equipe deve seguir um padrão de programação  baseando-se nas normas comuns do mercado. Esse padrão deve especificar coisas como onde declarar variáveis de instâncias; como nomear classes, métodos e variáveis; onde colocar as chaves; e assim por diante. A equipe não deve precisar de um documento que descreva essas convenções porque seus código fornecem os exemplos.
Cada membro da equipe deve seguir essas convenções. Isso significa que cada um deve ser maduro o suficiente para entender que não importa onde você coloque suas chaves contanto que todos concordem onde colocá-las.

### Substitua os números mágicos por constantes com nomes
Essa é provavelmente uma das regras mais antigas em desenvolvimento de software. De modo geral, é uma péssima ideia ter números soltos em seu código, deve-se escondê-los em constantes com nomes bem selecionados.
Por exemplo, o número 86.400 deve ficar escondido na constante SECONDS_PER_DAY. Se você for imprimir 55 linhas por página, então a constante 55 deve ficar na constante LINES_PER_PAGE.

### Seja Preciso
Quando você toma uma decisão em seu código, certifique-se de fazê-la precisamente. Saiba porque a tomou e como você lidará com quaisquer exceções. Não seja desleixado com precisão de suas decisões. Se chamar uma função que retorne null, certifique-se de verificar por null. Se for consultar o que você acha ser o único registro no bancode dados, garanta que seu código verifique se não há outros

### Evite condicionais negativos
É um pouco mais difícil entender condições negativas do que afirmativas. Portanto, sempre que possível, use condicionais afirmativas. Por exemplo:

    if(buffer.shoudCompact())

É melhor que:

    if(!buffer.shouldNotCompact())

### Encapsule as condições de limites
Condições de limite são difíceis de acompanhar. Coloque o processamento para elas em um único lugar. Não as deixe espalhadas pelo código. Não queremos um enxame de +1 e -1 aparecendo pelo código. Considere o exemplo:

    if(level + 1 < tags.length){
        parts = new Parse(body, tags, level + 1, offset + endTag);
        body = null;
    }
    
Note que 'level +1' aparece duas vezes. Essa é uma condição de limite que deveria estar encapsulada dentro de uma variável com um nome ou algo como 'nextLevel'

    int nextLevel = level + 1;
    if(nextLevel < tags.length){
         parts =  new Parse(body, tags, level + 1, offset + endTag);
         body = null;
     }

### Use nomes longos para escopos grandes
O comprimento de um nome deve estar relacionado com o do escopo. Você pode usar nomes de variáveis muitos curtos para escopos minúsculos. Mas para escopos grandes, devem-se usar nomes extensos.

### Teste abundantemente bugs próximos
Bugs tendem a se reunir. Quando encontrar um bug numa função, é sábio fazer um teste exaustivo nela. Provavelmente você verá que o bug não estava só. 


