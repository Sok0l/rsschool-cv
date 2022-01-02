## Calculator for roman and arabic numbers
```
function calculator(string) {

	const array = string.split(' ')
	const a = array[0]
	const b = array[2]
	const operator = array[1]

	const translator = (number) => { //конвертер  из арабских в римские
		if (number == 'I') {
			return 1;
		} else if (number == 'II') {
			return 2;
		} else if (number == 'III') {
			return 3;
		} else if (number == 'IV') {
			return 4;
		} else if (number == 'V') {
			return 5;
		} else if (number == 'VI') {
			return 6;
		} else if (number == 'VII') {
			return 7;
		} else if (number == 'VIII') {
			return 8;
		} else if (number == 'IX') {
			return 9;
		} else if (number == 'X') {
			return 10;
		} else if (number > 0 || number <= 10) {
			return 'not roman'
		}
	}

	const calcRomana = () => {  //калькулятор римских чисел

		if (operator === '+') {
			return String(Number(translator(a)) + Number(translator(b)))
		} else if (operator === '-') {
			return String(translator(a) - translator(b))
		} else if (operator === '*') {
			return String(translator(a) * translator(b))
		} else if (operator === '/' && a !== 0 && b !== 0) {
			return String(Math.floor(translator(a) / translator(b)))
		}
	}

	const result = calcRomana()
	if (result > 0) {
		function romanize(result) {  //конвертер из арабских в римские
			if (isNaN(result))
				return '';
			var digits = String(+result).split(""),
				key = ["", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM",
					"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC",
					"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"],
				roman = "",
				i = 3;
			while (i--)
				roman = (key[+digits.pop() + (i * 10)] || "") + roman;
			return Array(+digits.join("") + 1).join("M") + roman;
		}
	}

	const calc = (a, b) => {     //калькулятор арабских чисел
		if (a !== NaN && b !== NaN) {
			if (operator === '+') {
				return String(Number(a) + Number(b))
			} else if (operator === '-') {
				return String(a - b)
			} else if (operator === '*') {
				return String(a * b)
			} else if (operator === '/' && b !== 0) {
				return String(Math.floor(a / b))
			}
		}
	}

	if (array.length !== 3 || a > 10 || b > 10 || operator === '%') { //выборка ошибок
		return asdasd
	} else if (translator(a) === undefined || translator(b) === undefined) {
		return asdasd
	} else if (translator(a) == 'not roman' && translator(b) !== 'not roman' || translator(b) == 'not roman' && translator(a) !== 'not roman') {
		return asdasd
	} else if (operator === '/' && b == 0) {
		return asdasd
	} else if (a == 0 || b == 0) {
		return asdasd
	}

	if (result <= 0) { //вывод ответа калькулятора римских чисед
		return ''
	} else if (result > 0) {
		return romanize(result)
	}
	return calc(a, b) //вывод ответа калькулятора арабских чисел
}
```