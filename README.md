# Pizzacalculator<!DOCTYPE html>
<html>
<head>
	<title>Opdracht pizza Calculator</title>
</head>
<body>
	<p>Kies je pizza</p>
	<button id='btnSmall' onclick='pizzaSmall()'>Small</button>
	<button id='btnMedium' onclick='pizzaMedium()'>Medium</button>
	<button id='btnLarge' onclick='pizzaLarge()'>Large</button>
	<br>
	<content id='toppings' hidden='true'>
		<content id='sizeAndPrice'></content>
		<br>
		<p>Wil je extra toppings?</p>
		<button id='btnExtraCheese' onclick='addExtraCheese()'>Voeg extra kaas toe</button><p>+1 dollar naar het totaal</p><br>
		<button id='btnExtraSauce' onclick='addExtraSauce()'>Voeg extra tomaten saus toe</button><p>+1 dollar naar het totaal</p><br>
		<button id='btnPepperoni' onclick='addPepperoni()'>Voeg pepperoni toe</button><p>+1.50 dollar naar het totaal</p><br>
	</content>
	<br> 
	<button onclick='checkout()'>Ga naar winkelwagen</button>
	<br>
	<content id='checkoutInfo'></content>

	<script>
		// Daan Koning
		// ICT 
		// Opdracht Pizza
		
		var amtSmall = 0;
		var amtMedium = 0;
		var amtLarge = 0;
		var amtTotal = 0;
		var totalSmall = 0;
		var totalMedium = 0;
		var totalLarge = 0;
		var totalTotal = 0;
		var checkoutString = '';
		var size = ''; 

	
		function selectTopping(){
			document.getElementById('toppings').hidden = false;
			if (size == 'small'){
				document.getElementById('sizeAndPrice').innerHTML = ('Je hebt gekozen ' + amtSmall + ' ' + size + ' pizzas.');
			}
			if (size == 'medium'){
				document.getElementById('sizeAndPrice').innerHTML = ('Je hebt gekozen ' + amtMedium + ' ' + size + ' pizzas.');
			}
			if (size == 'large'){
				document.getElementById('sizeAndPrice').innerHTML = ('Je hebt gekozen ' + amtLarge + ' ' + size + ' pizzas.');
			}
			checkoutString += '<p>Extra toppings:</p>'
			amtTotal += (amtSmall + amtMedium + amtLarge);
		}

		function addExtraCheese(){
			totalTotal += (1.00 * amtTotal);
			checkoutString += ('Kaas +$1.00 * ' + amtTotal + ' pizzas<br>');
		}
		function addExtraSauce(){
			totalTotal += (1.00 * amtTotal);
			checkoutString += ('Saus +$1.00 * ' + amtTotal + ' pizzas<br>');
		}
		function addPepperoni(){
			totalTotal += (1.50 * amtTotal);
			checkoutString += ('Pepperoni +$1.50 * ' + amtTotal + ' pizzas<br>');
		}
		

		function pizzaSmall(){
			amtSmall = parseInt(prompt('Selecteer het aantal small pizzas, elke pizza is $5'));
			totalSmall = (amtSmall * 5.00);
			checkoutString += ('Het aantal pizzas is ' + amtSmall + ' met een totaal van $' + totalSmall + '<br>');
			document.getElementById('btnMedium').disabled = true;
			document.getElementById('btnLarge').disabled = true;
			size = 'small';
			selectTopping();

		}
		function pizzaMedium(){
			amtMedium = parseInt(prompt('Selecteer het aantal medium pizzas, elke pizza is $7.99'));
			totalMedium = (amtMedium * 7.99);
			checkoutString += ('Het aantal pizzas is ' + amtMedium + ' met een totaal van $' + totalMedium + '<br>');
			document.getElementById('btnSmall').disabled = true;
			document.getElementById('btnLarge').disabled = true;
			size = 'medium';
			selectTopping();

		}
		function pizzaLarge(){
			amtLarge = parseInt(prompt('Selecteer het aantal large pizzas, elke pizza is $9.99'));
			totalLarge = (amtLarge * 9.99);
			checkoutString += ('Het aantal pizzas is ' + amtLarge + ' met een totaal van $' + totalLarge + '<br>');
			document.getElementById('btnSmall').disabled = true;
			document.getElementById('btnMedium').disabled = true;
			size = 'large';
			selectTopping();

		}

		function checkout(){
			document.write(checkoutString);
			totalTotal += (totalSmall + totalMedium + totalLarge);
			document.write("<br>Dat word dan $" + totalTotal + ' alstublieft ');
			
			
		}

	</script>
</body>
</html>
