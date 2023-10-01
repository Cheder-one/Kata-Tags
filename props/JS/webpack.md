```
// Импортируем необходимые модули
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");

// Определяем режим сборки (development или production)
const mode = process.env.NODE_ENV || "development";
const devMode = mode === "development";

// Определяем цель сборки: web для development, browserslist для production
const target = devMode ? "web" : "browserslist";

// Определяем инструмент для генерации sourcemaps (карт исходного кода)
const devtool = devMode ? "source-map" : undefined;

module.exports = {
  mode,
  target,
  devtool,
  // Конфигурация для локального сервера разработки
  devServer: {
    port: 4221,
    open: true,
    hot: true
  },
  // Определяем точку входа для приложения
  entry: path.resolve(__dirname, "src", "index.js"),
  // Определяем место, куда будут сохранены файлы сборки
  output: {
    path: path.resolve(__dirname, "dist"),
    clean: true, // Очищать папку dist перед каждой сборкой
    filename: "[name].[contenthash].js", // Название файла JavaScript
    assetModuleFilename: "assets/[name][ext]" // Название файлов ресурсов (картинки, шрифты и т.д.)
  },
  // Плагины, используемые в сборке
  plugins: [
    // Плагин для генерации HTML-файла
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname, "src", "index.html")
    }),
    // Плагин для извлечения CSS в отдельные файлы
    new MiniCssExtractPlugin({
      filename: "[name].[contenthash].css"
    })
  ],
  // Правила обработки различных типов файлов
  module: {
    rules: [
      {
        test: /\.html$/i,
        loader: "html-loader" // Загрузчик для HTML файлов
      },
      {
        test: /\.(c|sa|sc)ss$/i,
        use: [
          devMode ? "style-loader" : MiniCssExtractPlugin.loader, // Используем либо style-loader, либо MiniCssExtractPlugin.loader в зависимости от режима
          "css-loader", // Загрузчик для CSS файлов
          {
            loader: "postcss-loader",
            options: {
              postcssOptions: {
                plugins: [require("postcss-preset-env")] // Плагин для обработки CSS с использованием postcss
              }
            }
          },
          "group-css-media-queries-loader", // Плагин для группировки медиа-запросов в CSS
          {
            loader: "resolve-url-loader" // Плагин для корректной обработки относительных путей в CSS
          },
          {
            loader: "sass-loader",
            options: {
              sourceMap: true // Включение генерации sourcemaps для SASS
            }
          }
        ]
      },
      {
        test: /\.woff2?$/i,
        type: "asset/resource",
        generator: {
          filename: "fonts/[name][ext]" // Конфигурация для обработки шрифтов
        }
      },
      {
        test: /\.(jpe?g|png|webp|gif|svg)$/i,
        use: devMode
          ? []
          : [
              {
                loader: "image-webpack-loader",
                options: {
                  mozjpeg: {
                    progressive: true
                  },
                  optipng: {
                    enabled: false
                  },
                  pngquant: {
                    quality: [0.65, 0.9],
                    speed: 4
                  },
                  gifsicle: {
                    interlaced: false
                  },
                  webp: {
                    quality: 75
                  }
                }
              }
            ],
        type: "asset/resource" // Обработка изображений и других ресурсов
      },
      {
        test: /\.m?js$/i,
        exclude: /(node_modules|bower_components)/,
        use: {
          loader: "babel-loader", // Загрузчик для обработки JavaScript с использованием Babel
          options: {
            presets: ["@babel/preset-env"]
          }
        }
      }
    ]
  }
};
```

