 1=============
 const itemsArray = localStorage.getItem("items") ? JSON.parse(localStorage.getItem("items")) : [];
console.log(itemsArray)

document.querySelector("#enter").addEventListener("click", ()=> {
    const item = document.querySelector("#item");
    createItem(item)
})

function createItem(item) {

}

function displayDate() {
    let date = new Date();
   date = date.toString().split(" ")
//    console.log(date)
   document.querySelector("#date").innerHTML = date[1]+ " " + date[2]  + " " + date[3];
//    console.log(d)
}


window.onload = function () {
    displayDate()
}


2============================
now create function name createItem();
document.querySelector("#enter").addEventListener("click", ()=> {
    const item = document.querySelector("#item");
    createItem(item)
})

//set items in local storage;
function createItem(item) {
itemsArray.push(item.value)
localStorage.setItem("items", JSON.stringify(itemsArray))
location.reload();
}

// display items;
function displayItems() {
    let items = "";
    for(let i = 0; i < itemsArray.length; i++) {
         items += `
         <div class="item">
         <div class="input-controller">
             <textarea disabled>${itemsArray[i]}</textarea>
             <div class="edit-controller">
                 <i class="fa-solid fa-check deleteBtn"></i>
                 <i class="fa-solid fa-pen editBtn"></i>
             </div>
         </div>
         <div class="update-controller">
             <button class="saveBtn">Save</button>
             <button class="cancelBtn">Cancel</button>
         </div>
     </div>
         `;
    }
//   console.log('ite', itemsArray)
    document.querySelector('.to-do-list').innerHTML = items;
    activateDeleteListeners();
    activateEditListeners();
    activateSaveListeners();
    activateCancelListeners()

}
function activateDeleteListeners() {
    let deleteBtn = document.querySelectorAll('.deleteBtn');
    deleteBtn.forEach((item, i)=> {
        item.addEventListener("click", ()=> { deleteItem(i)})
    })
}

function deleteItem(i) {
    itemsArray.splice(i, 1);
    localStorage.setItem("items", JSON.stringify(itemsArray));
    location.reload()
}




3======================================================
