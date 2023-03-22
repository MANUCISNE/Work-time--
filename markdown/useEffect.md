# useEffect

* Hooks: são funções que começam com o prefixo *use* e tem como intuito de adicionar algum funcionamento à algum componente da aplicação.

* effect vem de -> Side-effect: Efeito Colateral (ação que acontece após uma ação anterior já executada).

* o useEffect vai executar em 2 situações: quando a variável mudar e executa também no ínicio, assim que o componente for exibido em tela.

* evitar executar a função dentro da raiz do componente, pois não pode-se passar exatamente a variável que quero monitorar.

* não precisa criar um estado para criar informações que é originada a partir de outras informações (ex. lista de usuários, a lista advém dos usuários), basta apenas criar uma constante, exemplo:

 - essa forma de escrever o código evita renderizções desnecessárias, e só calcula o valor da const criada e não precisa salvar no estado de novo, ou seja, apenas 1 renderização e mais performático
```tsx
const filteredList = list.filter(item => item.includes(filter))
```

* não se usa useEffect para atualizar o nosso estado de forma syncrona(sem precisar fazer uma requisição)

* o useEffect pode ter um retorno que sempre será uma função, onde essa função tem ação na segunda renderização do useEffect (resetar o que o useEffect estava fazendo)

```tsx
  import { useEffect, useState } from 'react'
  
  function avisarAPI() {
    console.log('Lista salva!')
  }

  export function App() {
    const [list, setList] = useState<string[]>([])
    const [filter, setFilter] = useState<''>

    // {} = qual função será executada
    // dentro do [] eu passo a variável que eu quero monitorar as alterações
    // o [] é chamado de dependências
    useEffect(() => {
      //essa condicional evita que o useEffect seja executado na primeira renderização do App.
      //if (list.lenght !== 0) {
      avisarAPI()
      //}
    }, [list])  

    //quando não passo nenhuma dependência dentro do useEffect, o hook irá executar apenas 1x (quando aparecer em tela pela 1x).
    useEffect(() => {
      fetch('https://api.github.com/users/MANUCISNE/repos')
      .then(response => response.json())
      .then(data => {
        setList(data.map((item: any) => item.full_name))
      })
    }, [])

    const filteredList = list.filter(item => item.includes(filter))

    function addToList() {
      setList((state) => [...state, 'Novo item'])
    }

    function removeFromList() {
      //remover item da lista 
    }

    return (
      <div>
        <input 
          type="text" 
          onChange={e => setFilter(e.target.filter)}
          value={filter}
        />

        <ul>
          {list.map(item => <li>{item}</li>)}
        </ul>

        <ul>
          {filteredList.map(item => <li>{item}</li>)}
        </ul>

        <button onClick={addToList}>Add to list</button>
      </div>
    )
  }
```
