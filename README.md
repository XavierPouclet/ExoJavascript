ExoJavascript
=============

Exercice 1:

function adder() {
  var args = Array.prototype.slice.call(arguments);
  return function (v) {
    var res = 0;
    args.forEach(function (entry) {
      res += entry(v);
    });
    return res;
  }
} 

function mult (v) {
  return function (e) {
    return v*e;
  }
}

function sub (v) {
  return function (e) {
    return v-e;
  }
}

console.log(adder(mult(2), sub(2), mult(2))(1));

adder()(0); // 0
adder()(1); // 0
adder(mult(2))(1); // 2
adder(mult(2), mult(2))(1); // 4
adder(mult(2), mult(2), mult(2))(1); // 6
adder(mult(2), sub(2), mult(2))(1); // 5
