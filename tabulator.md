-   To disable paginationButtonCount, simply set it to 0.
-   To disable the First and Last buttons take the CSS approach and set display as none for these two buttons.

```js
{
  title: 'Gender',
  field: 'gender',
  width: 95,
  editor: 'select',
  editorParams: { values: ['male', 'female'] }
},
{
  title: 'Driver',
  field: 'car',
  width: 90,
  hozAlign: 'center',
  formatter: 'tickCross',
  sorter: 'boolean',
  editor: true,
},

{title:"Name", field:"name", maxWidth:200, headerMenu: headerMenu},

function headerMenu() {
    const menu = [];
    const columns = this.getColumns();

    for (let column of columns) {

        //create checkbox element using font awesome icons
        let icon = document.createElement("i");
        icon.classList.add("fas");
        icon.classList.add(column.isVisible() ? "fa-check-square" : "fa-square");

        //build label
        let label = document.createElement("span");
        let title = document.createElement("span");

        title.textContent = " " + column.getDefinition().title;

        label.appendChild(icon);
        label.appendChild(title);

        //create menu item
        menu.push({
            label: label,
            action: function (e) {
                //prevent menu closing
                e.stopPropagation();

                //toggle current column visibility
                column.toggle();

                //change menu item icon
                if (column.isVisible()) {
                    icon.classList.remove("fa-square");
                    icon.classList.add("fa-check-square");
                } else {
                    icon.classList.remove("fa-check-square");
                    icon.classList.add("fa-square");
                }
            }
        });
    }

    return menu;
}


```
