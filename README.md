

# 3D geometry analysis on the Web: Creating Websites with Rhino.Compute, Vue, and Three.js. 

This is repository with materials used for building Miniature program of runing 3D geometry analysis in web environment. 

To build a custom web interface for real-time control and display of Grasshopper definitions to run the 3D geometry analysis. In this project, Grasshopper scripts was prepared to run on the web with Rhino.Compute. Utilizing basics of Vue.js, a user-friendly web framework, enabling to create reusable web interfaces that can control Grasshopper definition inputs. 



## Prerequisites
- Rhino 7
- Hops
- Visual Studio Code/ Cursor/ Windsurf
- Node
- Git
- Github


## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

 
## Run project locally


### Start Rhino.Compute

Start  local Rhino.Compute server either by running your Grasshopper (with Hops installed) or by directly starting Rhino.Compute from `%AppData%\McNeel\Rhinoceros\packages\7.0\Hops\0.16.2\compute.geometry\compute.geometry`. 
Rhino.Compute is running if you can see in your console `Listening on..`

![image](https://github.com/just-ajs/aectech-2024-kpf-ttcore-worskhop/assets/35227625/f41a0b9b-d4a8-4e07-9fdf-4051a14b02a8)

When Rhino.Compute running, have a look at the number of the localhost. The example above has a localhost number 8081. This number needs to match the host number in the `source/scripts/compute.js` file (line 6).


![image](https://github.com/just-ajs/aectech-2024-kpf-ttcore-worskhop/assets/35227625/85246a48-a91d-41e6-aaca-4654cabc79e4)

If Rhino.Compute localhost number is different, adjust `compute.js` file to match it. 


### Run front-end

In the terminal, run following commands:

#### Install packages needed to run the project

```sh
npm install
```

#### Compile and Hot-Reload for Development

```sh
npm run dev
```

#### Compile and Minify for Production

```sh
npm run build
```


