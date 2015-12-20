#Learning Math
Math snippets for graphic programming.
This is work in progress!

##Contents

## Radians & Degrees

```
radians = degrees * Math.PI / 180;
degrees = radians * 180 / Math.PI;
```

```js
// JavaScript
var angleInDegrees = 45;
var radians = angleInDegrees * Math.PI / 180;
var backToDegrees = radians * 180 / Math.PI;
```

## Calculate side lengths
### SOHCAHTOA

##### Calculate basic trigonometric functions
```
Sine of an angle = opposite / hypotenuse
Cosine of an angle = adjacent / hypotenuse
Tangent of angle = opposite / adjacent
```

```js
// Javascript
var hyp = 100;
var angleDegrees = 45;
var angleRadians = angleDegrees * Math.PI / 180;

var opposite = Math.sin( angleRadians ) * hyp;
var adjacent = Math.cos( angleRadians ) * hyp;
var tangent  = opposite / adjacent;
```

## Rotate a 2D point
```js
var vec2 = {x: 2, y: 3};
var rotatedVector = rotate2D(vec2, angle);

function rotate2D(vector, angle)
{
	var theta = angle * Math.PI / 180; // radians
	var matrix = [  Math.cos(theta),  Math.sin(theta), 
					-Math.sin(theta), Math.cos(theta)
					];
					
	return { 
		x: matrix[0] * vector.x + matrix[1] * vector.y, 
		y: matrix[2] * vector.x + matrix[3] * vector.y
	};
}

```

## Linear Distance 2 points
```
dx = x2 - x1;
dy = y2 - y1;
dist = Math.sqrt(dx*dx + dy*dy);
```

```js
// JavaScript
var x1 = 3;
var x2 = 5;
var distance = x2 — x1;
```

## Linear distance between 2 vectors
### a² + b² = c²

```js
// Javascript
var v1 = {x: 4, y: -9};
var v2 = {x: 5, y: 15};

var distance = Math.sqrt( Math.pow((v2.x — v1.x), 2) + Math.pow((v2.y — v1.y), 2) );
```

## Length of a vector
### a.k.a Magnitude 

```js
// Javascript
// 2D -> hypotenuse
var v = {x: 4, y:-9};
var length = Math.sqrt( (Math.pow(v.x, 2) + Math.pow(v.y, 2)) );

// 3D
var v = {x: 4, y:-9, z: 0.5};
var length = Math.sqrt( (Math.pow(v.x, 2) + Math.pow(v.y, 2) + Math.pow(v.z, 2) ));
```

## Add and substract vectors

```js
var v1 = {x: 2, y: 3};
var v2 = {x: 2, y: -2};
var addedVec = {x: v1.x + v2.x, y: v1.y + v2.y};
var subVec = {x: v1.x - v2.x, y: v1.y - v2.y};
```

## Normalize vector

```js
// Javascript
// 2D
var v = {x: 4, y:-9};
var length = Math.sqrt( (Math.pow(v.x, 2) + Math.pow(v.y,2)) );
var n = {x: v.x / length, y: v.y / length};

// 3D
var v = {x: 4, y:-9, z: 3};
var length = Math.sqrt( Math.pow(v.x, 2) + Math.pow(v.y,2) + Math.pow(v.z,2) );
var n = {x: v.x / length, y: v.y / length, z: v.z / length};
```

## Dot product vectors

```js
// Javascript
var v1 = {x: 4, y: 5, z: 9};
var v2 = {x: 5, y: 9, z: -5};
var dot = (v1.x * v2.x) + (v1.y * v2.y) + (v1.z * v2.z);
```

## Finding angle between 2 points

```js
//Javascript
var x = -3;
var y = -2;
var radians = Math.atan2(x, y);
var degrees = radians * 180 / Math.PI;
```

## Finding angle between 2 vectors

```js
// Javascript
var v1 = {x: 4, y: 5, z: 9};
var v2 = {x: 5, y: 9, z: -5};
var dot = (v1.x * v2.x) + (v1.y * v2.y) + (v1.z * v2.z);

var lengthv1 = length(v1); // see length
var lengthv2 = length(v2); // see length

var radians = Math.acos(dot / (lengthv1 * lengthv2));
var angle = radians * 180 / Math.PI;
```

## Cross Product

```js
// Javascript
var v1 = {x: 1, y: 2, z: 3};
var v2 = {x: 3, y: 2, z: 1};
var cross = {
	x: v1.y*v2.z - v1.z*v2.y, 
	y: v1.z*v2.x - v1.x*v2.z, 
	z: v1.x*v2.y - v1.y*v2.x
};
```

## Rotate to the mouse (or any point)
```js
var dx = mouseX - spriteX;
var dy = mouseY - spriteY;
sprite.rotation = Math.atan2(dy, dx) * 180 / Math.PI;
```

## Create waves
```js
// value can be properties like x, y, alpha, rotation etc.
public function onEnterFrame(event:Event) {
  value = center + Math.sin(angle) * range;
  angle += speed;
}
```

## Hex to decimal
```
trace(hexValue);
```

## Decimal to hex
```
trace(decimalValue.toString(16));
```

## Combine component colors
```
color24 = red << 16 | green << 8 | blue;
color32 = alpha << 24 | red << 16 | green << 8 | blue;
```

