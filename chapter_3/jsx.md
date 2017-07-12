# JSX Rules {#jsx-rules}

1.  Maximum 2 level nesting, if you nest to much this mean you need to split your code into presentational components, this will help having cleaner and easier to maintain and extend code.
2.  Inline style over css classes
3.  Group inline styles into styles.js
4.  If you don’t need state use stateless
5.  Always use proptypes &amp; defaultProps
6.  Document you work.. Always
7.  use specific imports if possible, example use `import Btn from ‘lib/btn’` over ` import {btn} from ‘lib’`, this allows webpack *app builder* to do tree shaking and code splitting automatically without any custom configuration, which mean, it allow the build to only include the parts of the library that you need, and exclude the parts that you did not use, so your vendor.js file at the end will be as small as possible since it will only contain components that you used, and not the whole library !. this is a very useful feature that you need to utlize 