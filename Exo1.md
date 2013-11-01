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
