### React waifu list

Simple react app to listing waifus with simple handler.

```js
// app.js

import React from "react";
import "./App.css";

class Waifu extends React.Component {
  render() {
    return <span>Waifu {this.props.name}</span>;
  }
}

class Waifus extends React.Component {
  constructor(props) {
    super(props);
    const waifus = [
      { id: 1, name: "Emilia" },
      { id: 2, name: "Rem" },
      { id: 3, name: "Kokom1" }
    ];
    this.state = {
      waifus
    };
    this.removeWaifu = this.removeWaifu.bind(this);
  }

  removeWaifu(id) {
    let updatedWaifus = [];
    this.state.waifus.forEach(waifu => {
      if (waifu.id !== id) {
        updatedWaifus.push(waifu);
      }
    });
    this.setState({ waifus: updatedWaifus });
  }

  render() {
    return (
      <div>
        <h4>List of waifus</h4>
        {this.state.waifus.map(waifu => (
          <li key={waifu.id}>
            <Waifu name={waifu.name} />
            <button onClick={e => this.removeWaifu(waifu.id)}>Remove</button>
          </li>
        ))}
      </div>
    );
  }
}

function App() {
  return (
    <div className="App">
      <Waifus />
    </div>
  );
}

export default App;
```
