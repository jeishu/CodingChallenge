Java
> Take the number 192 and multiply it by each of 1, 2, and 3:
> 
> 192 × 1 = 192
> 
> 192 × 2 = 384
> 
> 192 × 3 = 576
> 
> By concatenating each product, we get the 1 to 9 pandigital, 192384576. We will call 192384576 the concatenated product of 192 and (1,2,3)
> 
> The same can be achieved by starting with 9 and multiplying by 1, 2, 3, 4, and 5,giving the pandigital, 918273645, which is the concatenated product of 9 and(1,2,3,4,5).
> 
> What is the largest 1 to 9 pandigital 9-digit number that can be formed as the concatenated product of an integer with (1,2, ... , n) where n >1?

```
public class RevCoding {
    public static String isPandigital(String sB) {
		    StringBuilder isPen = new StringBuilder("yes");
		    boolean isPend = true;
		    IntStream intStream = IntStream.range(1,10);
		
	      intStream.forEach((i) -> {
	    	    if(!sB.contains(i+"")) {
	    		    isPen.setLength(0);
	    		    isPen.append("no");  
	    	    }
	      });
	      return isPen.toString();
	  }
	
	  public static String panDecimal() {
		    StringBuilder finalNum = new StringBuilder("");
		    for (long i = 9876; i > 9123 ; i--) {
			      String nums = i + "" + 2*i;
			
		        if(isPandigital(nums).equals("yes")) {
		    	     finalNum.append(nums);
		    	     break;
		        }
		    }
		    return finalNum.toString();
	  }
	
	  public static void main(String[] args) {
		    System.out.println(panDecimal());
	  }
}
```

JavaScript:
> When coloring a striped pattern, you may start by coloring each square sequentially, meaning you spend time needing to switch coloring pencils.
> 
> Create a function where given an array of colors cols, return how long it takes to color the whole pattern. Note the following times:
> 
> It takes 1 second to switch between pencils.
> 
> It takes 2 seconds to color a square.
> 
> See the example below for clarification.
> 
> <code>color_pattern_times(["Red", "Blue", "Red", "Blue", "Red"]) ➞ 14</code><code>// There are 5 colors so it takes 2 seconds to color each one (2 x 5 = 10).</code><code>// You need to switch the pencils 4 times and it takes 1 second to switch (1 x 4 = 4).</code><code>// 10 + 4 = 14</code>
> 
> Examples
> 
> <code>colorPatternTimes(["Blue"]) ➞ 2</code><code>colorPatternTimes(["Red", "Yellow", "Green", "Blue"]) ➞ 11</code><code>colorPatternTimes(["Blue", "Blue", "Blue", "Red", "Red", "Red"]) ➞ 13</code>
> 
> Notes
> 
> Only change coloring pencils if the next color is different to the color before it.
> 
> Return a number in seconds.

```
const colorTime = (col) => {
  	let time = 0;
	  col.map((c, i) => i > 0 && col[i-1] !==c ? time++ : '' );
  	return col.length ? time += col.length * 2 : "empty array";
}

console.log(colorTime(["Red", "Blue", "Red", "Blue", "Red"]));
console.log(colorTime(["Red"]));
console.log(colorTime(["Red", "Yellow", "Green", "Blue"]));
console.log(colorTime(["Blue", "Blue", "Blue", "Red", "Red", "Red"]));
```
