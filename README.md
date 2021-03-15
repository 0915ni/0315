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
