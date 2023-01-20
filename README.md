# stack-react ♦ React + Sass + Webpack
Stack para React con unas cositas más

# :package: React + Sass + Webpack

### **Estructura de carpetas**
    my-project/
    ├── node_modules/
    ├── public/
    │   └── index.html
    ├── src/
    │   └── index.js
    ├── components/
    │   └── App.jsx
    ├── containers/
    │   └── Layout.jsx
    ├── styles/
    │   ├── global.scss
    │   └── _vars.scss
    ├── LICENSE
    ├── package.json
    ├── package-lock.json
    ├── .gitignore
    ├── .babelrc
    └── webpack.config.js

## **Comandos React + Sass + Webpack personal**

### **Git**
    git init

### **npm**
    npm init
    npm install react react-dom


### **Babel:**
    npm install @babel/core @babel/preset-env @babel/preset-react 

### **Webpack:**
    npm install webpack webpack-cli webpack-dev-server 

### **HTML plugin:**
    npm install babel-loader html-loader html-webpack-plugin

## **Archivos de configuración**

### **"webpack.config.js"**
    const path = require('path');
    const HtmlWebpackPlugin = require('html-webpack-plugin');
    const MiniCssExtractPlugin = require('mini-css-extract-plugin');
    
    module.exports = {
    	entry: './src/index.js',
    	output: {
    		path: path.resolve(__dirname, 'dist'),
    		filename: 'bundle.js',
    	},
    	mode: 'development',
    	resolve: {
    		extensions: ['.js', '.jsx'],
    	},
    	module: {
    		rules: [
			{
				test: /\.(js|jsx)$/,
				exclude: /node_modules/,
				use: {
					loader: 'babel-loader'
				}
			},
			{
				test: /\.html$/,
				use: [
					{
						loader: 'html-loader'
					}
				]
			},
			{
				test:/\.(css|scss)$/,
				use: [
					"style-loader",
					"css-loader",
					"sass-loader",
				],
			}
    		]
    	},
    	plugins: [
    		new HtmlWebpackPlugin({
    			template: './public/index.html',
    			filename: './index.html'
    		}),
    		new MiniCssExtractPlugin({
    			filename: '[name].css'
    		}),
    	],
    }
    
### **".gitignore"**
    node_modules
    
### **".babelrc"**
    {
      "presets": [
        "@babel/preset-env",
        "@babel/preset-react"
      ]
    }
### **"package.json"**
    {
      "name": "prueba-frontend-beyserin",
      "version": "1.0.0",
      "description": "Prueba de desarrollo frontend para beyserin Consulting",
      "main": "src/index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "start": "webpack serve --open",
        "build": "webpack --mode production"
      },
      "keywords": [
        "react",
        "javascript"
      ],
      "author": "Jair Erazo <jair.erazo.dev@proton.me>",
      "license": "MIT",
      "bugs": {
        "url": "https://github.com/jairerazodev/prueba-frontend-beyserin/issues"
      },
      "homepage": "https://github.com/jairerazodev/prueba-frontend-beyserin#readme",
      "dependencies": {
        "@babel/core": "^7.15.0",
        "@babel/preset-env": "^7.15.0",
        "@babel/preset-react": "^7.14.5",
        "babel-loader": "^8.2.2",
        "html-loader": "^2.1.2",
        "html-webpack-plugin": "^5.3.2",
        "react": "^17.0.2",
        "react-dom": "^17.0.2",
        "webpack": "^5.50.0",
        "webpack-cli": "^4.8.0",
        "webpack-dev-server": "^4.0.0"
      },
      "devDependencies": {
        "css-loader": "^6.2.0",
        "mini-css-extract-plugin": "^2.2.0",
        "sass": "^1.38.0",
        "sass-loader": "^12.1.0",
        "style-loader": "^3.2.1"
      }
    }

## **Archivos base del proyecto**

### **"./public/index.html"**
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
    </head>
    <body>
        <div id="app"></div>
    </body>
    </html>    

### **"./src/index.js"**
    import React from 'react';
    import ReactDOM from 'react-dom';
    import App from '../components/App';
    
    ReactDOM.render(<App />, document.getElementById('app'));   

### **"./components/App.jsx"**
    import React from 'react';
    
    const App = () => {
        return(
          <h1>
            Hey
          </h1>
        );
    }
    
    export default App; 

## **Configurar Sass**

    npm i mini-css-extract-plugin css-loader style-loader sass sass-loader -D
    
> Es indispensable importar las el plugin en el archivo webpack.config.js

    const MiniCssExtractPlugin = require('mini-css-extract-plugin');
    
> Támbien indispensable las configuraciones en las reglas  del css antes de los plugins.

    {
    	test:/\.(css|scss)$/,
    	use: [
    		"style-loader",
    		"css-loader",
    		"sass-loader",
    	],
	}
	
> Por último añadir la configuracíon del plugin.

    new MiniCssExtractPlugin({
		filename: '[name].css'
		}),
		
## **Importar global.scss a App.jsx**
    import '../styles/global.scss';

## **Inicializar entorno de desarrollo**
    npm i
    npm run start

Para automatizar el proceso de desarrollo y despliegue de tu proyecto con React y Sass utilizando Webpack, puedes seguir los siguientes pasos:

Crea un archivo llamado "script.sh" en la raíz del proyecto y agrega los siguientes comandos:

### Inicializa un repositorio Git
    git init

### Crea un archivo package.json y responde a las preguntas del asistente de npm
    npm init

### Instala las dependencias de React
    npm install react react-dom

### Instala las dependencias de Babel
    npm install @babel/core @babel/preset-env @babel/preset-react

### Instala las dependencias de Webpack
    webpack-cli webpack-dev-server

### Instala el plugin HTML para Webpack
    npm install babel-loader html-loader html-webpack-plugin

### Instala el plugin de extracción de CSS para Webpack
    npm install mini-css-extract-plugin

### Inicia el servidor de desarrollo de Webpack
    npm start

Crea un archivo `".gitignore"` en la raíz del proyecto y agrega la siguiente línea para excluir la carpeta `"node_modules"` del repositorio Git:

    node_modules
    Crea un archivo ".babelrc" en la raíz del proyecto y agrega la siguiente configuración para Babel:
    Copy code
    {
    "presets": [
        "@babel/preset-env",
        "@babel/preset-react"
    ]
    }

Crea un archivo `"webpack.config.js"` en la raíz del proyecto y agrega la siguiente configuración para Webpack:

        const path = require('path');
        const HtmlWebpackPlugin = require('html-webpack-plugin');
        const MiniCssExtractPlugin = require('mini-css-extract-plugin');

        module.exports = {
        entry: './src/index.js',
        output: {
            path: path.resolve(__dirname, 'dist'),
            filename: 'bundle.js',
        },
        mode: 'development',
        resolve: {
            extensions: ['.js', '.jsx'],
        },
        module: {
            rules: [
            {
                test: /\.(js|jsx)$/,
                exclude: /node_modules/,
                use: {
                loader: 'babel-loader'
                }
            },
            {
            
            test: /\.html$/,
            use: [
            {
                loader: 'html-loader'
            }
            ]
        },
        {
            test:/\.(css|scss)$/,
            use: [
            "style-loader",
            "css-loader",
            "sass-loader",
            ],
        }
        ]
    },
    plugins: [
        new HtmlWebpackPlugin({
        template: './public/index.html',
        filename: './index.html'
        }),
        new MiniCssExtractPlugin({
        filename: '[name].css'
        }),
    ],
    }

Crea la estructura de carpetas y archivos siguiendo el esquema mencionado en el enunciado.

Para desplegar el proyecto, agrega el siguiente comando al final del archivo `"script.sh":`

# Compila el proyecto en modo producción
    npm run build

Para ejecutar el script de automatización, abre una terminal en la raíz del proyecto y ejecuta el siguiente comando:

    bash script.sh

Con estos pasos, podrás automatizar el proceso de desarrollo y despliegue de tu proyecto con React y Sass utilizando Webpack.
