* CONTEXT API - aula ignite

- uma maneira de compartilhar informações entre vários componentes do nosso app, sem precisar ficar utilizando várias propriedades

- quando se cria um contexto, não se pode modificar essas informações, ou seja, o contexto tem o mesmo valor sempre 

- quando se quer modficar o valor da variável que esta dentro do contexto, essa variável precisa ser um estado.

  1. começa fazendo a importação do createContext:

  ```tsx
  import { createContext } from 'react'
  ```
  2. armazenar esse contexto numa variável (const):

  ```tsx
  // o nome da variável tem que ter alguma relação com o tipo de informação que eu vou guardar dentro do contexto (ex. CyclesContext)
  const CyclesContext = createContext()
  ```
  3. dentro do () geralmente colocamos um objeto, armazendo a data/valor inicial

  ```tsx
  const CyclesContext = createContext({
    activeCycle: 1,
  })
  ```
  4. para usar o contexto, deve-se usar um hook do react chamado useContext dentro do arquivo dos componentes
  
  ```js
  import { useContext } from 'react'

  export function NewCycleForm() {
    const { activeCycles } = useContext(CyclesContext)

    return (
      <h1>
        NewCycleForm: {activeCycle}
        <button
        onClick={() => {
          setActiveCycle(1)
        }}
        >
          Alterar Novo Ciclo
        </button>
      <h1>
    )
  }
  ```
    >> OBS. activeCycle é como se fosse uma variável compartilhada com 2 componentes 
  
  5. criar o estado no componente pai, para que todos os componentes tenha acesso a esse estado e no return do componente pai colocar um componente do react (provider):

  ```tsx
  // o estado precisa ser criado no componente pai, pois ela engloba todos os componentes que podem precisar ter acesso as mudanças de estado de uma função
  const [activeCycle, setActiveCycle] = useState(0)

  // o value geralmente será uma {}/objeto de informações que queremos enviar para os componentes
  <CyclesContext.Provider value={{ activeCycle, setActiveCycle }}>
    // os components precisam estar dentro do provider, para ter acesso aos valores declarados no contexto
    <NewCycleForm />
  </ CyclesContext.Provider >
  ```

* Context API - ChatGPT

The Context API is a feature in React, a popular JavaScript library for building user interfaces, that allows you to share data between components without having to pass it down through multiple levels of props.

The Context API provides a way to create global data that can be accessed by any component in the application. This can be useful for sharing data like the current user's authentication status, theme preferences, or language settings across different parts of the app.

The Context API consists of two parts: the context provider and the context consumer. The provider is used to create a new context and pass the data down to any components that need it. The consumer is used to access that data from within a component.

Using the Context API can help simplify your code and make it more readable, as it removes the need for "prop drilling" where you pass down data through multiple layers of components.

Here is an example of how to use the Context API in React:

```tsx
import { createContext } from 'react'

// Create a new context
const MyContext = React.createContext();

// Wrap your application in a provider
function MyApp() {
  return (
    <MyContext.Provider value={"Hello World"}>
      <MyComponent />
    </MyContext.Provider>
  );
}

// Access the context value in a consumer
function MyComponent() {
  return (
    <MyContext.Consumer>
      {value => <p>{value}</p>}
    </MyContext.Consumer>
  );
}
```

In this example, we create a new context called MyContext using React.createContext(). We then wrap our application in a MyContext.Provider component, passing the value "Hello World" as the context data. Finally, we access the context value within the MyComponent component using the MyContext.Consumer component.