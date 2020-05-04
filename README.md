#Javascript Bootcamp#

Chapter 2 recursion LASTIG!

Recursion is not always just an inefficient alternative to looping. Some problems really are easier to solve with recursion than with loops. Most often these are problems that require exploring or processing several “branches”, each of which might branch out again into even more branches.
Consider this puzzle: by starting from the number 1 and repeatedly either adding 5 or multiplying by 3, an infinite set of numbers can be produced. How would you write a function that, given a number, tries to find a sequence of such additions and multiplications that produces that number?
For example, the number 13 could be reached by first multiplying by 3 and then adding 5 twice, whereas the number 15 cannot be reached at all.
Here is a recursive solution:
function findSolution(target) {
  function find(current, history) {
    if (current == target) {
      return history;
    } else if (current > target) {
      return null;
    } else {
      return find(current + 5, `(${history} + 5)`) ||
             find(current * 3, `(${history} * 3)`);
    }
  }
  return find(1, "1");
}

console.log(findSolution(24));
// → (((1 * 3) + 5) * 3)
Note that this program doesn’t necessarily find the shortest sequence of operations. It is satisfied when it finds any sequence at all.
It is okay if you don’t see how it works right away. Let’s work through it, since it makes for a great exercise in recursive thinking.
The inner function find does the actual recursing. It takes two arguments: the current number and a string that records how we reached this number. If it finds a solution, it returns a string that shows how to get to the target. If no solution can be found starting from this number, it returns null.
To do this, the function performs one of three actions. If the current number is the target number, the current history is a way to reach that target, so it is returned. If the current number is greater than the target, there’s no sense in further exploring this branch because both adding and multiplying will only make the number bigger, so it returns null. Finally, if we’re still below the target number, the function tries both possible paths that start from the current number by calling itself twice, once for addition and once for multiplication. If the first call returns something that is not null, it is returned. Otherwise, the second call is returned, regardless of whether it produces a string or null.
To better understand how this function produces the effect we’re looking for, let’s look at all the calls to find that are made when searching for a solution for the number 13.
find(1, "1")
  find(6, "(1 + 5)")
    find(11, "((1 + 5) + 5)")
      find(16, "(((1 + 5) + 5) + 5)")
        too big
      find(33, "(((1 + 5) + 5) * 3)")
        too big
    find(18, "((1 + 5) * 3)")
      too big
  find(3, "(1 * 3)")
    find(8, "((1 * 3) + 5)")
      find(13, "(((1 * 3) + 5) + 5)")
        found!
The indentation indicates the depth of the call stack. The first time find is called, it starts by calling itself to explore the solution that starts with (1 + 5). That call will further recurse to explore every continued solution that yields a number less than or equal to the target number. Since it doesn’t find one that hits the target, it returns null back to the first call. There the || operator causes the call that explores (1 * 3) to happen. This search has more luck—its first recursive call, through yet another recursive call, hits upon the target number. That innermost call returns a string, and each of the || operators in the intermediate calls passes that string along, ultimately returning the solution.

Freecode camp


Met bracket notation kan de value van een bepaalde index (letter) worden opgehaald door van van de var de [0] op te halen. Javascript begint met tellen vanaf 0 ook wel “zero-based indexing”.

x
Je kan 1 bepaalde index niet veranderen van een sting door alleen deze index te veranderen. Wanneer je de string wilt aanpassen moet de hele string worden aangepast
:)

-------------------------------------------------------------------

Javascript telt dus vanaf 0, dus hier boven wordt de 2e letter aangeroepen van de variabele firstName.

Ook kan je de laatste letter krijgen door firstName[firstName.length -1] te gebruiken en zo verder terug naar voren -2 -3 enz, hier wordt nu dus wel de .length bij gebruikt.



Binnen een array kan wel een waarde worden gehaald door de brackets [0] te gebruiken en deze te vervangen.
There shouldn't be any spaces between the array name and the square brackets, like array [0][0] and even this array [0] [0] is not allowed. Although JavaScript is able to process this correctly, this may confuse other programmers reading your code.


Een array bestaande uit arrays. Op deze manier kan er een waarde uit de array binnen de array worden gehaald. 



Vergeet de () niet na .push!

Kennelijk neemt de pop() funtie automatisch de laatste van de array weg.


En shift() neemt altijd de eerste weg… logisch toch?


Unshift() is het tegenovergestelde van push(), de gewenste waarde wordt aan het begin van de Array toegevoegd.









Spelen met functies











Spelen met een Array.

Door de push wordt het laatste item weggehaald. Door de shift wordt het eerste item opgeslagen in de remove variable. VRAGEN! IK SNAP DIT NOG NIET HELEMAAL! .shift return? WAT IS HET NUT VAN DEZE FUNCTIE????




Er wordt nu not equal gereturnd omdat 10 een nummer is en “10” een string. Omdat deze met de === (strict equality)  wordt vergeleken wordt het not equal. Wanneer het met de == wordt vergeleken zou het wel equal zijn want dan maakt het niet uit of het een string of nummer is 10 is dan hetzelfde als “10”.

hetzelfde geldt voor de not equal to functie != en !===


Book chapter 4 interessante stukjes


Mutability






const en slice LASTIG!




nog meer properties






callback functie




Een specifiek stuk uit de data halen console.log(person.firstname)


Functie in een object, ook wel een method
this.name roept de naam Danny aan
DAG 5 







