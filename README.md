let menuItems = document.querySelector('.menu-itens')
let buttonContainer = document.querySelector('.button-container')

window.addEventListener("DOMContentLoaded", () => {
    displayMenuItems(menu);
    displayMenuButtons();
})
 function displayMenuItems(menuItem) {
    let showMenu = menuItem.map((menu) => {
        return `
        <div>
            <div class="item-image">
                            <img src="${menu.image}" alt="${menu.title}" srcset="">
                        </div>
                        <div class="item-info">
                            <div class="item-title">
                                <p>${menu.title}</p>
                                <p class="price">R$${menu.price}</p>
                            </div>
                            <div class="item-description">
                                <p>${menu.description}</p>
                            </div>
                        </div>
            </div>
    
            `
    });
    showMenu = showMenu.join("");
    menuItems.innerHTML = showMenu;
 }

function displayMenuButtons() {
    const categories = menu.reduce((value, item) => {
        if(!value.includes(item.category)){
            value.push(item.category)
        }

        return value;
    }, ["all"]);

    const categoryButtons = categories.map((category) => {
        return `
        <button class="filter-button" data-id="${category}">${category}</button>
        `
    }).join("");

    buttonContainer.innerHTML += categoryButtons;

const filterButton = document.querySelectorAll(".filter-button");

filterButton.forEach((button) => {
    button.addEventListener("click", (event) => {
        const category = event.currentTarget.dataset.id;
        const menuCategory = menu.filter((menuItem) => {
            if(menuItem.category === category) {
                return menuItem;
            }
        });

        if(category === "all"){
            displayMenuItems(menu);
        } else {
            displayMenuItems(menuCategory);
        };
    });
});

}
