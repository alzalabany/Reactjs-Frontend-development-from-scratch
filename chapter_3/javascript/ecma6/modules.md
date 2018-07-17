### Moduler system and commonJS.

##### History:
  - how we used to split javascript code before exsistence of moduler systems

##### Evolution of Modules in JavaScript

- ECMA 5
  - CommonJS
    - used in node js, developed extensivly for sync operations and server imports
  - AMD
    - most popular is RequireJs, this was developed with Async in mind.
 
 - ECMA 6 a.k.a: Best of both worlds:

#### Rules.. we love Rules

- Imports are read-only
- Exports are cached, single instance exported and side effects will run only once
- Must be defined @ top scope
- It scoped, & this is undefined
- Re-exporting
  - named export *|{foo, bar} from 'foo-bar';
  - default export { default } from 'foo-bar';

#### Code splitting and Async loading

System.import

#### comparison between Modules and Script tags

|Pint of Comparison |Scripts  |	Modules |
| ------------- |:-------------:|:-------------:|
HTML element	  | <script>	    | <script type="module">|
strict mode	    | off           |	on  |
Scope           |	global	| local to module|
Executed        |	synchronously|	asynchronously|
Programmatic imports |  yes |	yes |
