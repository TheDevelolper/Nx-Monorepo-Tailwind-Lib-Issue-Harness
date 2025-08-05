
## The Problem
Had an issue (in another repo) with tailwind in UI lib not being applied to app. 

So my good friend Richard told me that I should make a minimal example. 
I didn't want to, but I knew he was right. So I reproduced the issue, then I fixed it.

Now I can progress with my other project but first I wanted to commit this as an example for myself in the future:

## Steps To Get It Working: 

Create a workspace with an app an a UI component lib: 

``` bash
$ npx create-nx-workspace@latest
$ nx g @nx/react:lib ui-components
$ nx g @nx/react:app my-new-app  
```

Add some tailwind CSS to a component in the lib: 

```tsx
export function TailwindMultiProjectExampleUiComponents() {
  return (
    <div className="bg-blue-500 text-white">
      <h1>This should be blue with white text</h1>
    </div>
  );
}

export default TailwindMultiProjectExampleUiComponents;
```

Running the command below will allow you to specify which project to add tailwind config to. Just run it twice and *add tailwind to both projects*. 

``` bash
$ nx g setup-tailwind 
```

Now use the component in the app:

``` tsx
// Uncomment this line to use CSS modules
// import styles from './app.module.css';
import { TailwindMultiProjectExampleUiComponents } from '@tailwind-multi-project-example/ui-components';

export function App() {
  return (
    <div>
      <TailwindMultiProjectExampleUiComponents></TailwindMultiProjectExampleUiComponents>
    </div>
  );
}

export default App;

```

Now it should work for you as it does for me... All hail Richard 👑