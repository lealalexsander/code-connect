# CodeConnect - Curso de JavaScript: Entendendo Promises e Async/Await

## Descrição

Este projeto foi desenvolvido como parte do curso de JavaScript, com foco no entendimento de Promises e Async/Await. O CodeConnect é uma aplicação web que permite aos usuários publicar projetos, carregar imagens e adicionar tags para categorização. O projeto utiliza HTML, CSS e JavaScript para criar uma interface interativa e responsiva.

## Tecnologias Utilizadas

- **HTML5**: Estrutura da página
- **CSS3**: Estilização e responsividade
- **JavaScript (ES6+)**: Manipulação do DOM e gestão de eventos
- **Promises e Async/Await**: Manipulação assíncrona de arquivos e interações do usuário

## Funcionalidades

- Upload de imagens com exibição prévia
- Publicação de projetos com nome, descrição e tags
- Adição e remoção dinâmica de tags
- Interface responsiva para diferentes dispositivos
- Menu lateral com navegação

## Como Executar o Projeto

1. Clone este repositório:
   ```bash
   git clone https://github.com/seu-usuario/codeconnect.git
   ```
2. Acesse a pasta do projeto:
   ```bash
   cd codeconnect
   ```
3. Abra o arquivo `index.html` em um navegador web.

## Estrutura do Projeto

```
CodeConnect/
│── img/                 # Imagens do projeto
│── styles.css           # Estilização da aplicação
│── scripts.js           # Lógica do JavaScript (Promises e Async/Await)
│── index.html           # Estrutura principal da aplicação
│── README.md            # Documentação do projeto
```

## Explicação das Promises e Async/Await

### Uso de Promises

O projeto utiliza `Promise` para lidar com o upload de imagens. O `FileReader` é usado para ler o arquivo de forma assíncrona e retorná-lo como uma URL base64.

```javascript
function lerConteudoArquivo(arquivo) {
    return new Promise((resolve, reject) => {
        const leitor = new FileReader();
        leitor.onload = () => {
            resolve({ url: leitor.result, nome: arquivo.name });
        };
        leitor.onerror = () => {
            reject(`Erro na leitura do arquivo ${arquivo.name}`);
        };
        leitor.readAsDataURL(arquivo);
    });
}
```

### Uso de Async/Await

O evento de upload de imagem usa `async/await` para aguardar a leitura do arquivo antes de definir a imagem na interface.

```javascript
inputUpload.addEventListener("change", async (evento) => {
    const arquivo = evento.target.files[0];
    if (arquivo) {
        try {
            const conteudoDoArquivo = await lerConteudoArquivo(arquivo);
            imagemPrincipal.src = conteudoDoArquivo.url;
            nomeDaImagem.textContent = conteudoDoArquivo.nome;
        } catch (erro) {
            console.error("Erro na leitura do arquivo", erro);
        }
    }
});
```

## Melhorias Futuras

- Implementação de um backend para persistência dos projetos
- Melhorias na acessibilidade e usabilidade
- Adição de filtros e pesquisa para encontrar projetos

## Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

## Autor

Alexsander Leal - Alura
