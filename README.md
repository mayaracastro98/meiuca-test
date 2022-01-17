# Meiuca Design System Test

<img src="https://scontent.fpoa8-1.fna.fbcdn.net/v/t1.6435-9/80093565_585779018658678_1661205161529311232_n.png?_nc_cat=109&ccb=1-5&_nc_sid=973b4a&_nc_ohc=foPdGHjzqFMAX8F7R6N&_nc_ht=scontent.fpoa8-1.fna&oh=00_AT8mPXQWrbtSTvOX2HVLz8sJMVHTxQcU2iFAhJbamiSFgA&oe=6209DF2F" alt="Logo da Meiuca">

> Teste técnico para processo seletivo da Meiuca.

## 💻 Pré-requisitos

Antes de começar, verifique se você atendeu aos seguintes requisitos:
Sete a versão correta de node para `v16.11.0`. Se você utiliza [NVM](https://github.com/nvm-sh/nvm), basta executar `nvm use`.

## 🚀 Instalando o design-system

Para instalar o design-system, siga estas etapas:

```sh
`$ cd design-system`
`$ yarn install`
```

## ☕ Usando o design-system

Ainda que criado em Vue, o propósito do teste técnico é apresentar os componentes no Storybook. Por esta razão, não há um arquivo App.vue na arquitetura do projeto, não sendo possível rodar o comando 
```sh
`$ yarn serve`
``` 
Para visualizar os componentes no Storybook, siga estas etapas:
```sh
`$ yarn storybook`
``` 

## 📂 Estrutura de pastas

De forma resumida: os componente estão divididos em duas pastas: (`base-components`) onde estão os componentes base da aplicação e (`composition-components`), onde, como o nome sugere, estão os componentes compostos pelos componentes da pasta base-components. Junto do arquivo estão também os stories da documentação do storybook de cada componente(`.stories.mdx`). 

```text
├─ src/
│  ├─ base-components/
│  │  │  ├─ Button.vue
│  │  │  ├─ Button.stories.mdx
│  ├─ composition-components/
...
```

## 📝 Documentação no Storybook

As páginas do Storybook são escritas usando Markdown com JSX embutido, ou seja, podemos misturar texto formatado com componentes funcionais. A premissa das histórias (stories) é descrever casos de uso/estados dos componentes.

## 📸 Testes de Regressão Visual

Para realizar os testes visuais, foi escolhido a ferramenta [Loki](https://loki.js.org/), que é executada automaticamente em cada Story de componente que é criado. É importante destacar aqui que as imagens podem ser geradas de maneira diferente em diferentes sistemas operacionais, e alguns workarounds como o uso de docker podem ser implementados para evitar discrepâncias, ainda sim, este workaround NÃO foi desenvolvido neste teste, visto a baixa complexidade dos componentes.

### 🎞️ Rodando os testes localmente

Importante destacar que para rodarmos os testes, é necessário que o storybook esteja rodando. Após rodar o storybook execute o seguinte comando:

`$ yarn loki test`

Caso você tenha erros e precise atualizar a imagem:

`$ yarn loki update`

## ✏️ Decisões técnicas

###  Vue

Além de mais familiaridade com este framework, algumas outras razões suportam esta decisão, como:

- Tamanho pequeno: Com um tamanho tão pequeno, o Vue não é só rápido para baixar e instalar a biblioteca, mas também impacta positivamente o SEO e UX.

- Virtual DOM/performance: Alguns benchmarks já provaram que, ao testar componentes DOM vinculados a data updated, o Vue.js tem melhor desempenho que o Angular e o React.

- Reactive two-way data binding.

- Single-file components e legibilidade de código.

- Ótimo para testes unitários.

- Capacidades de integração e flexibilidade: Como depende apenas de JavaScript e não requer nenhuma outra ferramenta para funcionar, o Vue também permite que você escreva os templates como desejar: usando HTML, JS ou JSX. 

- Fácil de aprender.

###  TypeScript

- Linguagem compilada.

- Confiável: Ao contrário do JavaScript, o TypeScript é mais confiável e mais fácil de refatorar, o que permite aos desenvolvedores evitar erros e reescrever com muito mais facilidade. Os tipos invalidam a maioria dos erros bobos que podem se infiltrar nas bases de código JavaScript e criam um feedback rápido para corrigir todos os pequenos erros ao escrever um novo código ou refatorar.

- Explícito: Tornar os tipos explícitos concentra nossa atenção em como exatamente nosso sistema é construído e como as diferentes partes dele interagem entre si.

- É uma escolha inteligente para projetos e/ou sistemas complexos.

###  Visual Test com Loki

- Como um Design System é muito orientado à interface do usuário, os testes visuais caem muito bem para este tipo de projeto.

- Os testes visuais verificam se cada elemento em uma página aparece na forma, tamanho, cor e posição corretos.

- Os testes visuais verificam se esses elementos aparecem e funcionam perfeitamente em uma variedade de dispositivos e navegadores.

- Existem algumas ferramentas de testes de regressão visual para a web, mas a maioria não pode ser executada de maneira headless ou então utilizam phantomjs (que está obsoleto).

- Os testes visuais com loki são fáceis de configurar.

- Sem custo de manutenção.

- Testes reproduzíveis independentes do sistema operacional.


###  Approach dos componentes

- O approach da solução dos componentes fora levado em conta minha experiência com este tipo de solução e também a facilidade para aquele que irá utilizar o código gerado destes componentes.

- Ainda que o código possa parecer verboso, ele é na verdade configuravél, e fácil de se utilizar.

- Como approach, utilizei na sua maioria a estratégia do uso de props para lidar com os estilos e os dados de texto (ou outros dados) dos componentes. As props são utilizadas para configurar (ou personalizar) todas as propriedades dos componentes que são referentes à brand. Isso significa que, em um cenário hipotético, caso o componente de Button tenha sido especificado que na brand 1 sua cor de background é rosa, na brand 2 (que deseja utilizar o mesmo botão) a cor é azul. Com o uso das props, o desenvolvedor consegue fácilmente configurar estas opções.


### Breve explicação sobre como faria para otimizar a manutenção e a qualidade do código, levando em consideração o cenário de uma grande empresa com múltiplos desenvolvedores.

- A sugestão do uso de props é fácil e intuitiva de se entender, e o uso da tipagem de TypeScript no uso das mesmas também ajuda na legibilidade do código ou no entendimento do que está correto ou não. Isto ajuda também na manutenção do código, pois, quanto mais fácil e rápido for entender os erros e as limitações das aplicações, mais fácil é de encontrar workarounds para estes problemas. 

- Uso de linters no código.

- Documentação para desenvolvedores completa e clara sobre quais são os entregáveis, o que cada um deve fazer, como deve ser o handover, etc.

- Revisão severa de PRs com bom templates, utilização de exemplos, motivações da feature (ou o motivo de um bug),discussão nos PRs, uso de ambientes de desenvolvimento, uso de esteira de testes no CI, atenção de code-owners no que entra ou não nos projetos, uso de ferramentas externas para ajudar com a manutenção, como por exemplo: dependências que não são mais utilizadas, componentes ou outros arquivos que não são importados para lugar algum, etc.



