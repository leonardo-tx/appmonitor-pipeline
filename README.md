# AppMonitor

O projeto nesse repositório é referente ao trabalho
final (Assessment) desenvolvido na disciplina de 
**Pipelines de CI/CD e DevOps**.

## Papel do Git na Entrega Contínua

O Git como ferramenta, facilita bastante a Entrega Contínua 
(CD - Continuos Delivery), sendo a sua principal funcionalidade o 
controle de versionamento, podendo ser criado ramificações do código 
com as branches, permitindo que múltiplos desenvolvedores trabalhem 
em funcionalidades diferentes de maneira assíncrona, isso abre espaço
para um processo ágil e seguro, o que é um dos pilares do CD.

Outro ponto que o Git possui é a possibilidade de fazer uma reversão 
do projeto para um ponto estável quando há algum erro, já que 
justamente o Git possui um histórico de todas as mudanças feitas em 
um repositório, o que também ajuda a agilizar e melhorar a confiabilidade
da Entrega Contínua.

## Importância do branch

O branch tem como principal função isolar partes do desenvolvimento de
um projeto / repositório, permitindo que seja possível trabalhar em
funcionalidades sem alterar o projeto principal que se encontra na branch
principal, funcionando como ramificações.

Em um mesmo projeto pode existir diversas ramificações, cada uma podendo
ser trabalhada assíncronamente por um ou mais desenvolvedores, caso uma
ramificação esteja pronta para ser adicionada à ramificação principal,
é possível fazer a mesclagem para a ramificação principal, caso não seja
mais necessário, pode ser deletado e assim por diante.

Sem as branches, esse isolamento não existiria, o que resultaria em uma
dificuldade maior de testagem de funcionalidades e controle.

Por esses motivos, as branches são essenciais no desenvolvimento, principalmente
em equipe.

## Importância da tag

As tags possuem como funcionalidade registrar um momento do código / projeto,
sendo dividida em versões que são incrementadas ao longo do tempo.

Isso ajuda na organização, já que versões novas podem conter correções de bugs ou
a adição de novas funcionalidades, caso haja um problema com uma versão nova,
é possível descobrir com mais facilidade o que causou o erro.

Tags são bastante utilizadas, tanto em bibliotecas quanto em projetos, sendo fundamental
para registrar os incrementos de um projeto.

## Diferenças entre Variáveis de Repositório, Segredos de Repositório e Variáveis de Ambiente

- Variável de Ambiente (env): Diferente dos *vars* e *secrets*, a variável de um *env* é 
declarada no arquivo do workflow, podendo ser passado em diferentes contextos, no global, 
no job e no step, cada um representando escopos diferentes. Para utiliza-la, é possível
resgatar o valor com $VARIAVEL dentro de um run bash por exemplo ou com uma expressão
de contexto ${{ env.NAME }} que pode ser usado em qualquer lugar, desde que esteja 
no mesmo escopo que o *env*. É possível passar um valor de *vars* ou do *secrets* para 
uma variável *env*.

- Variável de Repositório (vars): O *vars* assim como o *secrets*, são declarados nas
configurações de segredos e variáveis do Github, só que diferente do *secrets*, o *vars*
é utilizado para armazenar valores que são públicos e não confidenciais. Para utiliza-la,
é possível resgatar o valor apenas com a expressão de contexto ${{ vars.NAME }}.

- Segredo de Repositório (secrets): O *secrets* assim como o *vars*, são declarados nas
configurações de segredos e variáveis do Github, só que diferente do *vars*, o *secrets*
é utilizado para armazenar dados sensíveis, como chave da API e credenciais por exemplo,
já que os dados na execução do workflow não são mostrados no log. Para utiliza-la, é
possível resgatar o valor apenas com a expressão de contexto ${{ secrets.NAME }}.
