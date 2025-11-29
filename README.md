# EXP 2 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
## WITH CONV FUNCTION
```
clc;
clear;

x1=input('Enter the first sequence x1(n) = ');
x2=input('Enter the second sequence x2(n) = ');
L=length(x1);
M=length(x2);
N=L+M-1;
yn=conv(x1,x2);
disp('The values of yn are= ');
disp(yn);
n1=0:L-1;
subplot(311);
plot2d3(n1,x1);

xlabel('n1--->');
ylabel('amplitude--->');
title('First sequence');
n2=0:M-1;
subplot(312);
plot2d3(n2,x2);

xlabel('n2--->');
ylabel('amplitude--->');

title('Second sequence');
n3=0:N-1;
subplot(313);
plot2d3(n3,yn);

xlabel('n3--->');
ylabel('amplitude--->');
title('Convolved output');

```
## WITHOUT CONV FUNCTION
```
clc;
clear;

x1=input('Enter the first sequence x1(n) = ');
x2=input('Enter the second sequence x2(n) = ');
L=length(x1);
M=length(x2);
N=L+M-1;
yn=zeros(1,N);
for i = 1:L
    for k=1:M
        yn(i+k-1)=yn(i+k-1)+x1(i)*x2(k);
    end
end
disp('The values of yn are= ');
disp(yn);
n1=0:L-1;
subplot(3,1,1);
plot2d3(n1,x1);
xlabel('n1--->');
ylabel('amplitude--->');
title('First sequence');
n2=0:M-1;
subplot(3,1,2);
plot2d3(n2,x2);
xlabel('n2--->');
ylabel('amplitude--->');
title('Second sequence');
n3=0:N-1;
subplot(313);
plot2d3(n3,yn);
xlabel('n3--->');
ylabel('amplitude--->');
title('Convolved output');


```


## PROGRAM (Circular Convolution): 

## WITH CONV FUNCTION

 ```
clc;
clear;
 

// Input sequences
x = input("Enter the first sequence x(n): ");
h = input("Enter the second sequence h(n): ");

N1 = length(x);
N2 = length(h);
N  = max(N1, N2);

// Zero padding to length N
x1 = [x, zeros(1, N-N1)];
h1 = [h, zeros(1, N-N2)];

// Linear convolution using built-in function
y_lin = convol(x1, h1);

// Convert to circular convolution (wrap around)
y_circ = zeros(1, N);
for k = 1:length(y_lin)
    y_circ(modulo(k-1, N) + 1) = y_circ(modulo(k-1, N) + 1) + y_lin(k);
end

disp("Result of Circular Convolution y(n) = ");
disp(y_circ);

// Plot input and output
subplot(3,1,1);
plot2d3(0:N1-1, x);
xtitle("x(n)", "time --->", "amplitude --->");

subplot(3,1,2);
plot2d3(0:N2-1, h);
xtitle("h(n)", "time --->", "amplitude --->");

subplot(3,1,3);
plot2d3(0:N-1, y_circ);
xtitle("Circular Convolution y(n)", "time --->", "amplitude --->");

 ```

## WITHOUT CONV FUNCTION

```
clc;
clear;


// Input sequences
x = input("Enter the first sequence x(n): ");
h = input("Enter the second sequence h(n): ");

N1 = length(x);
N2 = length(h);

// Plot input x(n)
subplot(3,1,1);
n = 0:N1-1;
plot2d3(n, x);
xtitle("x(n)", "time --->", "amplitude --->");

// Plot input h(n)
subplot(3,1,2);
n = 0:N2-1;
plot2d3(n, h);
xtitle("h(n)", "time --->", "amplitude --->");

// Make lengths equal
N = max(N1, N2);
x1 = [x, zeros(1, N-N1)];
h1 = [h, zeros(1, N-N2)];

// Circular convolution
y = zeros(1, N);
for n = 1:N
    for i = 1:N
        j = n - i + 1;
        if (j <= 0) then
            j = N + j;
        end
        y(n) = y(n) + x1(i) * h1(j);
    end
end

disp("Result of Circular Convolution y(n) = ");
disp(y);

// Plot output
subplot(3,1,3);
n = 0:N-1;
plot2d3(n, y);
xtitle("Output y(n)", "time --->", "amplitude --->");

```

## OUTPUT (Linear Convolution): 

## WITHOUT CONV FUNCTION

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/25defaf2-c1bb-4c72-95e4-81f09b77fb9e" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6ce5d088-8585-48bd-a212-8e0ec61658d9" />


## WITH CONV FUNCTION

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e08e1225-2b3b-4ec8-b479-4c425721ded4" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/41195d25-5997-4d92-a1e4-3573bb2276a2" />



## OUTPUT (Circular Convolution): 

## WITHOUT CONV FUNCTION

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/918a1ea2-9aa9-4505-b179-f374f29f5447" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/24159bf5-cb82-45ea-bc1f-95d645c072b3" />

## WITH CONV FUNCTION

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/918a1ea2-9aa9-4505-b179-f374f29f5447" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/24159bf5-cb82-45ea-bc1f-95d645c072b3" />


## RESULT: 
Thus convolution using both circular and linear method using with and without 'conv' function is performed.
