#20210315
```C++
#include <GL/glut.h>

#include <stdio.h>///0000
float teapotX=0, teapotY=0;
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glPushMatrix();
        glTranslatef(teapotX, teapotY, 0);
        glutSolidTeapot(0.3);///實心茶壺
    glPopMatrix();
    glEnd();
    glutSwapBuffers();///交換兩倍的buffers
}

//void mouse( int button, int state, int x, int y)///0000
//{
//}///0000
void motion(int x, int y)
{
    teapotX = (x-150)/150.0;
    teapotY = -(y-150)/150.0;
    display();
}
int main(int argc, char ** argv)///???以前是 int main()
{
    glutInit( & argc, argv);///(1)GLUT初始設定
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);///(2)顯示模式
    glutCreateWindow("08163070林育帆");///(3)開窗

    glutDisplayFunc(display);///(4)等一下要顯示的函式

    glutMotionFunc(motion);///0000

    glutMainLoop();///(5)主要迴圈
}
```
0322
```C
#include <GL/glut.h>
#include <stdio.h>
float vx[2000], vy[2000];///準備一堆頂點，等一下要畫!!!介於-1 ~ +1
int N=0;///有N個頂點
void display()
{   ///我就是 等一下
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glBegin(GL_LINE_LOOP);
    for(int i=0; i<N; i++)
    {
        glVertex2f( vx[i], vy[i]);
    }
    glEnd();
    glutSwapBuffers();///交換兩倍的buffers
}
void mouse( int button, int state, int x, int y)
{
}
void motion(int x, int y)
{
    printf("%d %d\n", x, y);///把頂點記起來...等一下要畫
    vx[N] = (x-150)/150.0;///很像這樣的寫法，記錄起來...
    vy[N] = -(y-150)/150.0;
    N++;
    display();
}///減一半，再除一半，y加負號
int main(int argc, char ** argv)///???以前是 int main()
{
    glutInit( & argc, argv);///(1)GLUT初始設定
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);///(2)顯示模式
    glutCreateWindow("08163070林育帆");///(3)開窗

    glutDisplayFunc(display);///week02  ///(4)等一下要顯示的函式

    glutMouseFunc(mouse);///week04 按下去、彈起來
    glutMotionFunc(motion);///week04 mouse motion 在動(拖曳)/在畫

    glutMainLoop();///(5)主要迴圈
}
```
