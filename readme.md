Answers for LAB 1                                          LIU GUANQUN 17082422D

Part 1
Q 1.1
Source code:

x = rand(1,65536);	
y = rand(1,65213);	
tic				
fft(x);
t1 = toc			

tic		 		
fft(y);
t2 = toc			

Output:

t1 =
    0.0053
t2 =
    0.0113


Q 1.2
Source code:

>> x1 = [1 1 1 1 0 0 0 0]
>> X1 = fft (x1)

>> x2 = [1 1 -1 0 1 0 -1 1]
>> X2 = fft (x2)

>> x3 = [1 1 1 1 -1 -1 -1 -1]
>> X3 = fft (x3)

>> x4 = [0 1 1 0 0 -1 -1 -1]
>> X4 = fft (x4)

Output:
x1 =
     1     1     1     1     0     0     0     0

X1 =
  Columns 1 through 6

   4.0000 + 0.0000i   1.0000 - 2.4142i   0.0000 + 0.0000i   1.0000 - 0.4142i   0.0000 + 0.0000i   1.0000 + 0.4142i

  Columns 7 through 8

   0.0000 + 0.0000i   1.0000 + 2.4142i

x2 =
     1     1    -1     0     1     0    -1     1

X2 =
    2.0000    1.4142    4.0000   -1.4142   -2.0000   -1.4142    4.0000    1.4142

x3 =
     1     1     1     1    -1    -1    -1    -1

X3 =
  Columns 1 through 6

   0.0000 + 0.0000i   2.0000 - 4.8284i   0.0000 + 0.0000i   2.0000 - 0.8284i   0.0000 + 0.0000i   2.0000 + 0.8284i

  Columns 7 through 8

   0.0000 + 0.0000i   2.0000 + 4.8284i

x4 =
     0     1     1     1     0    -1    -1    -1

X4 =
  Columns 1 through 6

   0.0000 + 0.0000i   0.0000 - 4.8284i   0.0000 + 0.0000i   0.0000 - 0.8284i   0.0000 + 0.0000i   0.0000 + 0.8284i

  Columns 7 through 8

   0.0000 + 0.0000i   0.0000 + 4.8284i

Questions:
(a)	The FFT for (B) is purely real.
(b)	The FFT for (D) is purely imaginary.
(c)	For real x[n], if x[n] is even symmetry, then x[n] has a purely real FFT;
If x[n] is odd symmetry, then x[n] has a purely imaginary FFT.

Q 1.3 
Source code:
>> x1 = [1 1 1 1]
>> X1 = fft(x1,4)
>> X1 = abs(X1)
>> subplot(511)
>> stem(X1)

>> x2 = [1 1 1 1]
>> X2 = fft(x1,8)
>> X2 = abs(X2)
>> subplot(512)
>> stem(X2)

>> x3 = [1 1 1 1]
>> X3 = fft(x3,32)
>> X3 = abs(X3)
>> subplot(513)
>> stem(X3)

>> x4 = [1 1 1 1]
>> X4 = fft(x4,128)
>> X4 = abs(X4)
>> subplot(514)
>> stem(X4)

>> x5 = [1 1 1 1]
>> X5 = fft(x5,1024)
>> X5 = abs(X5)
>> subplot(515)
>> stem(X5)

Magnitude Spectrum:
 

Questions:
       (b) Because the resolution of the 128-point DFT is much higher than that of 4-point DFT.
       (c) Xp(w) at 900Hz is (2.7814 - 2.1706i)


Part 2

Q 2.1
Source code:

>> x = [1 2 3 4 5 6 5 4 3 2 1 1]
>> h = [1 4 6 4 1]
>> y = conv(x, h)
>> L = length(y)

Output:
x =
     1     2     3     4     5     6     5     4     3     2     1     1

h =
     1     4     6     4     1

y =
     1     6    17    32    48    64    78    84    78    64    48    33    21    12     5     1

L =
    16

Q 2.2
(a)
Source code:

>> X = fft (x, 16)
>> H = fft (h, 16)
>> Y = fft (y, 16)
>> m1 = X.*H
>> d1 = abs (m1)
>> d2 = abs (Y)
>> d3 = immse (d1, d2)

Output:

X =
  Columns 1 through 6

  37.0000 + 0.0000i  -8.9649 -19.7954i  -3.1213 + 1.7071i   1.3622 - 0.2011i   0.0000 - 1.0000i  -1.1196 - 0.3016i

  Columns 7 through 12

   1.1213 - 0.2929i   0.7222 + 0.1041i  -1.0000 + 0.0000i   0.7222 - 0.1041i   1.1213 + 0.2929i  -1.1196 + 0.3016i

  Columns 13 through 16

   0.0000 + 1.0000i   1.3622 + 0.2011i  -3.1213 - 1.7071i  -8.9649 +19.7954i

