# Ionic

## Páginas e componentes

    Se você é, de alguma forma, familiar ao angular, provavelmente conhece o conceito de componentes: _Templates altamente funcionais que são encapsulados em seletores HTML personalizados_.
        O ionic extende esse conceito de componentes à páginas, que, em poucas palavras, são _components que ocupam toda a tela e devem ser chamados pela controller de navegação do ionic_.

### Navegação
A navegação dentro do ionic funciona como o gerenciamento de uma pilha de páginas.
É possível empilhar e desempilhar páginas e a página visualizada é sempre a página que está no topo.

`ion-nav` inicializa a pilha de páginas.

```
    <ion-nav [root]="rootPage"><ion-nav>

    ```

    - `rootPage` é setada em `app.component.ts` e seu valor padrão é _HomePage_.

