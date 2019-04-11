<!-- *
 * @Author: Arunabho Majumder
 * @Date: 2019-04-11 18:19:13
 * @Last Modified by: iarunabho
 * @Last Modified time: 2019-04-11 18:19:36 -->

# For Downloading the code

- Open your terminal and paste ->
  `git clone https://github.com/iarunabho/Save-a-file-Local.git`

# CODE

![#f03c15](https://placehold.it/15/f03c15/000000?text=+) `JS`

```javascript
var input = document.querySelector('input[type=file]');
var text = document.querySelector('textarea');
var button = document.querySelector('input[type=button]');
var name;

input.onchange = function(e) {
  var reader = new FileReader();
  reader.onload = function(event) {
    text.value = event.target.result;
    button.disabled = false;
  };
  name = e.target.files[0].name;
  reader.readAsText(
    new Blob([e.target.files[0]], {
      type: 'application/json'
    })
  );
};

button.onclick = function(e) {
  e.preventDefault();
  var blob = new Blob([text.value], {
    type: 'application/json'
  });
  var a = document.createElement('a');
  a.download = name;
  a.href = URL.createObjectURL(blob);
  document.body.appendChild(a);
  a.click();
  text.value = '';
  input.value = '';
  button.disabled = true;
  document.body.removeChild(a);
};
```

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) `HTML`

```Html
<form>
  <input type="file" />
  <br />
  <textarea></textarea>
  <br />
  <input type="button" disabled="true" value="Save" />
</form>
```

![#1589F0](https://placehold.it/15/1589F0/000000?text=+) `CSS`

```CSS
textarea {
  white-space: pre;
  width: 400px;
  height: 300px;
}
```

For more queries you can check this [link](https://stackoverflow.com/questions/34034475/edit-and-save-a-file-locally-with-js)
