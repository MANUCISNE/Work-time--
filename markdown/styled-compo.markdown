## STYLED COMPONENTS 

1- npm i styled-components
2- para typescript precisa instalar as tipagens em desenvolvimento (npm i @types/styled-components -D)
3- usar a extensão do styled-components dentro do VScode (verificar se estar ativa)

* Observações 

- com o styled components consigo inserir propriedades/funções dentro dos componentes, ou seja, estilizações que são baseadas nas informações que estão dentro das propriedades.

- o arquivo styles será com *.ts* se estiver usando typescript e *.js* se estiver usando javascript; não precisa ser *.tsx* ou *.jsx* pois dentro desse arquivo não terá nenhum componente, não terá nenhuma sintaxe HTML - return.

- arquivo styles.ts comentado:

```tsx
  //fazer a importação da biblioteca
  import styled from 'styled-components';

  //isso é um componente no react, então precisa ser criado uma interface para definir as propriedades
  interface ButtonContainerProps {
    variant: 'primary' | 'secondary';
  }

  const buttonVariants = {
    primary: 'purple'
    secondary: 'red'
  }
  
  //o nome da função precisa começar com letra maiúscula, pois no final se comportará como componente
  //button é a tag HTML que ele vai herdar 
  //usar a sintaxe do JS chamada template literals, usando as duas ``para colocar o CSS
  export function ButtonContainer = styled.button<ButtonContainerProps>`
    width: 100%;
    height: 40px;

    //junção de strings, incluir um código JS dentro de uma string maior. O código que está dentro das {} o styled-components vai executar como uma função 
    ${(props) => {
      return `background-color: ${buttonVariants[props.variant]}`
    }}
  `
```
- arquivo styles.ts sem comentários:

  ```tsx
  import styled from 'styled-components';

  export function ButtonContainer = styled.button`
    width: 100%;
    height: 40px;
  `
  ```
* logo após configurar o arquivo styles.ts trocar no arquivo de componentes Button.tsx a tag <button> para <ButtonContainer />