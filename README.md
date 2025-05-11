# Desafio 1 - Sistema de Cotação do Dólar

Este projeto é composto por dois serviços: [`server`](server ) e [`client`](client ). O [`server`](server ) é responsável por obter a cotação do dólar de uma API externa e armazená-la em um banco de dados SQLite. O [`client`](client ) consome o serviço do [`server`](server ) para obter a cotação e salva o resultado em um arquivo de texto.

## Como executar

### 1. Servidor ([`server`](server ))

1. Navegue até a pasta do servidor:
   ```bash
   cd server
   ```

2. Instale as dependências do projeto:
   ```bash
   go mod tidy
   ```

3. Execute o servidor:
   ```bash
   go run main.go
   ```

   O servidor será iniciado na porta `8080` e estará pronto para receber requisições.

4. Durante a execução, o servidor criará um arquivo de banco de dados SQLite chamado `cotacoes.db` na mesma pasta. Este arquivo armazenará as cotações obtidas da API externa.

### 2. Cliente ([`client`](client ))

1. Navegue até a pasta do cliente:
   ```bash
   cd client
   ```

2. Instale as dependências do projeto:
   ```bash
   go mod tidy
   ```

3. Execute o cliente:
   ```bash
   go run main.go
   ```

4. O cliente fará uma requisição ao servidor para obter a cotação do dólar e salvará o resultado em um arquivo de texto chamado `cotacao.txt` na mesma pasta. O conteúdo do arquivo será algo como:
   ```
   Dólar: 5.1234
   ```

## Estrutura do Projeto

```
client/
    go.mod
    main.go
server/
    go.mod
    go.sum
    main.go
```

- **[`server/main.go`](server/main.go )**: Código do servidor que obtém a cotação do dólar e a armazena no banco de dados SQLite.
- **[`client/main.go`](client/main.go )**: Código do cliente que consome o serviço do servidor e salva a cotação em um arquivo de texto.

## Observações

- Certifique-se de que o servidor esteja em execução antes de rodar o cliente.
- O arquivo `cotacoes.db` será criado automaticamente pelo servidor e armazenará as cotações com um timestamp.
- O arquivo `cotacao.txt` será sobrescrito toda vez que o cliente for executado.