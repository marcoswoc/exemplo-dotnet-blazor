![banner](Img/banner.png)
# Blazor WebAssembly

## Introdução
Blazor é uma tecnologia .NET para criar SPA, isso mesmo single page application, usando apenas HTML, CSS e C#, graças ao WebAssembly (WASM) é possível utilizar C# para criar aplicações do lado do cliente.
O Blazor possui dois modelos de hospedagem, Blazor Server que atualiza a interface utilizando SignalR e Blazor WASM, neste artigo vamos criar um projeto Blazor WASM.

Você pode acessar o repositório desse projeto em
[exemplo-dotnet-blazor](https://github.com/marcoswoc/exemplo-dotnet-blazor).

## Pré-requisitos

+ .NET 5+
+ Visual Studio Code (VS Code)
+ Terminal de sua preferência

## Criando o projeto

Com o comando **`dotnet new blazorwasm`** vamos criar um projeto Blazor Webassembly. O parâmetro **`-o`** indicar o nome da pasta em que o projeto será criado.
    
    dotnet new blazorwasm -o exemplo-dotnet-blazor


## Estrutura do Projeto
Acessando a pasta do projeto via terminal podemos utilizar o comando **`code .`** para abrir o projeto no Vs Code, teremos a seguinte estrutura de arquivos:

![img-1](Img/img-1.png)

### Pages

Nesta pasta contém os componentes/páginas roteáveis **`.razor`** . A rota da página pode ser especificada no arquivo utilizando **`@page`**

### Shared

Contém alguns componentes compartilhados e folhas de estilo, podemos criar um arquivo **`.css`** por componente.

### wwwroot

Contém os arquivos estáticos públicos do aplicativo. Nesta pasta temos o arquivo index.html, quando qualquer página do aplicativo é solicitada, essa página é renderizada dentro da div com id app **`<div id="app">Loading...</div>`** .

### _Imports.razor

É um arquivo onde podemos centralizar os recursos importados na aplicação de forma global. 
### App.razor

O componente raiz da aplicação, através desse componente que é renderizado a página que corresponde ao endereço solicitado no navegador.

### Program.cs

O ponto de entrada do aplicativo que configura o host do Webassembly *(se você estiver utilizando o .NET 5 ou inferior essas configurações vão estar no arquivo Startup.cs)*

Aqui é onde especificamos o componente principal da aplicação:

 **`builder.RootComponents.Add<App>("#app")`**.

Os Serviços podem ser adicionados e configurados da seguinte forma:

**`builder.Services.AddSingleton<IMyDependency, MyDependency>()`**.

## Executando o projeto

Para executar o projeto no Vs Code podemos utilizar um dos seguintes comandos:

    dotnet run

ou

    dotnet watch

 A vantagem de utilizar **`dotnet watch`** é que esse comando ativa o Hot reload, ao modificar determinados arquivos as alterações são aplicadas e o navegador é atualizado sem a necessidade de parar a execução da aplicação.

 ![img-2](Img/img-2.png)


Vamos modificar o componente Counter.razor no método **`IncrementCount()`** para incrementar **`currentCount`** de 10 em 10, e adicionar **`Console.WriteLine(DateTime.Now);`** para observarmos seu comportamento no **console do navegador**.

Código do arquivo **`Counter.razor`**:

```razor
@page "/counter"

<PageTitle>Counter</PageTitle>

<h1>Counter</h1>

<p role="status">Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount+=10;
        Console.WriteLine(DateTime.Now);
    }
}
```

Após as alterações teremos o seguinte resultado:

![img-3](Img/img-3.png)

## Criando um componente

As aplicações Blazor utilizam os Razor componentes escritos com **`HTML`** e **`C#`** com o comando **`dotnet new razorcomponent`** podemos adicionar um novo componente na aplicação, utilizamos os parâmetros **`-n`** para definir o nome do componente, e **`-o`** para indicar a pasta onde será criado.

    dotnet new razorcomponent -n Saudacao -o Shared

Ao fazer uma modificação com o projeto sendo executado podemos receber uma mensagem de confirmação de restart da aplicação, recomendo utilizar a opção **`Always (a)`** pois assim sempre que houver uma modificação será atualizado em tela.
 
 ![img-4](Img/img-4.png)

Para utilizar parâmetros nos componentes utilizamos o atributo **`[Parameter]`** que precisar ter o acesso público, podemos utilizar nosso componente com a marcação HTML utilizando seu nome **`<NomeDoComponente></NomeDoComponente>`** e os parâmetros podem ser atribuídos da seguinte forma **`<NomeDoComponente Parametro="valor"></NomeDoComponente>`**

Código do arquivo Saudacao.razor:

```razor
<h1>Hello @Name </h1>

@code {
    [Parameter]
    public string? Name { get; set; }
}
```

No arquivo Index.razor vamos substituir **`<h1>Hello, world!</h1>`** por **`<Saudacao Name="Peter 🕷"></Saudacao>`**

*(utilizei o atalho **`windows + .`** para fazer a aranha🕷 )*


Código do arquivo Index.razor:


```razor
@page "/"

<PageTitle>Index</PageTitle>

<Saudacao Name="Peter 🕷"></Saudacao>

Welcome to your new app.

<SurveyPrompt Title="How is Blazor working for you?" />

```

Teremos os seguinte resultado:

![img-5](Img/img-5.png)

## Conclusão 

O Blazor não veio para retirar o JavaScript da jogada, é possível utilizar javascript junto com o Blazor se houver necessidade, particularmente estou empolgado com o fato de poder aproveitar o conhecimento em C# para criar aplicações do lado do cliente. É possível criar Progressive Web App (PWA) com Blazor, além de poder utilizar o Blazor junto do o .NET MAUI (preview) para criar aplicativos multiplataforma com funcionalidades nativas. Para mais informações sobre Blazor consulte a documentação oficial - [Microsoft docs](https://docs.microsoft.com/pt-br/aspnet/core/blazor/?WT.mc_id=dotnet-35129-website&view=aspnetcore-6.0).


