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

## React + Vite

    npm create vite@latest
    Project name: nome-do-projeto
    react / react-ts
    npm i
    code .

## React Native

    npx react-native init app01 (build project app01)
    cd app01
    npx react-native run-android

## VS-Code

    React error 8810 - 8806:
    File -> Preferences -> Settings
    "javascript.validate.enable": false
