# **E7 ProjArq: Microsserviços de Câmbio e Conversão**

Este repositório contém dois microsserviços independentes criados com Spring Boot para demonstrar o uso de arquitetura baseada em microsserviços:

1. **Currency Exchange Service**: Fornece valores de câmbio entre moedas.
2. **Currency Conversion Service**: Converte valores de uma moeda para outra utilizando o serviço de câmbio.

---

## **Tecnologias Utilizadas**
- **Java 21**
- **Spring Boot 3.2.4**
- **Spring Web**
- **Spring Data JPA**
- **H2 Database**
- **Spring Cloud OpenFeign**
- **Maven**

---

## **Estrutura do Projeto**
```
e7-projarc/
├── currency-exchange-service/
│   ├── src/main/java/com/engsoft2/currencyexchange/
│   ├── src/main/resources/
│   │   ├── application.properties
│   │   ├── data.sql
│   ├── pom.xml
├── currency-conversion-service/
│   ├── src/main/java/com/engsoft2/currencyconversion/
│   ├── src/main/resources/
│   │   ├── application.properties
│   ├── pom.xml
└── README.md
```

---

## **Endpoints Disponíveis**

### **Currency Exchange Service**
- **Porta**: `8000`
- **Endpoints**:
  - `GET /currency-exchange/from/{from}/to/{to}`
    - Exemplo: `http://localhost:8000/currency-exchange/from/USD/to/BRL`

### **Currency Conversion Service**
- **Porta**: `8100`
- **Endpoints**:
  - `GET /currency-conversion/from/{from}/to/{to}/quantity/{quantity}`
    - Exemplo: `http://localhost:8100/currency-conversion/from/USD/to/BRL/quantity/100`
  - `GET /currency-conversion-feign/from/{from}/to/{to}/quantity/{quantity}`
    - Exemplo: `http://localhost:8100/currency-conversion-feign/from/USD/to/BRL/quantity/100`

---

## **Como Executar**

### **Pré-requisitos**
- Java 21 ou superior
- Maven 3.8+
- Git instalado

### **Passos**
1. Clone o repositório:
   ```bash
   git clone https://github.com/enzotonatto/e7-projarc.git
   ```
2. Navegue até o serviço desejado:
   ```bash
   cd e7-projarc/currency-exchange-service
   ```
3. Execute o serviço:
   ```bash
   ./mvnw spring-boot:run
   ```
4. Abra outra janela de terminal e inicie o serviço de conversão:
   ```bash
   cd e7-projarc/currency-conversion-service
   ./mvnw spring-boot:run
   ```

---

## **Exemplo de Uso**
Teste os serviços com ferramentas como **Postman** ou **Insomnia**:
1. Para obter o câmbio entre moedas:
   ```http
   GET http://localhost:8000/currency-exchange/from/USD/to/BRL
   ```
2. Para converter um valor de moeda:
   ```http
   GET http://localhost:8100/currency-conversion/from/USD/to/BRL/quantity/100
   ```
