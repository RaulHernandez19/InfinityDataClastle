### Directiva *nglf

Remueve o cre una parte del DOM basado en la expresion “snowSection”
![[Pasted image 20240625134650.png]]

### Directiva *ngFor

![[Pasted image 20240625134708.png]]

```html
<!--Extension de lo ya visto, basicamente se puede sacar el indice y mas valores en base a ello-->

<li *ngFor="let character of characterList;
        let i = index;
        let isFirst=first;
        let isLast=last;
        let isEven=even;
        let isOdd=odd;
        "
        class="list-group-item">

        <span class="text-primary">{{i+1}}.-</span>

        <span>{{character.name}} - </span>

        <strong>Power: </strong>

        {{character.power}}

        </li>
```

### Directiva *if

```html
<h3 *ngIf="deletedHero!=' '; else nothingWasDeleted">
  Heroe borrado: <small class="text-danger">{{deletedHero}}</small> </h3>

 <ng-template #nothingWasDeleted> <!--Aqui sera el else de lo de arriba-->
  <h3>No ha borrado nada.</h3>
 </ng-template>
```

### Directiva *ngModel

```html
<!--Sirve para aplicar  cosas especificas a cada linea-->

 <li *ngFor="let character of characterList;
        let i = index;
        let isFirst=first;
        let isLast=last;
        let isEven=even;
        let isOdd=odd;
        "
        class="list-group-item"
        **[ngClass]="{
          'list-group-item-secondary':isEven,
          'list-group-item-primary':isOdd

      }"**>
```