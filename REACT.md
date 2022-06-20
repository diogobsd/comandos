### React
####Guia e Ref. do curso ministrado por Diogo Germano
```javascript
import React from 'react';
import { //Core components
Button,
Image, <Image source={{uri: "https://abc/cat.png"}} style={{width: 20, height: 20}} />
ScrollView,
StatusBar,
StyleSheet,
Text <Text> equivalente a <p>
TextInput
View - <View> equivalente a <div>
SafeAreaView, - render em iOS version 11 or 11+, wrap flex: 1
InputAccessoryView - usar com nativeID, render iOS keyboard.
ScrollView
} from 'react-native';

//EXEMPLOS

const App = () => {
  return (
    <SafeAreaView style={styles.container}>
      <Text style={styles.text}>Page content</Text>
    </SafeAreaView>
	<InputAccessoryView nativeID={inputAccessoryViewID}>
        <Button
          onPress={() => setText(initialText)}
          title="Clear text"
        />
     </InputAccessoryView>

  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
  text: {
    fontSize: 25,
    fontWeight: '500',
  }
});

export default App;

//EXEMPLOS

import React from 'react';
import { Text, View } from 'react-native';

const Fish = () => {
  return (
    <View>
      <Text>Eu sou um peixe e sou componente filho de Cafe</Text>
    </View>
  );
}

const Cafe = () => {
  return (
    <View>
      <Text>Bem vindo! sou um componente pai</Text>
      <Fish />
      <Fish />
    </View>
  );
}

export default Cafe;

//State é útil para lidar com dados que mudam ao longo do tempo ou que vêm da interação do usuário. State dá memória aos seus componentes!

//Você pode adicionar estado a um componente chamando o Hook do ReactuseState . Um Hook é um tipo de função que permite que você “se conecte” aos recursos do React. Por exemplo, useStateé um Hook que permite adicionar estado aos componentes da função.

import React, { useState } from "react";
import { Button, Text, View } from "react-native";

const Cat = (props) => {
  const [isHungry, setIsHungry] = useState(true);

  return (
    <View>
      <Text>
        I am {props.name}, and I am {isHungry ? "hungry" : "full"}!
      </Text>
      <Button
        onPress={() => {
          setIsHungry(false);
        }}
        disabled={!isHungry}
        title={isHungry ? "Pour me some milk, please!" : "Thank you!"}
      />
    </View>
  );
}

const Cafe = () => {
  return (
    <>
      <Cat name="Munkustrap" />
      <Cat name="Spot" />
    </>
  );
}

export default Cafe;

//Chamar useStatefaz duas coisas:

//ele cria uma “variável de estado” com um valor inicial – neste caso a variável de estado é isHungrye seu valor inicial é true

//ele cria uma função para definir o valor dessa variável de estado—setIsHungry

//Não importa os nomes que você usa. Mas pode ser útil pensar no padrão como [<getter>, <setter>]

```

###Manipulando a entrada de texto

```javascript
//TextInput é um componente principal que permite ao usuário inserir texto. Tem uma onChangeText prop que pega uma função para ser chamada toda vez que o texto muda, e uma onSubmitEditing prop que pega uma função para ser chamada quando o texto é submetido.

import React, { useState } from 'react';
import { Text, TextInput, View } from 'react-native';

const PizzaTranslator = () => {
  const [text, setText] = useState('');
  return (
    <View style={{padding: 10}}>
      <TextInput
        style={{height: 40}}
        placeholder="Type here to translate!"
        onChangeText={newText => setText(newText)}
        defaultValue={text}
      />
      <Text style={{padding: 10, fontSize: 42}}>
        {text.split(' ').map((word) => word && '🍕').join(' ')}
      </Text>
    </View>
  );
}

export default PizzaTranslator;

```

### ScrollView

ScrollViews pode ser configurado para permitir a paginação através de visualizações usando gestos de deslizar usando os pagingEnabled adereços. Deslizar horizontalmente entre as visualizações também pode ser implementado no Android usando o componente ViewPager .

No iOS, um ScrollView com um único item pode ser usado para permitir que o usuário amplie o conteúdo. Configure os adereços maximumZoomScale e minimumZoomScale e seu usuário poderá usar gestos de pinçar e expandir para aumentar e diminuir o zoom.

O ScrollView funciona melhor para apresentar um pequeno número de coisas de tamanho limitado. Todos os elementos e visualizações de a ScrollViewsão renderizados, mesmo que não sejam exibidos na tela no momento. Se você tiver uma longa lista de itens que não cabem na tela, use um FlatList. Então, vamos aprender sobre exibições de lista a seguir.

```javascript
import React from 'react';
import { Image, ScrollView, Text } from 'react-native';

const logo = {
  uri: 'https://reactnative.dev/img/tiny_logo.png',
  width: 64,
  height: 64
};

const App = () => (
  <ScrollView>
    <Text style={{ fontSize: 96 }}>Scroll me plz</Text>
    <Image source={logo} />
    <Image source={logo} />
    <Text style={{ fontSize: 96 }}>If you like</Text>
    <Image source={logo} />
    <Image source={logo} />
    <Text style={{ fontSize: 96 }}>Scrolling down</Text>
    <Image source={logo} />
    <Text style={{ fontSize: 96 }}>What's the best</Text>
    <Image source={logo} />
    <Image source={logo} />
    <Text style={{ fontSize: 96 }}>Framework around?</Text>
    <Image source={logo} />
    <Text style={{ fontSize: 80 }}>React Native</Text>
  </ScrollView>
);

export default App;
```

