# Angular Style Guide
Angular Style Guide แปล สรุป เรียบเรียงจาก https://angular.io/guide/styleguide

## สารบัญ
1. [Single responsibility](#single-responsibility)
2. [Naming](#naming)
3. [Application structure and NgModules](#application-structure-and-ngmodules)
4. [Components](#components)
5. [Directives](#directives)
6. [Services](#services)
7. [Data Services](#data-services)
8. [Lifecycle hooks](#lifecycle-hooks)

## Single responsibility
### Rule of One
สร้างแต่ละอย่างเป็นไฟล์ๆไป เช่น Component 1 ไฟล์ Service 1 ไฟล์
พยายามให้ Code ในแต่ละไฟล์ไม่เกิน 400 บรรทัด
เพราะไฟล์เล็กจะทำให้อ่านง่ายกว่า ดูแลง่ายกว่า 
เพราะการประกาศ 1 Component ต่อ 1 ไฟล์ ทำให้ไม่สับสน
การมีเกิน 1 Component ต่อไฟล์อาจทำให้ใช้ตัวแปรตัวเดียวกัน ทำให้เกิดบัคได้ง่าย
การประกาศ 1 Component ต่อไฟล์จึงทำให้ Reuse ได้ง่ายกว่า อ่าน Code ง่ายกว่า และผิดพลาดน้อยกว่า

**ตัวอย่างที่ไม่ดี:**

app/heroes/hero.component.ts
```typescript
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { BrowserModule } from '@angular/platform-browser';
import { NgModule, Component, OnInit } from '@angular/core';

class Hero {
  id: number;
  name: string;
}

@Component({
  selector: 'my-app',
  template: `
      <h1>{{title}}</h1>
      <pre>{{heroes | json}}</pre>
    `,
  styleUrls: ['app/app.component.css']
})
class AppComponent implements OnInit {
  title = 'Tour of Heroes';

  heroes: Hero[] = [];

  ngOnInit() {
    getHeroes().then(heroes => this.heroes = heroes);
  }
}

@NgModule({
  imports: [ BrowserModule ],
  declarations: [ AppComponent ],
  exports: [ AppComponent ],
  bootstrap: [ AppComponent ]
})
export class AppModule { }

platformBrowserDynamic().bootstrapModule(AppModule);

const HEROES: Hero[] = [
  {id: 1, name: 'Bombasto'},
  {id: 2, name: 'Tornado'},
  {id: 3, name: 'Magneta'},
];

function getHeroes(): Promise<Hero[]> {
  return Promise.resolve(HEROES); // TODO: get hero data from the server;
}
```

### Small functions
สร้างฟังก์ชั่นที่มีขนาดเล็ก โดย 1 ฟังก์ชั่นไม่ควรเกิน 75 บรรทัด
ฟังก์ชั่นเล็กมีข้อดีคือ เทสง่าย reuse ง่าย อ่านง่าย ดูแลง่าย เกิดบัคยาก

**[⬆ back to top](#สารบัญ)**

## Naming
### General Naming Guidelines
### Separate file names with dots and dashes
### Symbols and file names
### Service names
### Bootstrapping
### Directive selectors
### Custom prefix for components
### Custom prefix for directives
### Pipe names
### Unit test file names
### End-to-End (E2E) test file names
### Angular NgModule names

**[⬆ back to top](#สารบัญ)**

## Coding conventions

**[⬆ back to top](#สารบัญ)**

## Application structure and NgModules

**[⬆ back to top](#สารบัญ)**

## Components

**[⬆ back to top](#สารบัญ)**

## Directives

**[⬆ back to top](#สารบัญ)**

## Services

**[⬆ back to top](#สารบัญ)**

## Data Services

**[⬆ back to top](#สารบัญ)**

## Lifecycle hooks

**[⬆ back to top](#สารบัญ)**
