let
total_rings = 10;
diameter = 1;
height = 0.1;
ring { d, t, h } = circle d >> shell (t*2) >> extrude h;
rings = [for(i in 0..total_rings) let
  p = (cis ((tau/4/total_rings)*i)) * (diameter/2);
in
  ring { d: p.[X]*2, t: 0.1, h: height }
  >> move [0, 0, p.[Y]]
  >> colour (sRGB.hue((p.[X] * p.[Y] + 1)/2))
];
in
union rings
>> rotate { angle: 90*deg, axis: Y_axis }
>> repeat_mirror_x
>> rotate { angle: -90*deg, axis: Y_axis }
