<div align="center">

## Plotting sine, cosine and tangential waveforms


</div>

### Description

This program is part of a larger project; one which involves plotting the curve for any given eqyuation. If someone wants to develop that program jointly with me, or has any useful tip concerning it please email me.

Meanwhile check out this program...
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Shahab Faruqi](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/shahab-faruqi.md)
**Level**          |Intermediate
**User Rating**    |4.3 (13 globes from 3 users)
**Compatibility**  |C\+\+ \(general\)
**Category**       |[Graphics/ Sound](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/graphics-sound__3-15.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/shahab-faruqi-plotting-sine-cosine-and-tangential-waveforms__3-2547/archive/master.zip)

### API Declarations

```
#include<math.h>
#include<stdlib.h>
#include<graphics.h>
#include<conio.h>
```


### Source Code

```
/*
Author: Shahab Faruqi
Dated: 17 September 2001
Description: This program calculates sine, cosine and tangent waveforms.
You can adjust the frequency and amplitude of the waves by
changing the 2 arguments to sinewave(), cosinewave() and
tanwave() functions.
NOTE: Your graphics library must be installed. All *.bgi and
*.chr files must be located in the c:\tc\bgi directory. If
they are situated elsewhere change the location in the
initgraph() function.
Copyright: Public Domain
*/
#include<math.h>
#include<stdlib.h>
#include<graphics.h>
#include<conio.h>
double x=0,sinx,cosx,tanx,multi;
int ay,ax,newx=0,ox,oy,maxx,maxy,midy;
void sinewave(int,int);
void cosinewave(int,int);
void tanwave(int,int);
int distance(double,double);
int distance_tan(double,double);
void sinewave(int xmult,int ymult)
{
x=0;
newx=0;
ox=oy=0;
maxx=getmaxx();
midy=getmaxy()/2;
while(newx<maxx)
{
while(1)
{
if(x>3.142)
break;
sinx=sin(x);
multi=sinx*ymult;
ay=multi;
ax=newx+x*xmult;
moveto(ox,midy-oy);
lineto(ax,midy-ay);
x+=0.01;
ox=ax;
oy=ay;
}
newx=ax;
x=0;
while(1)
{
if(x>3.142)
break;
sinx=sin(x);
multi=sinx*ymult;
ay=multi;
ax=newx+x*xmult;
moveto(ox,midy+oy);
lineto(ax,midy+ay);
x+=0.01;
ox=ax;
oy=ay;
}
newx=ax;
x=0;
}
}
void cosinewave(int xmult,int ymult)
{
x=0;
newx=0;
ox=oy=0;
maxx=getmaxx();
midy=getmaxy()/2;
while(newx<maxx)
{
while(1)
{
if(x>3.14000)
break;
cosx=cos(x);
multi=cosx*ymult;
ay=multi;
ax=newx+x*xmult;
moveto(ox,midy-oy);
if(distance(ax,midy-ay)==0)
lineto(ax,midy-ay);
x+=0.01;
ox=ax;
oy=ay;
}
newx=ax;
x=0;
while(1)
{
if(x>3.1420)
break;
cosx=cos(x);
multi=cosx*ymult;
ay=multi;
ax=newx+x*xmult;
moveto(ox,midy+oy);
if(distance(ax,midy+ay)==0)
lineto(ax,midy+ay);
x+=0.01;
ox=ax;
oy=ay;
}
newx=ax;
x=0;
}
}
void tanwave(int xmult,int ymult)
{
x=0;
newx=0;
ox=oy=0;
maxx=getmaxx();
midy=getmaxy()/2;
while(newx<maxx)
{
while(1)
{
if(x>3.14000)
break;
tanx=tan(x);
multi=tanx*ymult;
ay=multi;
ax=newx+x*xmult;
moveto(ox,midy-oy);
if(distance_tan(ax,midy-ay)==0)
lineto(ax,midy-ay);
x+=0.01;
ox=ax;
oy=ay;
}
newx=ax;
x=0;
while(1)
{
if(x>3.1420)
break;
tanx=tan(x);
multi=tanx*ymult;
ay=multi;
ax=newx+x*xmult;
moveto(ox,midy+oy);
if(distance_tan(ax,midy+ay)==0)
lineto(ax,midy+ay);
x+=0.01;
ox=ax;
oy=ay;
}
newx=ax;
x=0;
}
}
int distance(double x,double y)
{
int xx=getx(),yy=gety();
double r;
x-=xx;
y-=yy;
x*=x;
y*=y;
r=sqrt(x+y);
if(r>1.0)return 1;
else return 0;
}
int distance_tan(double x,double y)
{
int xx=getx(),yy=gety();
double r;
x-=xx;
y-=yy;
x*=x;
y*=y;
r=sqrt(x+y);
if(r>100.0)return 1;
else return 0;
}
void main()
{
int a=DETECT,b;
initgraph(&a,&b,"c:\\tc\\bgi");
setlinestyle(0,0,1);
setcolor(14);
line(1,0,1,getmaxy());
line(1,getmaxy()/2,getmaxx(),getmaxy()/2);
sinewave(30,100);/*Change the arguments to change the frequency and
amplitude of the wave respectively*/
getch();
cleardevice();
line(1,0,1,getmaxy());
line(1,getmaxy()/2,getmaxx(),getmaxy()/2);
cosinewave(30,100);/*Change the arguments to change the frequency and
amplitude of the wave respectively*/
getch();
cleardevice();
line(1,0,1,getmaxy());
line(1,getmaxy()/2,getmaxx(),getmaxy()/2);
tanwave(30,100);/*Change the arguments to change the frequency and
amplitude of the wave respectively*/
getch();
closegraph();
}
```

