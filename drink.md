---
layout: default
title: Drink
---

<h3>Get nutritional label on a Drink</h3>
<form id="formToGetOneDrinkDetail">
    <label for="Drink"><b>Drink name to get details:</b></label>
    <input type="text" id="Drink" name="Drink" /><br /><br />
    <button type="submit" value="btnToGetDrinkDetail" id="get_drinky">GetDrinkDetails</button>
    <div id="getOneDrinkDetailResponse"></div>
</form>
<br><br><br>


<h3>Create a new Drink</h3>
<form id="myForm">
    <label for="Drink">New Drink name:</label>
    <input type="text" id="Drink" name="Drink" /><br /><br />
    <label for="Calories">Calories:</label>
    <input type="text" id="Calories" name="Calories" /><br /><br />
    <button type="submit" value="Submit" id="create_drinky">CreateNewDrink</button>
</form>
<br><br>

<h3>All Drinks</h3>
<table id="DrinkTable">
    <!-- Table headers go here -->
    <thead>
        <tr>
            <th>Drink Name</th>
            <th>Calories</th>
            <th>Edit</th>
            <th>Delete</th>
        </tr>
    </thead>
</table>

<div id="editModalBackdrop" class="modal-backdrop">
	<div id="editModal" class="modal-content">
		<button id="closeModal" class="close-modal">X</button>
		<form id="editForm">
			<label for="editDrinkName">Drink Name:</label>
			<input type="text" id="editDrinkName" name="editDrinkName" /><br /><br />
            <label for="editCalories">Calories:</label>
			<input type="text" id="editCalories" name="editCalories" /><br /><br />
			<input type="submit" value="Update" />
		</form>
	</div>
</div>

<style>
	.modal-backdrop {
		display: none;
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.7);
		z-index: 1;
	}

	.modal-content {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		background: #272726;
		padding: 40px;
		z-index: 2;
	}

	.close-modal {
		position: absolute;
		top: 10px;
		right: 10px;
		cursor: pointer;
		background: none;
		border: none;
		font-size: 24px;
		color: white;
	}

	.wrapper,
	section {
		max-width: 900px;
	}
</style>


<script type="module">
    import { uri, options } from '{{site.baseurl}}/assets/js/api/config.js';

    const API_URL = uri + '/api/drinks/'
    const createbutton = document.getElementById("create_drinky")
    createbutton.addEventListener("click", submitForm);

    const getDrinkbutton = document.getElementById("get_drinky")
    getDrinkbutton.addEventListener("click", getOneDrink);

    //Get all drink items
    function loadItems() {
        fetch(API_URL, {
            method: 'GET'
            // headers: options.headers,
            //body: JSON.stringify(body),
        }) 
        .then((response) => response.json())
        .then(data => {
            displayItems(data);
        })
        .catch(error => {
            console.error("Error calling get all drinks:", error)
        });
    }

    function displayItems(items) {
            const table = document.getElementById("DrinkTable");

            items.forEach((drink) => {
                const row = table.insertRow();
                row.setAttribute("data-id", drink.id);

                ["drinkName", "calories"].forEach((field) => {
                    const cell = row.insertCell();
                    cell.innerText = drink[field];
                });

                const editCell = row.insertCell();
                const editButton = document.createElement("button");
                editButton.innerHTML = "Edit";
                editButton.addEventListener("click", () => editDrink(drink.drinkName, drink.calories));
                editCell.appendChild(editButton);

                const deleteCell = row.insertCell();
                const deleteButton = document.createElement("button");
                deleteButton.innerText = "Delete";
                //deleteButton.addEventListener("click", () => deleteDrink(drink.id, row));
                deleteButton.addEventListener("click", () => deleteDrink(drink.drinkName,row));
                deleteCell.appendChild(deleteButton);
            })
            .catch((error) => {
            console.error('Error:', error);
        });
    }

    // function to show Edit drink form pop up
    function editDrink(drinkName, calories) {
        // Implement edit functionalitydrinkName based on the drinkId
        console.log('Edit Drink:', drinkName);
        
        const form = document.getElementById("editForm");

		form.querySelector("#editDrinkName").value = drinkName;
		form.querySelector("#editCalories").value = calories;

        document.getElementById("editModalBackdrop").style.display = "block"; // show pop up edit modal
    }

    function deleteDrink(drinkName, row) {
        // Implement delete functionality based on the drinkId
        console.log('Delete Drink:', drinkName);

        const confirmation = prompt('Type "DELETE" to confirm.');
		if (confirmation === "DELETE") {
            const payload = {
                drinkName
            };
            console.log(JSON.stringify(payload))
            
            fetch(API_URL, {
                method: "DELETE",
                headers: {
                    "Content-Type": "application/json",
                },
                body: JSON.stringify(payload)
            })
            .then((response) => {
                if (response.ok) {
                    console.log("Successfully deleted",drinkName)
                    location.reload();
                    return response.json();
                } else {
                    alert("Server error");
                    throw new Error("Server");
                }
            })
		}

        // Remove the row from the table
        //row.remove();
    }

    	// Fetch users and ensure close modal interaction
	document.addEventListener("DOMContentLoaded", function () {
		loadItems();
		document.getElementById("closeModal").addEventListener("click", function () {
			document.getElementById("editModalBackdrop").style.display = "none"; // close pop up edit form
		});
	});

    //create method
    function submitForm(event) {

        event.preventDefault();
        //const formData = new FormData(event.target);
        //const drink = formData.get("Drink");
        //console.log("got form data Drink")
        //const calories = formData.get("Calories");

        const form = document.getElementById('myForm')
        const drinkName = form.elements['Drink'].value
        const calories = parseInt(form.elements['Calories'].value)
        
        const payload = {
            drinkName,
            calories,
        };
        console.log(JSON.stringify(payload))

        fetch(API_URL, {
            method: "POST",
            headers: {
                "Content-Type": "application/json",
            },
            body: JSON.stringify(payload),
        })
        .then((response) => {
            if (response.ok) {
                return response.json();
            } else {
                alert("Server error");
                throw new Error("Server");
            }
        })
        .then((data) => {
            location.reload()
        })
        .catch((error) => console.error("Error:", error));
    }

    //function to get details on one drink
    function getOneDrink(event) {
        event.preventDefault();
        //const formData = new FormData(event.target);
        //const drink = formData.get("Drink");
        //console.log("got form data Drink")
        //const calories = formData.get("Calories");

        const form = document.getElementById('formToGetOneDrinkDetail')
        const drinkName = form.elements['Drink'].value
        const responseDiv = document.getElementById('getOneDrinkDetailResponse')


        const URL_FOR_GetOne = API_URL + drinkName

        fetch(URL_FOR_GetOne, {
            method: "GET"
        })
        .then((response) => {
            if (response.ok) {
                return response.json();
            } else {
                alert("Server error");
                throw new Error("Server");
            }
        })
        .then((data) => {
            console.log(data)
            responseDiv.textContent =  data[0]['drinkName'] + " has " + data[0]['calories'] + " calories"
        })
        .catch((error) => console.error("Error:", error));
    }
</script>
