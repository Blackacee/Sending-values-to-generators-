# Sending-values-to-generators-

function* summer() {
 let sum = 0, value;
 while (true) {
 // receive sent value
 value = yield;
 if (value === null) break;
 // aggregate values
 sum += value;
 }
 return sum;
}
let generator = summer();
// proceed until the first "yield" expression, ignoring the "value" argument
generator.next();
// from this point on, the generator aggregates values until we send "null"
generator.next(1);
generator.next(10);
generator.next(100);
// close the generator and collect the result
let sum = generator.next(null).value; // 111
