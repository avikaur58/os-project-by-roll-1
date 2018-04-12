# os-project-by-roll-1

//algorithm of question
sem_t NS,NW,NE,ES,EW,SW,SN,WN,EN,SE,WS,WE,common
struct direction{ o,d}s1;
origin=0,destination=0
ncount=0,scount=0,ecount=0,wcount=0
void *North(s1)
{
print”hello 1 - North”
wait(common)
print”entering critical section”
ncount++
if(ncount=1)
{
if(s1->d=3)
       {
wait(EW)
   	wait(WE)
   	wait(EN)
   	wait(SE)
}
else if(s1->d=4)
{
    wait(WE)
    wait(SN)
    wait(EN) 
    wait(SE)  
}
}
signal(common)
call print_direction(s1.o,s1.d)
wait(common)
ncount - -
if(ncount=0)
{
if(s1->d=3)
       {
signal(EW)
   	signal(WE)
   	signal(EN)
   	signal(SE)
}
else if(s1->d=4)
{
    signal(WE)
    signal(SN)
    signal(EN) 
    signal(SE)  
}
}
signal(common)
}


void *East(s1)
{
print”hello 3 - East”
wait(common)
print”entering critical section”
ecount++
if(ecount=1)
{
if(s1->d=4)
       {
wait(NS)
   	wait(SN)
   	wait(WS)
   	wait(SE)
}
else if(s1->d=1)
{
    wait(NS)
    wait(WE)
    wait(WS) 
    wait(SE)  
}
}
signal(common)
call print_direction(s1.o,s1.d)
wait(common)
ecount--
if(ecount=0)
{
if(s1->d=4)
       {
signal(NS)
   	signal(SN)
   	signal(WS)
   	signal(SE)
}
else if(s1->d=1)
{
    signal(NS)
    signal(WE)
    signal(WS) 
    signal(SE)  
}
}
signal(common)
}


void *South(s1)
{
print”hello 2 - South”
wait(common)
print”entering critical section”
scount++
if(scount=1)
{
if(s1->d=1)
       {
wait(EW)
   	wait(WE)
   	wait(NW)
   	wait(WS)
}
else if(s1->d=2)
{
    wait(EW)
    wait(NS)
    wait(WS) 
    wait(NW)  
}
}
signal(common)
call print_direction(s1.o,s1.d)
wait(common)
scount--
if(scount=0)
{
if(s1->d=1)
       {
Signal(EW)
   	signal(WE)
   	signal(NW)
   	signal(WS)
}
else if(s1->d=2)
{
    signal(EW)
    signal(NS)
    signal(WS) 
    signal(NW)  
}
}
signal(common)
}



void *West(s1)
{
print”hello 4 - West”
wait(common)
print”entering critical section”
wcount++
if(wcount=1)
{
if(s1->d=1)
       {
wait(NS)
   	wait(SN)
   	wait(EW)
   	wait(SW)
}
else if(s1->d=3)
{
    wait(SN)
    wait(EW)
    wait(NW) 
    wait(EN)  
}
}
signal(common)
call print_direction(s1.o,s1.d)
wait(common)
wcount--
if(wcount=0)
{
if(s1->d=1)
       {
Signal(NS)
   	signal(SN)
   	signal(EW)
   	signal(SW)
}
else if(s1->d=3)
{
    signal(SN)
    signal(EW)
    signal(NW) 
    signal(EN)  
}
}
signal(common)
}

void print_direction(origin,destination)
{
switch(origin)
{
Case 1
Print”Car is starting from north”
break
Case 2
Print”Car is starting from south”
break
Case 3
Print”Car is starting from east”
break
Case 4
Print”Car is starting from west”
break
}
Print” and going to “
switch(destination)
{
Case 1
Print”north”
break
Case 2
Print”south”
break
Case 3
Print”east”
break
Case 4
Print”west”
break
}
}
