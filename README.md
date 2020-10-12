# kata-Calculating-with-Functions

This time we want to write calculations using functions and get the results. Let's have a look at some examples:

seven(times(five())); // must return 35
four(plus(nine())); // must return 13
eight(minus(three())); // must return 5
six(dividedBy(two())); // must return 3
Requirements:

There must be a function for each number from 0 ("zero") to 9 ("nine")
There must be a function for each of the following mathematical operations: plus, minus, times, dividedBy (divided_by in Ruby and Python)
Each calculation consist of exactly one operation and two numbers
The most outer function represents the left operand, the most inner function represents the right operand
Division should be integer division. For example, this should return 2, not 2.666666...:
eight(dividedBy(three()));

Test Cases
-
describe('static example calculations', function() {
  Test.assertEquals(seven(times(five())), 35);
  Test.assertEquals(four(plus(nine())), 13);
  Test.assertEquals(eight(minus(three())), 5);
  Test.assertEquals(six(dividedBy(two())), 3);
});

describe('random calculations', function() {
  var numbers = ['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine'];

  it('add', function() {
    for (var i=0; i<50; i++) {
      var num1 = Test.sample(numbers);
      var num2 = Test.sample(numbers);
      Test.assertEquals(eval(num1 + '(plus(' + num2 + '()))'), numbers.indexOf(num1) + numbers.indexOf(num2), 'Wrong result for ' + num1 + ' + ' + num2);
    }
  });
  
  it('subtract', function() {
    for (var i=0; i<50; i++) {
      var num1 = Test.sample(numbers);
      var num2 = Test.sample(numbers);
      Test.assertEquals(eval(num1 + '(minus(' + num2 + '()))'), numbers.indexOf(num1) - numbers.indexOf(num2), 'Wrong result for ' + num1 + ' - ' + num2);
    }
  });
  
  it('multiply', function() {
    for (var i=0; i<50; i++) {
      var num1 = Test.sample(numbers);
      var num2 = Test.sample(numbers);
      Test.assertEquals(eval(num1 + '(times(' + num2 + '()))'), numbers.indexOf(num1) * numbers.indexOf(num2), 'Wrong result for ' + num1 + ' * ' + num2);
    }
  });
  
  it('divide', function() {
    for (var i=0; i<50; i++) {
      var num1 = Test.sample(numbers);
      var num2 = Test.sample(numbers.slice(1));
      Test.assertSimilar(eval(num1 + '(dividedBy(' + num2 + '()))'), numbers.indexOf(num1) / numbers.indexOf(num2)|0, 'Wrong result for ' + num1 + ' / ' + num2);
    }
  });
});
