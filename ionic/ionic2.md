# Ionic

## Páginas e componentes

Se você é, de alguma forma, familiar ao angular, provavelmente conhece o conceito de componentes: _Templates altamente funcionais que são encapsulados em seletores HTML personalizados_.

O ionic extende esse conceito de componentes à páginas, que, em poucas palavras, são _components que ocupam toda a tela e devem ser chamados pela controller de navegação do ionic_.

### Criação de novas páginas

Através do ionic CLI é possível criar novas páginas:
```
ionic generate page users
```

Isso criará uma pasta em `src` contendo o template, a página de estilos e a controller: `users.html`, `users.scss` e `users.ts`, respectivamente.

Dentro do arquivo do template, podem ser utilizados os [componentes visuais](https://ionicframework.com/docs/components/) presentes na [documentação do ionic](https://ionicframework.com/docs/).

**IMPORTANTE**

É necessário registrar `UsersPage` em `app.module.ts` dentro de `declarations` e `entryComponents`:

```js
import { ErrorHandler, NgModule } from '@angular/core';
import { IonicApp, IonicErrorHandler, IonicModule } from 'ionic-angular';
import { MyApp } from './app.component';
import { UsersPage } from '../pages/users/users';
	
@NgModule({
    declarations: [
        MyApp,
        HomePage,
	UsersPage,
    ],
    imports: [
        IonicModule.forRoot(MyApp),
    ],
    bootstrap: [IonicApp],
    entryComponents: [
        MyApp,
        HomePage,
	UsersPage,
    ],
})
export class AppModule {}

```

## Navegação
A navegação dentro do ionic funciona como o gerenciamento de uma pilha de páginas.

É possível empilhar e desempilhar páginas e a página visualizada é sempre a página que está no topo.

`ion-nav` inicializa a pilha de páginas.

```html
<ion-nav [root]="rootPage"><ion-nav>

```

- `rootPage` é setada em `app.component.ts` e seu valor padrão é _HomePage_.

## Navegação

Agora considere que da Home (página criada automaticamente pelo ionic) você queira navegar para a página de usuários. Existem duas formas de fazer isso:
### 1. Através de um método

**home.html**
```html
<ion-header>
	<ion-navbar>
		<ion-title>categories</ion-title>
	</ion-navbar>
</ion-header>

<ion-content padding>
	<button ion-button (click)="onGoToUsers()">Users</button>
</ion-content>
```

**home.ts**
```js
import { Component } from '@angular/core';
import { NavController } from 'ionic-angular';
import { UsersPage } from '../users/users';


@IonicPage()
@Component({
		selector: 'page-home',
		templateUrl: 'home.html',
	})
	export class HomePage {

		constructor(public navCtrl: NavController) {}

		onGoToUsers() {
		    this.navCtrl.push(UsersPage);
		}
	}
	
```
### 2. Através de diretivas de navegação

**home.html**
```html
<ion-header>
	<ion-navbar>
		<ion-title>categories</ion-title>
	</ion-navbar>
</ion-header>
	
<ion-content padding>
	<button ion-button [push]="userPage">Users</button>
</ion-content>
```

**home.ts**
```js
import { Component } from '@angular/core';
import { NavController } from 'ionic-angular';
import { UsersPage } from '../users/users';


@IonicPage()
@Component({
		selector: 'page-home',
		templateUrl: 'home.html',
	})
	export class HomePage {
		userPage = UsersPage;
	}
```
### Removendo páginas da pilha
Pode-se remover uma página do topo da pilha com `this.navCtrl.pop()` (Note que, por ser uma pilha, não há necessidade de passar argumentos).
Também é possível remover todas as páginas da pilha e retornar à rootPage com `this.navCtrl.popToRoot()`.
