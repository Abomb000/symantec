# symantec
Symantec Example

```js
function search(start,end,variants) {
	if(variants.indexOf(end)==-1) return 0;
	if(diff(start,end)==1) return 1;

	var positive_results=[];
	
	variants.forEach(element => {
		if(diff(start,element)==1) {
			if(element==end) {
				positive_results.push(1);
			}
			var result = search(element,end,variants.filter((e) =>{ return e !== element }));
			if(result>0) {
				positive_results.push(result);
			}
		}
	});
	
	if(positive_results.length>0) 
		return (Math.min.apply(Math, positive_results)+1);
	else 
		return 0;
}

function diff(a,b) {
	var diff_count=0;
	for(i=0;i<a.length;i++) {
		if(a[i]!=b[i]) diff_count++;
	}
	return diff_count;
}

console.log("Result: "+search('cor','hut',['hut','bot','not','hot','hin','kut','zir','zor','zot']));
console.log("Result: "+search('hot','hut',['hut','bot','not','hot','hin','kut','zir','zor','zot']));
console.log("Result: "+search('uuu','hut',['hut','bot','not','hot','hin','kut','zir','zor','zot']));
console.log("Result: "+search('not','fff',['hut','bot','not','hot','hin','kut','zir','zor','zot']));
console.log("Result: "+search('hit','bot',['hut','bot','not','hot','hin','kut','zir','zor','zot']));
console.log("Result: "+search('hit','lll',['hut','bot','not','hot','hin','kut','zir','zor','zot','llr']));
```
