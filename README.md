# Blazor WebAssembly

## Introdução
Blazor é uma tecnologia .NET para criar SPA, isso mesmo single page application, usando apenas HTML, CSS e C#, graças ao WebAssembly (WASM) é possivel utiliza C# para criar aplicações do lado do cliente.
O blazor possui dois modelos de hospedagem, Blazor Server que atualiza a interface utilizando SignalR e Blazor WASM, neste artigo vamos criar um projeto Blazor WASM.

Você pode acessar o repositorio desse projeto em
[exemplo-dotnet-enum](https://github.com/marcoswoc/exemplo-dotnet-enum).

## Pré-requisitos

+ .NET 5+
+ Visual Studio Code (VS Code)
+ Terminal de sua preferência

## Criando o projeto

Com o comando **`dotnet new blazorwasm`** vamos criar um projeto Blazor Webassembly.Voce pode usar o paramentro **`-o`** para indicar o nome da pasta em que o projeto sera criado.
    
    new blazorwasm -o exemplo-dotnet-blazor


## Estrutura do Projeto
Acessando a pasta do projeto via terminal podemos utilizar o comando **`code .`** para abrir o projeto no Vs Code, teremos a seguinte estrutura de arquivos:

![img-1](Img/img-1.png)

### Pages

Nesta pasta contém os componentes/páginas roteáveis **`.razor`** . A rota da pagina pode ser especificada no arquivo utilizando **`@page`**

### Shared

Contém alguns componentes compartilhados e folhas de estilo, podemos criar um arquivo **`.css`** por componente.

### wwwroot

Contém os arquivos estáticos públicos do aplicativo. Nesta pasta temos o arquivo index.html, quando qualquer página do aplicativo é solicitada, essa página é renderizada dentro da div com id app **`<div id="app">Loading...</div>`** .

### _Imports.razor

É um arquivo onde podemos centralizar os recursos importados na aplicação de forma global. 
### App.razor

O componente raiz da aplicação, atraves desse componente navegador e renderiza a página que corresponde ao endereço solicitado.

### Program.cs

O ponto de entrada do aplicativo que configura o host do Webassembly *(se você estiver utilizando o .NET 5 ou inferior ainda possuem o arquivo Startup.cs)*

Aqui é onde especificamos o componente principal da aplicação:

 **`builder.RootComponents.Add<App>("#app")`**.

Os Serviços podem ser adicionados e configurados:

**`builder.Services.AddSingleton<IMyDependency, MyDependency>()`**.

## Execultado o projeto

Para executar o projeto podemos utilizar um dos seguintes comandos:

    dotnet run

ou

    dotnet watch
 A vantagem de utilizar **`dotnet watch`** é que ao modificar determiandos arquivos as alteração são aplicadas e o navegador é atulizado sem a necessidade de parar a execução da aplicação.

 ![img-2](Img/img-2.png)