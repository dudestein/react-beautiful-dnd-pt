# `<DragDropContext />`

Para usar clique e arraste, você precisa ter a parte da sua árvore `React` em que você quer usar clique e arraste encapsulada em um `<DragDropContext />`. É aconselhável encapsular sua aplicação inteira em um `<DragDropContext />`. Ter `<DragDropContext />` aninhados ainda não é suportado. Você vai conseguir alcançar o objetivo de clique e arraste condicional desejado usando os props do `<Droppable />` e `<Draggable />`. Você pode pensar do `<DragDropContext />` como tendo propósito similar ao componente [react-redux Provider component](https://react-redux.js.org/api/provider)

## Props

```js
type Responders = {|
  // optional
  onBeforeDragStart?: OnBeforeDragStartResponder,
  onDragStart?: OnDragStartResponder,
  onDragUpdate?: OnDragUpdateResponder,
  // required
  onDragEnd: OnDragEndResponder,
|};

import type { Node } from 'react';

type Props = {|
  ...Responders,
  children: ?Node,
|};
```

> Veja o nosso [type guide](/docs/guides/types.md) para mais detalhes.

## Utilização básica

### Usando um componente `class`

```js
import React from 'react';
import { DragDropContext } from 'react-beautiful-dnd';

class App extends React.Component {
  onBeforeDragStart = () => {
    /*...*/
  };

  onDragStart = () => {
    /*...*/
  };
  onDragUpdate = () => {
    /*...*/
  };
  onDragEnd = () => {
    // O único que é realmente necessário
  };

  render() {
    return (
      <DragDropContext
        onBeforeDragStart={this.onBeforeDragStart}
        onDragStart={this.onDragStart}
        onDragUpdate={this.onDragUpdate}
        onDragEnd={this.onDragEnd}
      >
        <div>Hello world</div>
      </DragDropContext>
    );
  }
}
```

### Utilizando um componente `function`

```js
import React from 'react';
import { DragDropContext } from 'react-beautiful-dnd';

function App() {
  const onBeforeDragStart = useCallback(() => {
    /*...*/
  }, []);

  const onDragStart = useCallback(() => {
    /*...*/
  }, []);
  const onDragUpdate = useCallback(() => {
    /*...*/
  }, []);
  const onDragEnd = useCallback(() => {
    // the only one that is required
  }, []);

  return (
    <DragDropContext
      onBeforeDragStart={onBeforeDragStart}
      onDragStart={onDragStart}
      onDragUpdate={onDragUpdate}
      onDragEnd={onDragEnd}
    >
      <div>Hello world</div>
    </DragDropContext>
  );
}
```

## `Responders`

> `Responders` eram conhecidos anteriormente como `Hooks`

Responders são eventos de aplicação no nível de aplicação que você pode utilizar para fazer sua própria atualização de estado, de estilo, além de fazer anúncios para leitores de tela.

[Veja nosso guia de responders](/docs/guides/responders.md) para informações detalhadas sobre responders ❤️

[← Voltar para a documentação](/README.md#documentation-)
