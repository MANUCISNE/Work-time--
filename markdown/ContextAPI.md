* CONTEXT API

- uma maneira de compartilhar informações entre vários componentes do nosso app, sem precisar ficar utilizando várias propriedades

- quando se cria um contexto, não se pode modificar essas informações, ou seja, o contexto tem o mesmo valor sempre 

- quando se quer modficar o valor da variável que esta dentro do contexto, essa variável precisa ser um estado.

  1. começa fazendo a importação do createContext:
  ```ts
  import { createContext } from 'react'
  ```
  2. armazenar esse contexto numa variável (const):

  OBS. o nome da variável tem que ter alguma relação com o tipo de informação que eu vou guardar dentro do contexto
  ```ts
  const CyclesContext = createContext()
  ```
  3. dentro do () geralmente colocamos um objeto:
  ```ts
  const CyclesContext = createContext({
    activeCycle: 1,
  })
  ```
  4. usa um hook do react chamado useContext dentro do arquivo dos componentes
  ```ts
  import { createContext, useContext } from 'react'

  export function Countdown() {
    const { activeCycles } = useContext(CyclesContext)

    return <h1>NewCycleForm: {activeCycle}<h1>
  }
  ```
  OBS. activeCycle é como se fosse uma variável compartilhada com 2 componentes 
  
  5. criar o estado no componente pai, para que todos os componentes tenha acesso a esse estado e no return do componente pai colocar um componente do react (provider):

  ```ts
  const [activeCycle, setActiveCycle] = useState(0)

  <CyclesContext.Provider value={{ activeCycle  }}>
  CONTEÚDO DO RETURN - COMPONENTE PAI
  </ CyclesContext.Provider >
  ```
