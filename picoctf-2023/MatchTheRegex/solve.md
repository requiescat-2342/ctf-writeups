# MatchTheRegex
Web Exploitation, 100 points

## Description

How about trying to match a regular expression
The website is running here.

Hints: None

## Solution

The question says to match a regular expression. Going to the website shows a text box with a submit button. 

![alt text](https://github.com/requiescat-2342/ctf-writeups/blob/main/picoctf-2023/MatchTheRegex/website.PNG)

View source (Ctrl+U) shows this block of code:
```console
<script>
	function send_request() {
		let val = document.getElementById("name").value;
		// ^p.....F!?
		fetch(`/flag?input=${val}`)
			.then(res => res.text())
			.then(res => {
				const res_json = JSON.parse(res);
				alert(res_json.flag)
				return false;
			})
		return false;
	}

</script>
```

There is a commented string that is a regular expression (regex). A little research reveals that the `^` signifies the beginning of the regex, and `?` signifies the end. `!` is the `not` operator. `.` signifies any character. 
This implies the `send_request()` function will fetch the flag if you pass a string gthat starts with a `p`, has 5 of any character, then ends with a capital F. (Since `!` isn't before another character, it does nothing.)

Entering such a string, for example `paaaaaF`, prints out the flag.

picoCTF{succ3ssfully_matchtheregex_REDACTED}
