#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>

int sum(int a, int b, int c) {

return a + b + c;

}

float Avg(float a, float b, float c) {

return (a + b + c) / 3;

}

struct member {

char name[10];

int computer;

int english;

int math;

};

void dread(struct member *test) {

int i;

FILE* fp;

fp = fopen("testfile.txt", "r");

for (i = 0; i < 3; i++) {

fscanf(fp, "%s %d %d %d", test->name, &test->computer, &test->english, &test->math);

++test;

}

fclose(fp);

}

int main()

{

printf("Name Computer English Math Sum Avg\n");

struct member test[3];

int i;

dread(test);

for (i = 0; i < 3; i++)

printf("%s %d %d %d %d %5.2f\n", test[i].name, test[i].computer, test[i].english, test[i].math, sum(test[i].computer, test[i].english, test[i].math), Avg(test[i].computer, test[i].english, test[i].math));

printf("Sum %d %d %d\n", sum(test[0].computer, test[1].computer, test[2].computer), sum(test[0].english, test[1].english, test[2].english), sum(test[0].math, test[1].math, test[2].math));

printf("Avg %5.2f %5.2f %5.2f ", Avg(test[0].computer, test[1].computer, test[2].computer), Avg(test[0].english, test[1].english, test[2].english), Avg(test[0].math, test[1].math, test[2].math));

printf("%5.2f", Avg(Avg(test[0].computer, test[0].english, test[0].math), Avg(test[1].computer, test[1].english, test[1].math), Avg(test[2].computer, test[2].english, test[2].math)));

return 0;

}
