# rockdefender
http://jsfiddle.net/binghuan/a0s1f0dq/

<pre><code>
defender.start(
  function notify_player(rocks, paddle_y) {
    var moves = [];
    var nearestIndex = 0;
    var nearestDistance = rocks[0].distance;
    for (var i = 0; i < rocks.length; i++) {
      if (nearestDistance > rocks[i].distance) {
        nearestDistance = rocks[i].distance
        nearestIndex = i;
      }
    }
    //console.log("nearestIndex = " + nearestIndex);
    //console.log(rocks[nearestIndex].radians / Math.PI * 180);
    //console.log(rocks[nearestIndex]);
    var distance = rocks[nearestIndex].distance;
    var radians = rocks[nearestIndex].radians;
    var degree = rocks[nearestIndex].radians / Math.PI * 180;
    if (degree < 0) {
      degree = degree * -1;
    }
    var superStep = 0;
    if (degree > 0) {
      var length = (80-distance) / Math.sin( (90-degree) / 180 * Math.PI ) * Math.sin(degree / 180 * Math.PI);
      if(length<0)
      {
        length = length * -1;
      }
      superStep = Math.floor(length / 2.5);
    }
    console.log(radians + " --- " + degree + " -- " + superStep);
    if (rocks[nearestIndex].radians > 0) {
      if (superStep > 0) {
        for (var i = 0; i < superStep; i++) {
          moves.push(-1);
        }
      } else {
        moves.push(-1);
      }
    }
    if (rocks[nearestIndex].radians < 0) {
      if (superStep > 0) {
        for (var i = 0; i < superStep; i++) {
          moves.push(1);
        }
      } else {
        moves.push(1);
      }
    }
    return moves;
  }
);
</code></pre>
