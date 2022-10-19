I attended the Code Katas monthly meet-up hosted by the Seattle JS Hackers group. The meet-up was organized and hosted by Justin Lee, a front-end software engineer that works at SeekOut. SeekOut is an AI-powered talent search engine that helps companies discover and engage the hard-to-find and diverse talent. Before that, Justin worked for Microsoft, and he started the Code Katas group a few years ago and now holds these meet-ups to help people of all experience levels practice their code and learn new techniques to solve problems.

We also met Jon Borgonia, a software engineer at Digit, a Seattle-based company focused on financial health (and they're hiring!). Jon co-hosts these meet-ups with Justin each month.

The meeting started with a round of intros from everyone in the meeting about their background and what projects they're working on. Then we started with a warm-up problem:

1) Consider the word `abode`. We can see that the letter `a` is in position `1` and `b` is in position `2`. In the alphabet, `a` and `b` are also in positions `1` and `2`. Notice also that `d` and `e` in `abode` occupy the positions they would occupy in the alphabet, which are positions `4` and `5`. Given an array of words, return an array of the number of letters that occupy their positions in the alphabet for each word. For example, `solve(["abode","ABc","xyzD"])` = `[4, 3, 1]`.

I was able to solve this problem with the following code:

```
function solve(arr){
  let alphabet = 'abcdefghijklmnopqrstuvwxyz';
  let result =[];
  for(let i = 0; i < arr.length; i++){
    let lower = arr[i].toLowerCase();
    let counter = 0;
    for(let j=0; j < lower.length; j++){
      if(lower[j] === alphabet[j]){
        counter++;
      }
    }
    result.push(counter);
  }
  return result;
};
```

We were then given 3 problems to work on for about 45 minutes and I was able to solve 2 of them:

2) You will create a function named `tiyFizzBuzz`. This function will take on a string parameter and will return that string with some characters replaced, depending on the value:

* If a letter is a upper case consonants, replace that character with "Iron".
* If a letter is a lower case consonants or a non-alpha character, do nothing to that character
* If a letter is a upper case vowel, replace that character with "Iron Yard".
* If a letter is a lower case vowel, replace that character with "Yard".

Here is my solution:

```
function tiyFizzBuzz(sentence){
  let cons = 'BCDFGHJKLMNPQRSTVWXYZ';
  let vowels = 'AEIOU';
  let vowelsLower = 'aeiou';
  let sentenceArr = sentence.split('');
  for ( let i = 0; i < sentence.length; i++) {
    for ( let j = 0; j < cons.length; j++) {
      if( sentenceArr[i] == cons[j]) {
        sentenceArr.splice(i, 1, 'Iron');
      } else if (j < 6) {
        if( sentenceArr[i] == vowels[j]) {
          sentenceArr.splice(i, 1, 'Iron Yard');
        } else if (sentenceArr[i] == vowelsLower[j]) {
          sentenceArr.splice(i, 1, 'Yard');
        }
      }
    }
  }
  return sentenceArr.join('');
}
```

3) If we are to start our Tribonacci sequence with `[1, 1, 1]` as a starting input (AKA `signature`), we have this sequence: `[1, 1 ,1, 3, 5, 9, 17, 31, ...]`. But what if we started with `[0, 0, 1]` as a `signature`? As starting with `[0, 1]` instead of `[1, 1]` basically shifts the common Fibonacci sequence by once place, you may be tempted to think that we would get the same sequence shifted by 2 places, but that is not the case and we would get: `[0, 0, 1, 1, 2, 4, 7, 13, 24, ...]`. Well, you may have guessed it by now, but to be clear: you need to create a fibonacci function that given a `signature` array/list, returns the first `n` elements - `signature` included of the so seeded sequence. `Signature` will always contain 3 numbers; `n` will always be a non-negative number; if `n == 0`, then return an empty array (except in `C` return `NULL`) and be ready for anything else which is not clearly specified.

Here is my solution:

```
function tribonacci(signature,n){
  if (n === 0) {
    return [];
  } else if (n === 1) {
    return [signature[0]];
  } else if (n === 2) {
    return [signature[0], signature[1]]
  };
  let result = [signature[0], signature[1], signature[2]];
  let sum = 0;
  for (let i = 0; i < n - 3; i++) {
    sum = result[i] + result[i + 1] + result[i + 2];
    result.push(sum);
  }
  return result;
}
```

The last problem had to do with making a function that tells you the best possible outcome of a given hand of cards in the game Blackjack. But I didn't get that far and had no idea how to do it.

This was pretty challenging for me since I haven’t done many JS problems before. The solutions the other devs created were simpler, more efficient, and used formats and methods I had never seen before. They understood I was new to JS and they provided feedback that was much appreciated. I’ll probably jump in on their next meet-up to keep practicing!
