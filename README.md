# Grupo 1

## Spring Boot
## O que é (Mat)
O Spring Boot é um framework Java open source que fornece suporte abrangente de infraestrutura para o desenvolvimento de aplicativos Java. Tem como objetivo facilitar esse processo em aplicações Java. Consequentemente, ele traz mais agilidade para o processo de desenvolvimento, uma vez que devs conseguem reduzir o tempo gasto com as configurações iniciais.
Em sua essência, o Spring lida com a infraestrutura para que você possa se concentrar em seu aplicativo oferecendo um contêiner, geralmente chamado de contexto do aplicativo Spring, que cria e gerencia os componentes do aplicativo. Esses componentes, ou beans, são conectados dentro do contexto do aplicativo Spring para fazer um aplicativo completo  a nível de produção.

#### Características
- Crie aplicativos Spring independentes
- Incorpore Tomcat, Jetty ou Undertow diretamente (sem necessidade de implantar arquivos WAR);
- Forneça dependências 'starter' opinativas para simplificar sua configuração de compilação;
- Configure automaticamente bibliotecas Spring e de terceiros sempre que possível;
- Forneça recursos prontos para produção, como métricas, verificações de integridade e configuração externa;
- Absolutamente nenhuma geração de código e nenhum requisito para configuração XML.

Portanto, o Spring Boot é uma maneira eficiente e eficaz de criar  uma aplicação em Spring e facilmente colocá-la no ar, funcionando sem depender de um servidor de aplicação.

## Como Funciona Internamente (Mat)
O Spring possui uma arquitetura baseada em interfaces e POJOs (Plain Old Java Objects), oferecendo aos POJOs características como mecanismos de segurança e controle de transações. Esse recurso se aplica ao modelo de programação Java SE e ao Java EE total e parcial. Também facilita testes unitários e surge como uma alternativa à complexidade existente no uso de EJBs. Ademais, Spring codifica padrões de design formalizados como objetos de primeira classe que podemos integrar em nossos próprios aplicativos.

O Spring Framework consiste em recursos organizados em cerca de 21 módulos. Esses módulos são agrupados em 7 grupos: 

#### Core Container
O Core Container consiste nos módulos Core, Beans, Context e Expression Language. 
Dentro do grupo Core Container, estão os módulos responsáveis por conter as partes fundamentais do framework, como as classes básicas e avançadas, suas implementações e controle das definições em tempo de execução das configurações por anotações ou arquivos XML. 

#### Data Access/Integration
A camada Acesso/Integração de Dados consiste nos módulos JDBC, ORM, OXM, JMS e Transação.
O módulo Data Access/Integration é o responsável por prover funcionalidades para transações com o banco de dados. O módulo Web contém os recursos para uma aplicação web, como a implementação do MVC, Web Services REST, entre outros. 

#### Web
O módulo Web do Spring fornece recursos básicos de integração orientados à web, neste contém os recursos para uma aplicação web, como a implementação do MVC, Web Services REST, entre outros. A camada da Web consiste nos módulos Web, Web-Servlet, Web-Struts e Web-Portlet. 
- O módulo Web-Servlet contém a implementação do model-view-controller (MVC) do Spring para aplicativos da web;
- O módulo Web-Struts contém as classes de suporte para integrar uma camada da web Struts clássica em um aplicativo Spring;
- O módulo Web-Portlet fornece a implementação MVC para ser usada em um ambiente de portlet e espelha a funcionalidade do módulo Web-Servlet.

#### Aspect Oriented Programming (AOP)
O módulo AOP fornece a implementação para programação orientada a aspectos, permitindo que você defina, por exemplo, interceptadores de método e pontos de corte para desacoplar de maneira limpa o código que implementa a funcionalidade que deve ser separada.

#### Instrumentation
o módulo Instrumentation fornece suporte a instrumentação de classe e implementações de carregador de classe para serem usados em determinados servidores de aplicativos.

#### Messaging 
O módulo  Messaging contém implementação e suporte para programação baseada em mensagens. 

#### Test
O módulo Test possui o suporte para os testes unitários utilizando JUnit e testes de integração. Todos os módulos citados acima, com exceção do módulo Test, são construídos sobre o Core Container do Spring Framework.

<br>
<p align="center">
  <img src="https://docs.spring.io/spring-framework/docs/4.3.x/spring-framework-reference/html/images/spring-overview.png" min-width="720px" max-width="540px" width="400px" alt="Modulos Spring Framework">
 
 <p align="center">Figura 1: Projeto Spring Framework destacando o módulo Core Container</p>
</p>
<br>

Embora o Spring forneça integração e suporte para uma grande variedade de ferramentas corporativas e externas, ele intencionalmente mantém suas dependências obrigatórias em um mínimo absoluto. O ato de conectar beans juntos é baseado em um padrão conhecido como injeção de dependência (DI). Em vez de os componentes criarem e manterem o ciclo de vida de outros beans dos quais dependem, um aplicativo com injeção de dependência depende de uma entidade separada (o contêiner) para criar e manter todos os componentes e injetá-los nos beans que precisam deles. Isso é feito normalmente por meio de argumentos de construtor ou métodos de acesso de propriedade.

