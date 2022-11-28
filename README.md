# Grupo 1

## Spring Boot
## O que é (Mat)
## Como Funciona Internamente (Mat)
---
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


