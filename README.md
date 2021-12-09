# JavaScript-ES6

Configuração do Ambiente
Antes de tudo, precisamos ter o Node.js instalado.

https://nodejs.org

Vamos criar um diretório para o nosso código.

Dentro dele, abriremos nosso terminal e daremos o comando

$ npm init

Isto irá iniciar o arquivo package.json, onde teremos nossas dependências. Coloque as seguintes dependências em seu arquivo:

 "devDependencies": {
    "babel-core": "^6.5.2",
    "babel-loader": "^6.2.3",
    "babel-polyfill": "^6.3.14",
    "babel-preset-es2015": "^6.5.0",
    "babel-preset-stage-0": "^6.5.0",
    "webpack": "^1.12.6"
  },
 "scripts": {
    "build": "./node_modules/.bin/webpack --config webpack.config.js"
  }
  
  Com essas dependências teremos o Babel e WebPack. 
  
  Agora no terminal, execute o comando
  
  $ npm install
  
  Para quem não está no Windows, lembre-se de usar “sudo” antes do comando “npm install”.

Teremos agora que criar um arquivo ”webpack.config.js”. É esse arquivo que o WebPack vai usar para ver as nossas configurações. Nele colocaremos o seguinte conteúdo:

module.exports = {
    entry: './scripts/app.js',
    output: {
        path: './dist',
        filename: 'app.js'
    },
    devtool: 'source-map' ,
    module: {
        loaders: [
            {
                test: /\.jsx?$/,
                exclude: /(node_modules|bower_components)/,
                loader: 'babel',
                query: {
                    presets: ['es2015', 'stage-0']
                }
            }
        ]

    }
};
Criaremos um diretório “scripts“ com um arquivo chamado “app.js” dentro. Este será o arquivo inicial de nossa aplicação.

Criaremos um diretório “dist”. Aqui ficará o arquivo de saída após a transpilação.

Para iniciar o WebPack, basta executar o comando:
$ npm run build
