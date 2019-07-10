

```js
import React, { Fragment, useState } from "react";
import ReactDOM from "react-dom";

import "./styles.css";
import { freemem } from "os";

function App() {
  const languages = [
    {
      name: "Ruby",
      _self: "http://localhost:8080/languages/1"
    },
    {
      name: "Java",
      _self: "http://localhost:8080/languages/2"
    }
  ];

  const [selectedLanguages, setSelectedLanguages] = useState({});

  function handleCheckboxChange(e) {
    const nextLanguages = { ...selectedLanguages };
    nextLanguages[e.currentTarget.name] = e.currentTarget.checked;
    setSelectedLanguages(nextLanguages);
  }

  function getSelectedLanguages() {
    return Object.keys(selectedLanguages).filter(
      (key, _) => selectedLanguages[key]
    );
  }

  function makePsForEachSelectedLangauge() {
    return getSelectedLanguages().map(language => <p>{language}</p>);
  }

  const languageCheckBoxes = languages.map(language => {
    return (
      <Fragment>
        <input
          type="checkbox"
          onChange={handleCheckboxChange}
          id={language._self}
          name={language._self}
        />
        <label for={language._self}>{language.name}</label>
      </Fragment>
    );
  });

  return (
    <Fragment>
      {languageCheckBoxes}
        {makePsForEachSelectedLangauge()}
    </Fragment>
  );
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

![Imgur](https://i.imgur.com/ODBtAcZ.png)

![img](https://i.imgur.com/V11aBMI.png)
