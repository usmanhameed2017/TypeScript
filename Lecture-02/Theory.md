# SETUP TYPESCRIPT

* Initialize **Node.js** in your project.

```bash
npm init -y
```

* Install **TypeScript** as a development dependency.

```bash
npm i -D typescript
```

* Initialize **TypeScript** in your project.

```bash
npx tsc --init
```

* The above command will create a `tsconfig.json` file.

> **Note:** The `tsconfig.json` file contains the configuration for the TypeScript compiler. Some important **`compilerOptions`** include `rootDir` and `outDir`.

* **`rootDir`** specifies the **root directory** where your TypeScript source files are located.

* **`outDir`** specifies the **output directory** where the compiled JavaScript files will be generated.

### Run TypeScript Code

To compile all the **TypeScript** files inside `/src` folder and then run the generated **JavaScript** file using a single command, we can add a **`dev` script** in `package.json`.

```json
{
    "scripts": {
        "dev": "tsc && node dist/index.js"
    }
}
```

Now, we can use the following command to compile the **TypeScript** code and run the generated **JavaScript** file:

```bash
npm run dev
```

> **Note:** `tsc` compiles all the **TypeScript** files inside `/src` folder according to the configuration in `tsconfig.json`, and `node dist/index.js` runs the generated **JavaScript** file.