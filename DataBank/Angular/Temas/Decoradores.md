# @Input

```tsx
import { Component, Input } from '@angular/core';
import { Character } from '../../interfaces/character.interface';

@Component({
  selector: 'app-dbz-list',
  templateUrl: './list.component.html',
  styleUrl: './list.component.css'
})
export class ListComponent {

  **@Input()//Lo que se hace aqui es que a characterList se le pueda inputar desde el padre
  public characterList: Character[]**=[{
    name:'Trunk',
    power:10
  }]
}
```

```tsx
//Aqui tenemos los personajes que agregaremos
export class MainPageComponent {
    public characters: Character[]=[{
      name:'Krillin',
      power: 1000
    },{
      name:'Goku',
      power: 10000
    },{
      name:'Vegeta',
      power: 1
    }];
}
```

```html
<div class="col">
    <!--list-characters-->
    <app-dbz-list **[characterList]="characters"**></app-dbz-list>
  </div>
  <!--ahora a characterList se le agrega los characters-->
```

# @Output

Hijo —> Padre

```tsx
//Dentor del hijo "addCharacter"

@Output()
  onNewCharacter:EventEmitter<Character> = new EventEmitter;

  public character: Character = {
    name: '',
    power: 0
  }

emitCharacter():void{
  console.log(this.character)
  if(this.character.name.length===0)return;

  this.onNewCharacter.emit({...this.character});

  this.character.name='';
  this.character.power=0;
}
```

```tsx

@Component({
  selector: 'app-dbz-main-page',
  templateUrl: 'main-page.component.html'
})

export class MainPageComponent {
    public characters: Character[]=[{
      name:'Krillin',
      power: 1000
    },{
      name:'Goku',
      power: 10000
    },{
      name:'Vegeta',
      power: 1
    }];

    **onNewCharacter(character:Character):void{
        this.characters.push(character)
    }**
```

```html
<div class="col">
    <!--add-character-->
    <app-dbz-add-character (onNewCharacter)="onNewCharacter($event)"></app-dbz-add-character>

  </div>
```

### @Output-Borrar

### @ViewChild
```tsx
<h5>Buscar</h5>
  <input type="text" class="form-control" placeholder="Buscar gifs..."
  (keyup.enter)="searchTag()"
  #txtTagInput
  >
```

```tsx
 @ViewChild('txtTagInput')
  public tagInput!: ElementRef<HTMLInputElement>

  constructor() { }

  searchTag(){

    const newTag= this.tagInput.nativeElement.value;
    console.log({newTag});
  }
```