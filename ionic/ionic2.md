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

### Criação de novas páginas e navegação

Através do ionic CLI é possível criar novas páginas:
```
	ionic generate page users
```

Isso criará uma pasta em `src` contendo o template, a página de estilos e a controller: `users.html`, `users.scss` e `users.ts`, respectivamente.

Dentro do arquivo do template, podem ser utilizados os [https://ionicframework.com/docs/components/](componentes visuais) presentes na [https://ionicframework.com/docs/](documentação do ionic).

**IMPORTANTE**
É necessário registrar `UsersPage` em `app.module.ts` dentro de `declarations` e `entryComponents`:

```
	import { ErrorHandler, NgModule } from '@angular/core';
	import { IonicApp, IonicErrorHandler, IonicModule } from 'ionic-angular';
	import { MyApp } from './app.component';
	import { UsersPage } from '../pages/users/users';
	
@NgModule({
    declarations: [
        MyApp,
        HomePage,
    ],
    imports: [
        IonicModule.forRoot(MyApp),
    ],
    bootstrap: [IonicApp],
    entryComponents: [
        MyApp,
        HomePage,
    ],
})
export class AppModule {}

```
