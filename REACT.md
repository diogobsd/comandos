### React
#### Guia do curso ministrado por Diogo Germano
```javascript
import React from 'react';
import { //Core components
Button,
FlatList, - para grande quantidade de conteúdo.
Image, <Image source={{uri: "https://abc/cat.png"}} style={{width: 20, height: 20}} />
Platform, Ex: Platform.OS === 'ios' ? 200 : 100
ScrollView,
StatusBar,
StyleSheet,
Text <Text> equivalente a <p>
TextInput
View - <View> equivalente a <div>
SafeAreaView, - render em iOS version 11 or 11+, wrap flex: 1
InputAccessoryView - usar com nativeID, render iOS keyboard.
ScrollView - para pequena quantidade de conteúdo
SectionList, - para segmentar pela letra do nome uma lista de nomes, d: dan, den...
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

### Manipulando a entrada de texto

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

O **ScrollView** funciona **melhor para apresentar um pequeno número de coisas de tamanho limitado**. Todos os elementos e visualizações de a ScrollViewsão renderizados, mesmo que não sejam exibidos na tela no momento. **Se você tiver uma longa lista de itens que não cabem na tela, use um FlatList**. Então, vamos aprender sobre exibições de lista a seguir.

```javascript

//ScrollView para pouca quantidade de itens

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

//FLATLIST para grande quantidade de itens

import React from 'react';
import { FlatList, StyleSheet, Text, View } from 'react-native';

const styles = StyleSheet.create({
  container: {
   flex: 1,
   paddingTop: 22
  },
  item: {
    padding: 10,
    fontSize: 18,
    height: 44,
  },
});

const FlatListBasics = () => {
  return (
    <View style={styles.container}>
      <FlatList
        data={[
          {key: 'Devin'},
          {key: 'Dan'},
          {key: 'Dominic'},
          {key: 'Jackson'},
          {key: 'James'},
          {key: 'Joel'},
          {key: 'John'},
          {key: 'Jillian'},
          {key: 'Jimmy'},
          {key: 'Julie'},
        ]}
        renderItem={({item}) => <Text style={styles.item}>{item.key}</Text>}
      />
    </View>
  );
}

export default FlatListBasics;

//SECTIONLIST

import React from 'react';
import { SectionList, StyleSheet, Text, View } from 'react-native';

const styles = StyleSheet.create({
  container: {
   flex: 1,
   paddingTop: 22
  },
  sectionHeader: {
    paddingTop: 2,
    paddingLeft: 10,
    paddingRight: 10,
    paddingBottom: 2,
    fontSize: 14,
    fontWeight: 'bold',
    backgroundColor: 'rgba(247,247,247,1.0)',
  },
  item: {
    padding: 10,
    fontSize: 18,
    height: 44,
  },
})

const SectionListBasics = () => {
    return (
      <View style={styles.container}>
        <SectionList
          sections={[
            {title: 'D', data: ['Devin', 'Dan', 'Dominic']},
            {title: 'J', data: ['Jackson', 'James', 'Jillian', 'Jimmy', 'Joel', 'John', 'Julie']},
          ]}
          renderItem={({item}) => <Text style={styles.item}>{item}</Text>}
          renderSectionHeader={({section}) => <Text style={styles.sectionHeader}>{section.title}</Text>}
          keyExtractor={(item, index) => index}
        />
      </View>
    );
}

export default SectionListBasics;

```
### Platform
```javascript
import { Platform, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  height: Platform.OS === 'ios' ? 200 : 100
});
```
Há também um Platform.selectmétodo disponível, que dado um objeto onde as chaves podem ser uma de 'ios' | 'android' | 'native' | 'default'

```javascript
import { Platform, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: {
    flex: 1,
    ...Platform.select({
      ios: {
        backgroundColor: 'red'
      },
      android: {
        backgroundColor: 'green'
      },
      default: {
        // other platforms, web for example
        backgroundColor: 'blue'
      }
    })
  }
});
```

```javascript
const Component = Platform.select({
  ios: () => require('ComponentIOS'),
  android: () => require('ComponentAndroid')
})();

<Component />;

const Component = Platform.select({
  native: () => require('ComponentForNative'),
  default: () => require('ComponentForWeb')
})();

<Component />;

import { Platform } from 'react-native';

if (Platform.Version === 25) {
  console.log('Running on Nougat!');
}

import { Platform } from 'react-native';

const majorVersionIOS = parseInt(Platform.Version, 10);
if (majorVersionIOS <= 9) {
  console.log('Work around a change in behavior');
}
```
