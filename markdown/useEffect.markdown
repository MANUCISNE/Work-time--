## useEffect

* Hooks: são funções que começam com o prefixo *use* e tem como intuito de adicionar algum funcionamento à algum componente da aplicação

* effect vem de -> Side-effect: Efeito Colateral (ação que acontece após uma ação anterior já executada)

```tsx
  export function App() {
    const [list, setList] = useState<string[]>([])

    function addToList() {
      setList()
    }

    return (
      <div>
        <button>Add to list</button>
      </div>
    )
  }
```