H =
  Columns 1 through 6

  16.0000 + 0.0000i  10.4689 -10.4689i   0.0000 -11.6569i  -5.4074 - 5.4074i  -4.0000 + 0.0000i  -1.0779 + 1.0779i

  Columns 7 through 12

   0.0000 + 0.3431i   0.0164 + 0.0164i   0.0000 + 0.0000i   0.0164 - 0.0164i   0.0000 - 0.3431i  -1.0779 - 1.0779i

  Columns 13 through 16

  -4.0000 + 0.0000i  -5.4074 + 5.4074i   0.0000 +11.6569i  10.4689 +10.4689i


Y =
   1.0e+02 *

  Columns 1 through 6

   5.9200 + 0.0000i  -3.0109 - 1.1338i   0.1990 + 0.3638i  -0.0845 - 0.0628i   0.0000 + 0.0400i   0.0153 - 0.0088i

  Columns 7 through 12

   0.0010 + 0.0038i   0.0001 + 0.0001i   0.0000 + 0.0000i   0.0001 - 0.0001i   0.0010 - 0.0038i   0.0153 + 0.0088i

  Columns 13 through 16

   0.0000 - 0.0400i  -0.0845 + 0.0628i   0.1990 - 0.3638i  -3.0109 + 1.1338i

m1 =
   1.0e+02 *

  Columns 1 through 6

   5.9200 + 0.0000i  -3.0109 - 1.1338i   0.1990 + 0.3638i  -0.0845 - 0.0628i   0.0000 + 0.0400i   0.0153 - 0.0088i

  Columns 7 through 12

   0.0010 + 0.0038i   0.0001 + 0.0001i   0.0000 + 0.0000i   0.0001 - 0.0001i   0.0010 - 0.0038i   0.0153 + 0.0088i

  Columns 13 through 16

   0.0000 - 0.0400i  -0.0845 + 0.0628i   0.1990 - 0.3638i  -3.0109 + 1.1338i

d1 =
  Columns 1 through 12

  592.0000  321.7297   41.4710   10.5302    4.0000    1.7675    0.3977    0.0169         0    0.0169    0.3977    1.7675

  Columns 13 through 16

    4.0000   10.5302   41.4710  321.7297

d2 =
  Columns 1 through 12

  592.0000  321.7297   41.4710   10.5302    4.0000    1.7675    0.3977    0.0169         0    0.0169    0.3977    1.7675

  Columns 13 through 16

    4.0000   10.5302   41.4710  321.7297

d3 =
   5.1778e-28

Since the mean square difference d3 = 5.1778e-28 is approximately 0, therefore it can be concluded that X.*H = Y.

(b)
No. Because the linear convolution result of x[n] and h[n] (y[n]) have length 16, in order to preserve the complete convolution result, we cannot use shorter length DFT.

(c)
Source code: 

>> X = fft (x, 32)
>> H = fft (h, 32)
>> Y = fft (y, 32)
>> m1 = X.*H
>> d1 = abs (m1)
>> d2 = abs (Y)
>> d3 = immse (d1, d2)

Output (Mean-Square-Difference):

d3 =
   4.0724e-28

Since 4.0724e-28 can still be considered as 0, it can be concluded that X.*H = Y still holds.


Q 2.3 
(a)
Source code:

>> tic
>> x = randn(1,102500)
>> h = randn(1,1024)
>> y = conv(x,h)
>> t = toc

Output: 

t =
    0.7150

(b)
Source code:

>> tic
>> X = fft (x, 2^20)
>> H = fft (h, 2^20)
>> y2 = ifft (X.*H)
>> T = toc
>> y = [y, zeros(1, 945053)]
>> err = immse (y, y2)
Output:

T =
   21.4084

err =
   1.3611e-28

Since err = 1.3611e-28 can be considered as 0, it can be concluded that y = y2. However, there is no saving in computation time, on the opposite, the computation time is apparently longer than that of direct linear convolution. 


(c)
Program: 
>>  x = randn(1,102500); 
>>  h = randn(1,1024);
>>  y = conv(x,h); 
 
>> tic;
>> L = 1025;
>> k = 100;
>> y3 = zeros(1,103523);
 
>> H = fft(h, 2048);
 
>> for i = 1 : k
           xs = x((L.*(i-1))+1 : L.*i);
           Xs = fft(xs, 2048);
           yr = ifft(Xs.*H);
           y3((L.*(i-1))+1 : (L.*(i-1))+2048) = y3((L.*(i-1))+1 : (L.*(i-1))+2048) + yr;
>> end
>> t = toc;
>> err = immse(y, y3);

The mean square difference between y and y3 is 1.4024e-27, which can be considered as 0 in this case, therefore it can be concluded that y = y3. The operation time t = 0.0088s.

Q 2.4
Source Code:

>> h = [1 4 6 4 1]/16
>> H = fft (h, 100)
>> Ha = angle (H)
>> Hm = abs (H)
>> subplot (211)
>> stem (Ha)
>> subplot (212)
>> stem (Hm)


If the sampling frequency fs = 8000Hz, from the magnitude spectrum, the bandwidth of the filter is approximately 13*8000/100 = 1040Hz.


Q 2.5 
(b)
Source code:
 
>> X = fft (xx, 100)
>> y = ifft (X.*H)
>> plot (y)

 
