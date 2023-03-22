# LIBS DE VALIDAÇÃO DE FORMULÁRIO

* exemplos (js)

* yup
* joi
* zod (utilizada no curso, pois traz mais interação com TS)

## INSTALAR A ZOD

* npm i zod
* npm i @hookform/resolvers (permitir a integração do react hook form às bibliotecas de validação)
* a biblioteca zod não tem um export default(padrão), então tenho que fazer a importação assim:

```tsx
import * as zod from 'zod'
```

* Observações

* definação Schema: as bibliotecas de validações usam um formato de validação que é schema bases(definir um formato e validar nosso formulário com base nesse formato)

* interface: utilizar quando vou definir o objeto de validação

* type: utilizar quando vou criar uma tipagem a partir de outra referência

* o verbo inferir dentro do typescript = definido automaticamente

* quando quero converter uma variável JS para TS eu sempre preciso tipar (typeof ...)

* reset (do useForm) volta aos valores do input para os default values
