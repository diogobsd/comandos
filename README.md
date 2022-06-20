### Git - Criar primeira commit

    git init
    git add .
    git commit -m "primeira commit"
    git remote add origin https://github.com/diogobsd/react-api-axios.git
    git push -u origin master

##### Git - Atualizar commit

    git status
    git add .
    git commit -m "segunda commit" 
    git pull (verifica se há novas atualizacoes no github para poder enviar)
    git pull origin main
    git push -u origin master

##### Git - Tags

    git tag (lista tags)
    git tag react (add tag react)
    git tad -d react (remove tag react)
    git log (exibe log)
    git push --tags
    
## Git Editor
    https://pandao.github.io/editor.md/en.html

## React + Vite

    npm create vite@latest
    Project name: nome-do-projeto
    react / react-ts
    npm i
    code .

## React Native

    npx react-native init nome_do_projeto
    ou
    npx react-native init nome_do_projeto --template react-native-template-typescript (Para TSX)
    cd nome_do_projeto
    npx react-native run-android
    
    Convert AAB to APKs rename to ZIP and extract APK
    java -jar bundletool.jar build-apks --bundle=app-release.aab --output=single-app-release.apks --mode=universal
    
    *** BUILD AAB
    
    1) sudo keytool -genkey -v -keystore my-upload-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
    * DEFINA UMA SENHA
    
    2) cp my-upload-key.keystore ./android/app
    2) copy my-upload-key.keystore android/app
    
    3) * Update android/gradle.properties
    MYAPP_UPLOAD_STORE_FILE=my-upload-key.keystore
    MYAPP_UPLOAD_KEY_ALIAS=my-key-alias
    MYAPP_UPLOAD_STORE_PASSWORD=*SUA SENHA*
    MYAPP_UPLOAD_KEY_PASSWORD=*SUA SENHA*
    
    4) * Edit: android/app/build.gradle
    signingConfigs {
        release {
            if (project.hasProperty('MYAPP_UPLOAD_STORE_FILE')) {
                storeFile file(MYAPP_UPLOAD_STORE_FILE)
                storePassword MYAPP_UPLOAD_STORE_PASSWORD
                keyAlias MYAPP_UPLOAD_KEY_ALIAS
                keyPassword MYAPP_UPLOAD_KEY_PASSWORD
            }
        }
        /*
        debug {
            storeFile file('debug.keystore')
            storePassword 'android'
            keyAlias 'androiddebugkey'
            keyPassword 'android'
        }
        */
    }
    buildTypes {
    
    cd android
    ./gradlew bundleRelease

## VS-Code

    React error 8810 - 8806:
    File -> Preferences -> Settings
    "javascript.validate.enable": false

## React extras

    npm install --save styled-components
    ou
    yarn add styled-components
    
    
    npm install @react-navigation/native
    https://reactnavigation.org/docs/getting-started
    npm install react-native-screens react-native-safe-area-context
    
    index.js
    import 'react-native-gesture-handler'; (Gestos a serem feitos na tela)
    
    npm install @react-navigation/stack
    npm install @react-navigation/bottom-tabs
    npm install @react-native-community/async-storage
    
    npm install @react-native-community/geolocation
    * Edit: \android\app\src\main\AndroidManifest.xml (Solicita localização do usuario)
        <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" ></uses>
    
    npm install react-native-permissions
    
    npm install react-native-swiper
    npm install react-native-svg
    
    npm install react-native-svg-transformer
    * Edit: \metro.config.js (faça o merge ou / cole abaixo)
    //Conforme: https://github.com/kristerkari/react-native-svg-transformer
    
    const { getDefaultConfig } = require('metro-config');
    
    module.exports = (async () => {
      const {
        resolver: { sourceExts, assetExts },
      } = await getDefaultConfig();
      return {
        transformer: {
          getTransformOptions: async () => ({
            transform: {
              experimentalImportSupport: false,
              inlineRequires: true,
            },
          }),
          babelTransformerPath: require.resolve('react-native-svg-transformer'),
        },
        resolver: {
          assetExts: assetExts.filter(ext => ext !== 'svg'),
          sourceExts: [...sourceExts, 'svg'],
        },
      };
    })();
    
    

