## useState

* hook para armazenar variáveis, que quando tem o seu valor alterado provocam uma nova renderização do componente, assim consegui-se exibir em tempo real uma informação conforme ela foi atualizada por uma funcionalidade (onClick, onSubmit) do usuário.

* iniciar um estado com uma informação do mesmo tipo a qual eu vou manuzear ao longo da minha aplicação =
    se for uma LISTA DE USUÁRIOS[], então preciso iniciar com uma [] vazia, exemplo: 

    ```tsx
    const [usuarios, setUsuarios] = useState<Usuarios[]>([])
    ```
   
    OBS. lembrar sempre de criar um interface para TS, exemplo:

    ```tsx
    interface Usuarios {
      id: string
      email: string
      age: number
    }
    ```
* para adicionar uma nova informação no array eu preciso copiar todos os ciclos que eu já tenho + ele próprio no final, exemplo: 

  ```tsx
  const newUsuario: newUsuarios = {
    id: 'string',
    email: data.email,
    age: data.age,
  }

  setUsuarios((state) => ([...state, newUsuario]))
  ```
* toda vez que eu estou alterando um estado e esse estado depende da sua versão anterior, o valor desse estado deve ser SETADO em formato de função(areo function), exemplo: 

  ```tsx
  setUsuarios((state) => ([...state, newUsuario]))
  ```