Como o projeto Spring Framework possui o módulo Core Container, onde está implementado a Inversão de Controle que utiliza da Injeção de Dependência, ele se torna o projeto essencial para iniciar uma aplicação sendo assim a base de toda a plataforma Spring.


## Controller Rest
### O que é (A)
- Controllers REST são utilizados para a criação de aplicações web baseados no padrão REST;
- Um controller ou controlador, é o responsável por receber requisições de fora do sistema e devolver respostas de acordo com as requisições;
### Anotações e Parâmetros das Anotações (A)
- @RestController -> Responsável por dizer que determinada classe irá manipular requisições HTTP;
- @RequestMapping(<partial_url>) -> Os métodos de seu controlador serão mapeados para URLs de acordo com a url parcial dentro da anotação;
    - @RequestMapping("/users/") -> indica que é responsável por atender requisições que contenham "/users/" em sua url;
#### Anotações de Requisição para métodos do Controller:
- @GetMapping(path) -> Indica que a requisição é do tipo GET;
- @PostMapping(path) -> Indica que a requisição é do tipo POST;
- @PutMapping(path) -> Indica que a requisição é do tipo PUT;
- @DeleteMapping(path) -> Indica que a requisição é do tipo DELETE;
- Todos estes métodos possuem path concatenado ao @RequestMapping, portanto "/users/"+path;
---
- @RequestParam <Type> -> Indica que o tipo será indicado na url juntamente ao seu RequestMapping+TipoGetting+RequestParam
    - Exemplo: "/users/getUser?id=123" -> Uma requisição do tipo get, de users, e enviando parametro id = 123;
- @PathVariable <Type> -> Similar ao RequestParam, porém utilizará uma URL diferente;
    - Exemplo: "/users/getUser/123"
#### Anotações de Resposta para métodos do controller:
- @ResponseBody -> Indica que o método irá retornar uma resposta HTTP;
- @ExceptionHandler(<Exception>.class) -> Configuração de resposta para caso um erro ocorra;
- @ResponseStatus(HttpStatus.<status>) -> Configura uma resposta de status para retorno de sua requisição;

### Exemplos
- Exemplo de criação de um controller:
```Java
@RestController
@RequestMapping("/users")
public class MyRestController {

    private final UserRepository userRepository;
    private final CustomerRepository customerRepository;

    public MyRestController(UserRepository userRepository, CustomerRepository customerRepository) {
        this.userRepository = userRepository;
        this.customerRepository = customerRepository;
    }

    @GetMapping("/{userId}")
    public User getUser(@PathVariable Long userId) {
        return this.userRepository.findById(userId).get();
    }

    @GetMapping("/{userId}/customers")
    public List<Customer> getUserCustomers(@PathVariable Long userId) {
        return this.userRepository.findById(userId).map(this.customerRepository::findByUser).get();
    }

    @DeleteMapping("/{userId}")
    public void deleteUser(@PathVariable Long userId) {
        this.userRepository.deleteById(userId);
    }
}
```
- Exemplo de controlar exceções:
```JAVA
class EmployeeNotFoundAdvice {

  @ResponseBody
  @ExceptionHandler(EmployeeNotFoundException.class)
  @ResponseStatus(HttpStatus.NOT_FOUND)
  String employeeNotFoundHandler(EmployeeNotFoundException ex) {
    return ex.getMessage();
  }
}
```
---
### Construtores, Acessores e Modificadores Necessários (Zé)
### Mapeamento de Verbos (D)
### Exemplos (D)
---
### Como Receber Dados da Chamada (Manu)
### Como Retornar Dados e Status (Manu)
### Classes e Métodos Adicionais (Zé)
### Exemplos (Cassiano)
----------------------------------
# Grupo 2

## Testes Unitários e de Integração
### O que são
## A Ferramenta Básica: JUnit
### O que é
### Cookbook
#### Pacotes (imports)
#### Anotações
#### Asserções
#### Execmplos
-----------------------------------
# Grupo 3

## Mocks
### O que são
### Quando usar
## A Ferramenta Mockito
### O que é
### Cookbook
### Pacotes (imports)
### Anotações e cláusulas
### Exemplos
### Testes Unitários e Mocks com Spring Rest Controller
-----------------------------------
# Grupo 4 

## Spring Data JPA
### O que é
## Classes e Interfaces
## Anotações
### Exemplos
## Anotações de Mapeamento
### Exemplos
## Cookbook
### Como usar
### Exemplos
## Testes Unitários e Mocks com Repositórios
### Como fazer
### Exemplos
------------------------------------
# Grupo 5

## Spring Security

## O que é
## Como funciona
### Cenários de uso (User details, OAuth com Token)
### Cadeia de Filtros
### Autorização e Roles
## Cookbook
### Como configurar
### Exemplos
### Autenticação com User Details
### Exemplos
### Autorização (com roles) de RestControllers e Beans
### Exemplos
### Autenticação com OAuth e Toke
### Exemplos
### Autorização (com roles) de RestControllers e Beans
### Exemplos


