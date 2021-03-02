1-Instalando dependecias de desarrollo

babel-cli babel-core babel-loader babel-preset-react babel-preset-env css-loader 
html-webpack-plugin node-sass sass-loader style-loader
webpack webpack-dev-middleware webpack-livereload-plugin -D


2-Instalando las dependencias
express react react-dom


3-Creamos src y web pack
Dentro del proyecto creamos una carpeta donde se destinen los proyectos de Front y Back End
ademas en la ruta principal creamos el archivo webpack.config.js

4-Configuramos Babel
creamos un archivo llamado .babelrc
dentro configuramos lo siguiente
{
	"preset":["env","react"]
}


5-Configuramos webpack

import webpack from 'webpack';
import htmlWebpackPlugin from 'html-webpack-plugin';
import LiveReloadPlugin from 'webpack-livereload-plugin';

export default {
  entry: './src/client/index.js',
  output: {
    path: '/',
    filename: 'bundle.js'
  },
  module: {
    rules: [
      {
        use: 'babel-loader',
        test: /\.js$/,
        exclude: /node_modules/
      },
      {
        use: ['style-loader', 'css-loader'],
        test: /\.css$/
      },
      {
        test: /\.scss$/,
        use: [
          {
            loader: 'style-loader'
          },
          {
            loader: 'css-loader', options: {
              sourceMap: true
            }
          },
          {
            loader: 'sass-loader', options: {
              sourceMap: true
            }
          }
        ]
      }
    ]
  },
  plugins: [
    new htmlWebpackPlugin({
      template: 'src/client/index.html'
    }),
    new LiveReloadPlugin()
  ]
}







6-Creamos la carpeta client y la carpeta server
En el cliente crearemos todo el proyecto de react 
en el server todo el proyecto de NodeJs


7-Configuramos los Scripts de npm
  "dev":"babel-node src/server/server"




