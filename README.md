1. 문제정의

3명의 컴퓨터/영어/수학 성적을 처리하는 프로그램을 작성해야 한다. 필요한 과정은 
  1) dat.txt에 들어있는 3명의 데이터를 구조체형으로 정의해서 설계해야 한다.
  2) 파일에서 데이터를 읽을 수 있도록 dread()함수를 만들어야 한다.
  3) 점수, 과목별 총점, 과목별 평균, 학생별 성적총점, 학생별 성적 평균을 구해서 화면에 출력하도록 프로그래밍해야 한다.
  4) 도출된 결과를 하드디스크에 저장한다.
--------------------------------------------------------------------------------------------------------

2. 플로우 차트 : https://github.com/qkrgudals1030/cpp.anu/blob/master/%ED%94%8C%EB%A1%9C%EC%9A%B0%EC%B0%A8%ED%8A%B8.jpg

   슈도코드 : https://github.com/qkrgudals1030/cpp.anu/blob/master/슈도코드.jpg

--------------------------------------------------------------------------------------------------------

3. 소스코드

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

fp = fopen("dat.txt", "r");

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

  printf("%s %d %d %d %d %5.2f\n", test[i].name, test[i].computer, test[i].english, test[i].math, sum(test[i].computer, test[i].english,   test[i].math), Avg(test[i].computer, test[i].english, test[i].math));

printf("Sum %d %d %d\n", sum(test[0].computer, test[1].computer, test[2].computer), sum(test[0].english, test[1].english, test[2].english), sum(test[0].math, test[1].math, test[2].math));

printf("Avg %5.2f %5.2f %5.2f ", Avg(test[0].computer, test[1].computer, test[2].computer), Avg(test[0].english, test[1].english, test[2].english), Avg(test[0].math, test[1].math, test[2].math));

printf("%5.2f", Avg(Avg(test[0].computer, test[0].english, test[0].math), Avg(test[1].computer, test[1].english, test[1].math), Avg(test[2].computer, test[2].english, test[2].math)));

return 0;

f
}
