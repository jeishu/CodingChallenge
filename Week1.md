Java Code Challenge:

> Create a function that takes the memory size (ms is a string type) as an argument and returns the actual memory size.
> Examples
> actualMemorySize("32GB") --> "29.76GB"

> actualMemorySize("2GB") --> "1.86GB"

> actualMemorySize("512MB") --> "476MB"

> Notes
> -The actual storage loss on a USB device is 7% of the overall memory size!
> -If the actual memory size was greater than 1 GB, round your result to two decimal places.
> -If the memory size after adjustment is smaller then 1 GB, return the result in MB.

```
public static void main(String[] args) {
		System.out.println(actualMemorySize("32GB"));
		System.out.println(actualMemorySize("2GB"));
		System.out.println(actualMemorySize("512GB"));
		System.out.println(actualMemorySize("1GB"));
		System.out.println(actualMemorySize("50MB"));
		System.out.println(actualMemorySize("25MB"));
	}
	
	public static String actualMemorySize(String ms) {
	
		// Changing the String to a float and removing the GB from the string
		float memory = Float.parseFloat(ms.substring(0, ms.length() - 2));
		
		// If the String contains GB then it will take the 7% memory loss 
		// and if the memory is under 1GB it will return MB instead of GB
		if(ms.substring(ms.length() - 2).equals("GB")) {
			
			// formatting the floating point of the decimal
			return memory > 1.075 ?  String.format("%.2f", memory * 0.93) + "GB" :
				Math.round(memory * 0.93 * 1000) + "MB";
		} 
		// if the memory is already a MB, it will just round to the nearest whole number for MB
		else {
			return Math.round(memory * 0.93) + "MB";
		}
		
	}
```

JavaScript Code Challenge:
> Write a function that retrieves the top 3 longest words of a newspaper headline and transforms them into hashtags. If multiple words tie for the same length, retrieve the word that occurs first.

> Examples
> getHashTags("How the Avocado Became the Fruit of the Global Trade")

> --> ["#avocado", "#became", "#global"]

> getHashTags("Why You Will Probably Pay More for Your Christmas Tree This Year")

> --> ["#christmas", "#probably", "#will"]

> getHashTags("Hey Parents, Surprise, Fruit Juice Is Not Fruit")

> --> ["#surprise", "#parents", "#fruit"]

> getHashTags("Visualizing Science")

> --> ["#visualizing", "#science"]

```
const getHashTags = (string) => {

    //splitting the string by the spaces
    let stringArr = string.toLowerCase().split(" ");

    let words = [];

    stringArr.forEach( string => {
        string = string.replace(/\W/g,"");

        if(!words[0] || string.length > words[0].length -1) {
            words.unshift(`#${string}`);

        } else if(!words[1] || string.length > words[1].length -1) {
            words.splice(1, 0, `#${string}`);

        } else if (!words[2] || string.length > words[2].length -1) {
            words.splice(2, 0, `#${string}`);

        }

        while (words.length > 3) {
            words.splice(3);
        }
    })

    return words;
}

console.log(getHashTags("How the Avocado Became the Fruit of the Global Trade"));
console.log(getHashTags("Why You Will Probably Pay More for Your Christmas Tree This Year"));
console.log(getHashTags("Hey Parents, Surprise, Fruit Juice Is Not Fruit"));
console.log(getHashTags("Visualizing Science"));
```



