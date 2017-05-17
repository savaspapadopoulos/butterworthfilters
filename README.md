# butterworthfilters
A collection of Butterworth filter code from my <a href="http://doctorpapadopoulos.com">blog</a>


void ButterworthLowpassFilter0100SixthOrder(const double src[], double dest[], int size)
{       
const int NZEROS = 6;    
const int NPOLES = 6;    
const double GAIN = 2.936532839e+03;     
double xv[NZEROS+1] = {0.0}, yv[NPOLES+1] = {0.0};     
for (int i = 0; i < size; i++)    
{         
xv[0] = xv[1]; xv[1] = xv[2]; xv[2] = xv[3]; xv[3] = xv[4]; xv[4] = xv[5]; xv[5] = xv[6];  
xv[6] = src[i] / GAIN;        
yv[0] = yv[1]; yv[1] = yv[2]; yv[2] = yv[3]; yv[3] = yv[4]; yv[4] = yv[5]; yv[5] = yv[6];  
yv[6] =   (xv[0] + xv[6]) + 6.0 * (xv[1] + xv[5]) + 15.0 * (xv[2] + xv[4])  + 20.0 * xv[3]  + ( -0.0837564796 * yv[0]) + (  0.7052741145 * yv[1])                     + ( -2.5294949058 * yv[2]) + (  4.9654152288 * yv[3])                     + ( -5.6586671659 * yv[4]) + (  3.5794347983 * yv[5]);        dest[i] = yv[6];    
  }
}
