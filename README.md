# Blazor WebAssembly

## Introdução
Blazor é uma tecnologia .NET para criar SPA, isso mesmo single page application, usando apenas HTML, CSS e C#, graças ao WebAssembly (WASM) é possivel utiliza C# para criar aplicações do lado do cliente.
O blazor possui dois modelos de hospedagem, Blazor Server que atualiza a interface utilizando SignalR, mas neste artigo vamos criar um projeto Blazor WASM.

Você pode acessar o repositorio desse projeto em
[exemplo-dotnet-enum](https://github.com/marcoswoc/exemplo-dotnet-enum).

## Pré-requisitos

+ .NET 5+
+ Visual Studio Code (VS Code)
+ Terminal de sua preferência

## Criando o projeto

Com o comando **`dotnet new blazorwasm`** Voce pode usar o paramentro **`-o`** para indicar o nome da pasta em que o projeto sera criado.
    
    new blazorwasm -o exemplo-dotnet-blazor

Acessando a pasta do projeto via terminal podemos utilizar o comando **`code .`** para abrir o projeto no Vs Code, teremos a seguinte estrutura de arquivos:


