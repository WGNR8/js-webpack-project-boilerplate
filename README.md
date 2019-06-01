# js-webpack-project-boilerplate
Template Javascript project using babel/webpack/webpack-dev-server 

## Roteiro de construção do projeto

### Install NodeJS => https://nodejs.org/en/
    Check NodeJS => node -v
### Install Yarn => https://yarnpkg.com/pt-BR/
    Check yarn => yarn -v

### Executar comando
    yarn init

### Instalar dependencias
    yarn add @babel/cli -D
    yarn add @babel/preset-env -D
    yarn add @babel/core -D 
    yarn add @babel/plugin-proposal-object-rest-spread -D
    yarn add @babel/plugin-transform-async-to-generator
    yarn add @babel/polyfill -D
    yarn add babel-loader -D
    yarn add webpack webpack-cli -D
    yarn add webpack-dev-server -D 


### Configurar o babel
    Criar no diretorio raiz do projeto o arquivo .babelrc
    Conteúdo
        {
            "presets": ["@babel/preset-env"],
            "plugins": ["@babel/plugin-proposal-object-rest-spread"]
        }


### Criar script no package.json para executar o babel
    Conteúdo
    	"scripts": {
    		"dev": "babel -w ./src/js/main.js -o ./public/bundle.js"
	    }
    para executar 
        yarn dev

### Configurar o webpack
     Criar no diretorio raiz do projeto o arquivo webpack.config.js
     Conteúdo
        module.exports = {
            entry: [ '@babel/polyfill', './src/js/main.js' ],
            output: {
                path: __dirname + '/public',
                filename: 'bundle.js'
            },
            devServer: {
                contentBase: __dirname + '/public'
            },
            module: {
                rules: [
                    {
                        test: /\.js$/,
                        exclude: /node_modules/,
                        use: {
                            loader: 'babel-loader'
                        }
                    }
                ]
            }
        };

### Configurar o webpack-dev-server
    incluir em package.json 
     scripts: {
        "dev": "webpack-dev-server --mode=development",
		"build": "webpack --mode=production"
     }

### Criar arquivo index.html em public
### Criar arquivo main.js em src/js
