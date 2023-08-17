# Tutorial de Uso de TypeScript en Angular

Link al curso completo en Youtube:
[TYPESCRIPT DESDE CERO POR SERGIE CODE](https://youtu.be/UTA5bykCx2c)

Este tutorial te guiará a través de los pasos para usar TypeScript en una aplicación Angular. Aprenderás cómo definir modelos de datos, crear componentes y trabajar con condicionales en Angular utilizando TypeScript. El ejemplo se centrará en la visualización de una lista de alumnos y cursos en dos tablas diferentes en función de una condición.

## Paso 1: Configuración del Proyecto

1.  Crea un nuevo proyecto Angular usando el Angular CLI:
    
```
ng new mi-proyecto
```
    
2.  Navega al directorio del proyecto:
```
cd mi-proyecto
```
    

## Paso 2: Definición de Modelos

1.  Crea dos archivos en la carpeta `src/app` para definir los modelos de datos:
    
**alumno.model.ts:**
    
```
export interface Alumno {
        nombre: string;
        apellido: string;
        promedio: number;
    }
```
    
 **curso.model.ts:**
    
```
export interface Curso {
        materia: string;
        dificultad: number;
        requiere: string;
    }
```
    

## Paso 3: Creación de Componentes

1.  Crea tres componentes en la carpeta `src/app` utilizando el Angular CLI:
    
```
ng generate component tabla-alumnos
ng generate component tabla-cursos
ng generate component app
```
    
2.  En el archivo `app.component.html`, agrega el siguiente código para mostrar las tablas de alumnos y cursos condicionalmente:
    
```
<div class="container mt-5">
<app-tabla-alumnos *ngIf="!cursos"></app-tabla-alumnos>
<app-tabla-cursos *ngIf="cursos"></app-tabla-cursos>
   
<button class="btn btn-primary" (click)="handleCambio()">Cambiar de tabla</button>
</div>
```
    

## Paso 4: Implementación de Componentes

1.  Abre `tabla-alumnos.component.html` y agrega el siguiente código para mostrar la tabla de alumnos:
    
```
<h1>Alumnos:</h1>
    <table class="table table-dark">
        <thead>
          <tr>
            <th scope="col">Nombre</th>
            <th scope="col">Apellido</th>
            <th scope="col">Promedio</th>
          </tr>
        </thead>
        <tbody>
          <tr *ngFor="let alumno of alumnos">
            <td>{{ alumno.nombre }}</td>
            <td>{{ alumno.apellido }}</td>
            <td>{{ alumno.promedio }}</td>
          </tr>
        </tbody>
     </table>
```
    
2.  En `tabla-cursos.component.html`, agrega el siguiente código para mostrar la tabla de cursos:
    
```
<h1>Cursos:</h1>
    <table class="table table-dark">
        <thead>
          <tr>
            <th scope="col">Materia</th>
            <th scope="col">Dificultad</th>
            <th scope="col">Requiere</th>
          </tr>
        </thead>
        <tbody>
          <tr *ngFor="let curso of cursos">
            <td>{{ curso.materia }}</td>
            <td>{{ curso.dificultad }}</td>
            <td>{{ curso.requiere }}</td>
          </tr>
        </tbody>
      </table>
```
    
3.  En `app.component.ts`, implementa la lógica para alternar entre las tablas de alumnos y cursos:
    
```
import { Component } from '@angular/core';
    import { Alumno } from './alumno.model';
    import { Curso } from './curso.model';
    
    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })
    export class AppComponent {
      alumnos: Alumno[] = [
        // Agrega algunos datos de alumnos aquí
      ];
    
      cursos: Curso[] = [
        // Agrega algunos datos de cursos aquí
      ];
    
      handleCambio(): void {
        this.cursos = !this.cursos;
      }
    }
```
    

## Paso 5: Visualización de Resultados

1.  En cada modelo (`alumno.model.ts` y `curso.model.ts`), agrega algunos datos de ejemplo para los alumnos y cursos.
    
2.  Ejecuta el servidor de desarrollo para ver la aplicación en el navegador:
    
```
npm start
```
    
3.  Navega a `http://localhost:4200` en tu navegador web.