## Extract component colors
```
red = color24 >> 16;
green = color24 >> 8 & 0xFF;
blue = color24 & 0xFF;

alpha = color32 >> 24;
red = color24 >> 16 & 0xFF;
green = color24 >> 8 & 0xFF;
blue = color24 & 0xFF;
```

## Draw a curve through a point
```
//xt, yt is the point to draw through
// x0, y0, x2, y2 is the end points
x1 = xt * 2 - (x0 - x2) / 2;
y1 = yt * 2 - (y0 - y2) / 2;
moveTo(x0, y0);
curveTo(x1, y1, x2, y2);
```

## Convert angular velocity to x, y velocity
```
vx = Math.cos(angle) * speed;
vy = Math.sin(angle) * speed;
```

## Convert angular acceleration or any other force to x and y
```
ax = Math.cos(angle) * force;
ay = Math.sin(angle) * force;
```

## Add acceleration to velocity
```
vx += ax;
vy += ay;
```

## Add velocity to position
```
sprite.x += vx;
sprite.y += vy;
```

## Testing for out of bound
```
if(sprite.x - sprite.width / 2 > right) ||
  sprite.x - sprite.width / 2 < left ||
  sprite.y - sprite.height / 2 > bottom ||
  sprite.y - sprite.height / 2 < top)
{
  //remove or reposition sprite
}
```

## Apply friction (correct way)
```
speed = Math.sqrt(vx*vx + vy*vy);
angle = Math.atan2(vy, vx);
if(speed > friction)
{
  speed -= friction;
} else {
  speed = 0;
}
vx = Math.cos(angle) * speed;
vy = Math.sin(angle) * speed;
```

## Apply friction (the easy way)
```
vx *= friction;
vy *= friction;
```

## Simple easing, long form
```
var dx = targetX - sprite.x;
var dy = targetY - sprite.y;
vx = dx * easing;
vy = dy * easing;
sprite.x += vx;
sprite.y += vy;
```

## Simple easing, abbreviated form
```
vx = (targetX - sprite.x) * easing;
vy = (targetY - sprite.y) * easing;
sprite.x += vx;
sprite.y += vy;
```

## Simple easing, short form
```
sprite.x += (targetX - sprite.x) * easing;
sprite.y += (targetY - sprite.y) * easing;
```

## Simple spring, long form
```
var ax = (targetX - sprite.x) * spring;
var ay = (targetY - sprite.y) * spring;
vx += ax;
vy += ay;
vx *= friction;
vy *= friction;
sprite.x += vx;
sprite.y += vy;
```

## Simple spring, abbreviated form
```
vx = (targetX - sprite.x) * spring;
vy = (targetY - sprite.y) * spring;
vx *= friction;
vy *= friction;
sprite.x += vx;
sprite.y += vy;
```

## Simple spring, short form
```
vx = (targetX - sprite.x) * spring;
vy = (targetY - sprite.y) * spring;
sprite.x += (vx *= friction);
sprite.y += (vy *= friction);
```

## Offset spring
```
var dx = sprite.x - fixedX;
var dy = sprite.y - fixedY;
var angle = Math.atan2(dy, dx);
var targetX = fixedX + Math.cos(angle) * springLength;
var targetY = fixedY + Math.sin(angle) * springLength;
// Spring to targetX and targetY;
```

## Distance-based collision detection
```
// Starting with spriteA and spriteB
// If using a plain sprite, or obejct without a radius property
// you can use with and height divided by 2

var dx = spriteB.x - spriteA.x;
var dy = spriteB.y - spriteA.y;
var dist = Math.sqrt(dx*dx + dy*dy);
if(dist < spriteA.radius + spriteB.radius)
{
  // handle collision
}
```

## Multiple-objects collision detection
```
var numObjects = 10;
for (var i = 0; i < numObjects; i++)
{
  var objectA = objects[i];
  for (var j = i+1; j < numObjects; j++)
  {
    var objectB = objects[j];
    // perform collision detection
    // between objectA and objectB
  }
}
```

## Coordinate rotation
```
x1 = Math.cos(angle) * x - Math.sin(angle) * y;
y1 = Math.cos(angle) * y + Math.sin(angle) * x;
```

## Reverse coordiante rotation
```
x1 = Math.cos(angle) * x + Math.sin(angle) * y;
y1 = Math.cos(angle) * y - Math.sin(angle) * x;
```

## Conservation of momentum in ActionScript (with a shortcut)
```js
var vxTotal = vx0 - vx1;
vx0 = ((ball0.mass - ball1.mass) * vx0 + 2 * ball1.mass * vx1) / (ball0.mass + ball1.mass);
vx1 = vxTotal + vx0;
```

## Gravity implementation
```js
function gravitate(partA, partB) {
  var dx = partB.x - partA.x;
  var dy = partB.y - partA.y;
  var distSQ  = dx*dx + dy*dy;
  var dist = Math.sqrt(distSQ);
  var force = partA.mass * partB.mass / distSQ;
  var ax = force * dx / dist;
  var ay = force * dy / dist;
  partA.vx += ax / partA.mass;
  partA.vy += ay / partA.mass;
  partB.vx += ax / partB.mass;
  partB.vy += ay / partB.mass;
}
```

# Resources
- Coding Math
- Generative Art by Matt Pearson

