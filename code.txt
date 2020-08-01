#include<stdio.h>
#include<stdlib.h>
#include<GL/glut.h>
#include<math.h>
#include<string.h>

static int m=0,M=0,v=0,V=0,E=0,e=0,r=0,R=0,j=0,J=0,s=0,S=0,U=0,u=0,n=0,N=0,X=0,z=0,b=0,c=0;
GLfloat diffuseMaterial[4]={0.5,0.5,0.5,1.0};
/*initialize material property,light soure,lighting model,and depth buffer*/
void myinit(void)
{
   glClearColor(0.0,0.0,0.0,0.0);
   glShadeModel(GL_SMOOTH);
   glEnable(GL_DEPTH_TEST);
   GLfloat mat_specular[]={1.0,1.0,1.0,1.0};
   GLfloat light_position[]={1.0,1.0,1.0,0.0};
   glMaterialfv(GL_FRONT,GL_DIFFUSE,diffuseMaterial);
   glMaterialfv(GL_FRONT,GL_SPECULAR,mat_specular);
   glMaterialf(GL_FRONT,GL_SHININESS,25.0);
   glEnable(GL_LIGHTING);
   glEnable(GL_LIGHT0);
   glLightfv(GL_LIGHT0,GL_POSITION,light_position);
   glColorMaterial(GL_FRONT,GL_DIFFUSE);
   glEnable(GL_COLOR_MATERIAL);
}

void display(void)
{
   GLfloat position[]={0.0,0.0,1.5,1.0};
   glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
   glColor3f(1.0,0.5,0.0);
   glPushMatrix();
   glRotatef((GLfloat)z,1.0,1.0,1.0);
   glLightfv(GL_LIGHT0,GL_POSITION,position);
   glDisable(GL_LIGHTING);
   glutSolidSphere(0.8,40,16); /*draw sun*/
   glPopMatrix();
   glPushMatrix();
   glLightfv(GL_LIGHT0,GL_POSITION,position);
   glDisable(GL_LIGHTING);
   glEnable(GL_LIGHTING);
   glColor3f(1.5,0.5,0.0);
   glutSolidTorus(0.2,0.9,6,20);
   glPopMatrix();
   glPushMatrix();
   glRotatef((GLfloat)M,0.0,1.0,0.0);
   glTranslatef(1.5,0.0,0.0);
   glRotatef((GLfloat)m,0.0,1.0,0.0);
   glColor3f(1.0,0.0,0.0);
   glutSolidSphere(0.2,20,8); /*draw smaller planet mercury*/
   glPopMatrix();
   glPushMatrix();
   glRotatef((GLfloat)V,0.0,1.0,0.0);
   glTranslatef(2.0,0.0,1.0);
   glRotatef((GLfloat)v,0.0,1.0,0.0);
   glColor3f(7.5,9.5,1.0);
   glutSolidSphere(0.2,20,8); /*draw smaller plant venus*/
   glPopMatrix();
   glPushMatrix();
   glRotatef((GLfloat)E,0.0,1.0,0.0);
   glTranslatef(3.5,0.0,0.0);
   glRotatef((GLfloat)e,0.0,1.0,0.0);
   glColor3f(0.1,6.5,2.0);
   glutSolidSphere(0.2,20,8); /*draw smaller plant earth*/
   glRotatef((GLfloat)X,0.0,1.0,0.0);
   glTranslatef(0.3,0.2,0.0);
   glColor3f(4.3,3.5,8.0);
   glutSolidSphere(0.1,20,14); /*draw moon*/
   glPopMatrix();
   glPushMatrix();
   glRotatef((GLfloat)R,0.0,1.0,0.0);
   glTranslatef(5.0,0.0,3.0);
   glRotatef((GLfloat)r,0.0,1.0,0.0);
glColor3f(1.0,0.2,0.0);
   glutSolidSphere(0.2,20,8); /*draw smaller planet mars*/
glPopMatrix();
glPushMatrix();
glRotatef((GLfloat)J,0.0,1.0,0.0);
glTranslatef(-2.5,0.0,1.0);
glRotatef((GLfloat)j,0.0,1.0,0.0);
glColor3f(0.9,0.7,0.3);
glutSolidSphere(0.2,20,8);/*draw smaller planet Jupiter*/
glPopMatrix();
glPushMatrix();
glRotatef((GLfloat)S,0.0,1.0,0.0);
glTranslatef(-5.0,0.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)s,0.0,0.0,5.0);
glColor3f(4.5,0.5,0.0);
glutSolidSphere(0.5,20,16); /*draw smaller plant Saturn*/
int i=0;
glBegin(GL_QUAD_STRIP);
for(i=0;i<=360;i++)
{
glVertex3f(sin(i*3.1416/180)*0.5,cos(i*3.1416/180)*0.5,0);
glVertex3f(sin(i*3.1416/180)*0.7,cos(i*3.1416/180)*0.7,0);
}
glEnd();
glPopMatrix();
glPushMatrix();
glRotatef ((GLfloat) U, 0.0, 1.0,0.0);
glTranslatef (-6.5, 0.0, 0.0);
gluLookAt (10.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 10.0, 1.0);
glRotatef((GLfloat) u, 0.0, 0.0, 5.0);
glColor3f( 1.2, 0.6,0.2);
glutSolidSphere (0.5, 20, 16); /* draw smaller planet Uranus*/
glBegin(GL_QUAD_STRIP);
for(i=0; i<=360; i++)
{
glVertex3f(sin(i*3.1416/180)*0.5,cos(i*3.1416/180)*0.5, 0);
glVertex3f(sin(i*3.1416/180)*0.7, cos(i*3.1416/180)*0.7,0);
}
glEnd();
glPopMatrix();
glPushMatrix();
glRotatef ((GLfloat) N,0.0, 1.0, 0.0);
glTranslatef (-8.0, 0.0, 0.0);
glRotatef ((GLfloat) n, 0.0, 1.0, 0.0);
glColor3f(1.0, 2.0, 0.0);
glutSolidSphere(0.4, 20, 8);
glPopMatrix();/* draw smaller planet Neptune */
glPushMatrix();
glRotatef ((GLfloat) c, 6.0, -14.0,-6.0);
glTranslatef (5.0,3.0,-1.0);
glScalef(0.60,0.0,2.5);
glColor3f (7.5, 9.5, 2.0);
glutSolidSphere (0.2, 12, 6);
glPopMatrix();/*draw comet*/
//to put the stars as a background
glPushMatrix();
glTranslatef(0.0,-2.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,2.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,-4.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,4.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.1,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,-6.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.1,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,6.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.1,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,-8.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.1,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,8.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.1,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(8.0,0.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-8.0,-2.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(6.0,4.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-6.0,4.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(5.0,-4.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-7.0,3.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-7.0,2.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(7.0,-2.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(7.0,-3.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-7.0,-3.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(7.0,2.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(1.0,-7.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(2.0,-5.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,3.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(5.0,-1.0,0.0);
gluLookAt(0.0,10.0,0.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.07,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-6.0,7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.07,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-0.5,3.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.07,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-1.5,4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.07,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-9.0,3.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.07,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(9.0,-5.9,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.1,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(6.5,8.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.1,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(5.0,7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.1,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-9.0,6.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.1,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-10.5,9.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.07,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-11.0,-7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.07,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-11.0,5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-7.0,-5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-10.0,3.7,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-7.0,-2.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-8.0,5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.03,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-8.0,-5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-11.0,-4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(6.0,-5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-6.9,7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(5.0,-4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(6.0,4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(3.0,-4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(4.0,-7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat) b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-4.0,-3.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
 glPushMatrix();
glTranslatef(4.0,-7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
 glTranslatef(11.0,-4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
 glTranslatef(9.0,-9.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
 glTranslatef(8.0,-4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
 glTranslatef(9.0,5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef (7.0,7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.9,7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(1.0,6.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.8,-5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();

glPushMatrix();
glTranslatef(3.0,-7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(1.0,5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(2.0,4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-9.0,0.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-10.0,4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(9.0,3.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-10.0,-6.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(10.0,0.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-9.0,-7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-3.0,4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-9.9,-7.5,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(1.0,5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(3.0,6.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-2.0,-5.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-3.0,-2.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-4.0,-8.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(8.3,-7.1,0.0);
gluLookAt (0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-10.0,7.6,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-3.0,7.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-1.4,7.5,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(3.0,6.5,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-6.0,4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(-6.0,-6.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.05,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.7,4.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(2.0,2.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,0.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,-1.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,1.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(0.0,2.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,0.0,0.0,0.0);
glScalef(200.0,0.0,0.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glPushMatrix();
glTranslatef(8.7,9.0,0.0);
gluLookAt(0.0,10.0,2.0,1.0,0.0,0.0,0.0,0.0,1.0);
glRotatef((GLfloat)b,1.0,7.0,5.0);
glColor3f(4.3,3.5,1.0);
glutSolidSphere(0.04,20,8);
glPopMatrix();
glutSwapBuffers();
}
void welcomedisplay()
{
	int i;
	char msg1[]="BANGALORE INSTITUTE OF TECHNOLOGY";
	char msg2[]="SUBMITTED BY:";
	char msg3[]="KOKILA";
	char msg4[]="SHANTVEER";
	char msg5[]="1BI17CS076";
	char msg6[]="1BI17CS140";
	char options[]="OPTIONS";
	char option1[]="press \"G\" SOLAR SYSTEM";
	char option2[]="press \"F\" MENU OPTIONS";
	char option3[]="press \"D\" to EXIT";
	glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
	glColor3f(1.0,1.0,1.0);

    glRasterPos3f(-2.5,1.5,0);
    for(i=0;i<strlen(msg1);i++)
    glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,msg1[i]);

    glRasterPos3f(-3,1,0);
    for(i=0;i<strlen(msg2);i++)
    glutBitmapCharacter(GLUT_BITMAP_9_BY_15,msg2[i]);

    glRasterPos3f(-2,0.5,0);
    for(i=0;i<strlen(msg3);i++)
    glutBitmapCharacter(GLUT_BITMAP_9_BY_15,msg3[i]);

    glRasterPos3f(-2,0.8,0);
    for(i=0;i<strlen(msg4);i++)
    glutBitmapCharacter(GLUT_BITMAP_9_BY_15,msg4[i]);

    glRasterPos3f(-0.8,0.5,0);
    for(i=0;i<strlen(msg5);i++)
    glutBitmapCharacter(GLUT_BITMAP_9_BY_15,msg5[i]);

    glRasterPos3f(-0.8,0.8,0);
    for(i=0;i<strlen(msg6);i++)
    glutBitmapCharacter(GLUT_BITMAP_9_BY_15,msg6[i]);

    glRasterPos3f(-3,0,0);
    for(i=0;i<strlen(options);i++)
    glutBitmapCharacter(GLUT_BITMAP_9_BY_15,options[i]);

    glRasterPos3f(-2,-0.5,0);
    for(i=0;i<strlen(option1);i++)
    glutBitmapCharacter(GLUT_BITMAP_9_BY_15,option1[i]);

    glRasterPos3f(-2,-0.9,0);
    for(i=0;i<strlen(option2);i++)
    glutBitmapCharacter(GLUT_BITMAP_9_BY_15,option2[i]);

    glRasterPos3f(-2,-1.3,0);
    for(i=0;i<strlen(option3);i++)
    glutBitmapCharacter(GLUT_BITMAP_9_BY_15,option3[i]);

    glutSwapBuffers();

}
void menudisplay()
{
 int i;
 char menu1[]="MENU OPTION";
 char menu2[]="CLICK THE D BUTTON TO GO TO SOLAR SYSTEM";
 char menu3[]="THIS BUTTONS WILL WORK ON SOLAR SYSTEM SCREEN";
 char m1[]="m-rotation of planet mercury";
 char m2[]="v - rotation of planet venus";
 char m3[]="e - rotation of planet earth";
 char m4[]="r - rotation of planet mars";
 char m5[]="j - rotation of planet jupiter";
 char m6[]="s - rotation of planet saturn";
 char m7[]="u - rotation of planet uranus";
 char m8[]="n - rotation of planet neptune";
 char m9[]="M - revolution of planet mercury";
 char m10[]="V - revolution of planet venus";
 char m11[]="E - revolution of planet earth";
 char m12[]="R - revolution of planet mars";
 char m13[]="J - revolution of planet jupiter";
 char m14[]="S - revolution of planet saturn";
 char m15[]="U - revolution of planet uranus";
 char m16[]="N - revolution of planet neptun";
 char m17[]="z - rotation of sun";
 char m18[]="B - rotation and revolution of planets, rotating sun, comet revolution and stars twinkle";
 char m19[]="A - revolution of all planets, rotation of sun and twinkling of stars";
 char m20[]="a - rotation of all planets and twinkling of stars";
 char m21[]="b - stars twinkle";
 char m22[]="c - revolution of comet";

 glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
 glClearColor(0.0,0.0,0.0,1.0F);
 glColor3f(1.0,1.0,1.0);

 glRasterPos3f(-1,2.5,0);
 for(i=0;i<strlen(menu1);i++)
 glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,menu1[i]);

 glRasterPos3f(-2,2,0);
    for(i=0;i<strlen(menu2);i++)
    glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,menu2[i]);

glRasterPos3f(-2,1.8,0);
    for(i=0;i<strlen(menu3);i++)
    glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,menu3[i]);

 glRasterPos3f(-5.0,1.5,0);
 for(i=0;i<strlen(m1);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m1[i]);

 glRasterPos3f(-5.0,1.3,0);
 for(i=0;i<strlen(m2);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m2[i]);

 glRasterPos3f(-5.0,1.1,0);
 for(i=0;i<strlen(m3);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m3[i]);

 glRasterPos3f(-5.0,0.9,0);
 for(i=0;i<strlen(m4);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m4[i]);

 glRasterPos3f(-5.0,0.7,0);
 for(i=0;i<strlen(m5);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m5[i]);

 glRasterPos3f(-5.0,0.5,0);
 for(i=0;i<strlen(m6);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m6[i]);

 glRasterPos3f(-5.0,0.3,0);
 for(i=0;i<strlen(m7);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m7[i]);

 glRasterPos3f(-5.0,0.1,0);
 for(i=0;i<strlen(m8);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m8[i]);

 glRasterPos3f(-5.0,-0.1,0);
 for(i=0;i<strlen(m9);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m9[i]);

 glRasterPos3f(-5.0,-0.3,0);
 for(i=0;i<strlen(m10);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m10[i]);

 glRasterPos3f(-5.0,-0.5,0);
 for(i=0;i<strlen(m11);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m11[i]);

 glRasterPos3f(-0.5,1.5,0);
 for(i=0;i<strlen(m12);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m12[i]);

 glRasterPos3f(-0.5,1.3,0);
 for(i=0;i<strlen(m13);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m13[i]);

 glRasterPos3f(-0.5,1.1,0);
 for(i=0;i<strlen(m14);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m14[i]);

 glRasterPos3f(-0.5,0.9,0);
 for(i=0;i<strlen(m15);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m15[i]);

 glRasterPos3f(-0.5,0.7,0);
 for(i=0;i<strlen(m16);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m16[i]);

 glRasterPos3f(-0.5,0.5,0);
 for(i=0;i<strlen(m17);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m17[i]);

 glRasterPos3f(-0.5,0.3,0);
 for(i=0;i<strlen(m18);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m18[i]);

 glRasterPos3f(-0.5,0.1,0);
 for(i=0;i<strlen(m19);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m19[i]);

 glRasterPos3f(-0.5,-0.1,0);
 for(i=0;i<strlen(m20);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m20[i]);

 glRasterPos3f(-0.5,-0.3,0);
 for(i=0;i<strlen(m21);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m21[i]);

 glRasterPos3f(-0.5,-0.5,0);
 for(i=0;i<strlen(m22);i++)
 glutBitmapCharacter(GLUT_BITMAP_9_BY_15,m22[i]);

glutSwapBuffers();
}
void exitdisplay()
{
 int i;
 char exit1[]="EXIT";
 char exit2[]="THANK YOU";
 glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
 glColor3f(1.0,1.0,1.0);
 glRasterPos3f(-2.5,0,0);
 for(i=0;i<strlen(exit1);i++)
 glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,exit1[i]);
 glRasterPos3f(0,0,0);
    for(i=0;i<strlen(exit2);i++)
    glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,exit2[i]);
glutSwapBuffers();
}
void reshape(int w,int h)
{
glViewport(0,0,(GLsizei)w,(GLsizei)h);
glMatrixMode(GL_PROJECTION);
glLoadIdentity();
gluPerspective(60.0,(GLfloat)w/(GLfloat)h,1.0,20.0);
glMatrixMode(GL_MODELVIEW);
glLoadIdentity();
gluLookAt(0.0,0.0,5.0,0.0,0.0,0.0,0.0,1.0,0.0);
}

void keyboard(unsigned char key,int x,int y)
{
switch(key)
{
case 'G':glutDisplayFunc(display);
         glutPostRedisplay();
         break;
case 'F':glutDisplayFunc(menudisplay);
         glutPostRedisplay();
         break;
case 'D':glutDisplayFunc(exitdisplay);
         glutPostRedisplay();
         break;
case 'z':z=(z+50)%360;
         glutPostRedisplay();
         break;
case 'm':m=(m+3)%360;
         glutPostRedisplay();
         break;
case 'M':M=(M+12)%360;
         glutPostRedisplay();
         break;
case 'v':v=(v+2)%360;
         glutPostRedisplay();
         break;
case 'V':V=(V+10)%360;
         glutPostRedisplay();
         break;
case 'e':e=(e+5)%360;
         glutPostRedisplay();
         break;
case 'E':E=(E+8)%360;
         glutPostRedisplay();
         break;
case 'r':r=(r+6)%360;
         glutPostRedisplay();
         break;
case 'R':R=(R+6)%360;
         glutPostRedisplay();
         break;
case 'j':j=(j+10)%360;
         glutPostRedisplay();
         break;
case 'J':J=(J+4)%360;
         glutPostRedisplay();
         break;
case 's':s=(s+9)%360;
         glutPostRedisplay();
         break;
case 'S':S=(S+3)%360;
         glutPostRedisplay();
         break;
case 'u':u=(u+8)%360;
         glutPostRedisplay();
         break;
case 'U':U=(U+2)%360;
         glutPostRedisplay();
         break;
case 'n':n=(n+7)%360;
         glutPostRedisplay();
         break;
case 'N':N=(N+1)%360;
         glutPostRedisplay();
         break;
case 'b':b=(b+10)%360;
         glutPostRedisplay();
         break;
case 'c':c=(c+1)%360;
         b=(b+10)%360;
         glutPostRedisplay();
         break;
case 'X':X=(X+5)%360;
         glutPostRedisplay();
         break;
case 'a':z=(z+50)%360;
         b=(b+10)%360;
         m=(m+3)%360;
         v=(v+2)%360;
         e=(e+5)%360;
         r=(r+6)%360;
         j=(j+10)%360;
         s=(s+9)%360;
         u=(u+8)%360;
         n=(n+7)%360;
         c=(c+1)%360;
         glutPostRedisplay();
         break;
case 'A':z=(z+50)%360;
         b=(b+10)%360;
         M=(M+12)%360;
         V=(V+10)%360;
         E=(E+8)%360;
         R=(R+6)%360;
         J=(J+4)%360;
         S=(S+3)%360;
         U=(U+2)%360;
         N=(N+1)%360;
         c=(c+1)%360;
         glutPostRedisplay();
         break;
case 'B':z=(z+50)%360;
         b=(b+10)%360;
         c=(c+1)%360;
         m=(m+3)%360;M=(M+12)%360;
         v=(v+2)%360;V=(V+10)%360;
         e=(e+5)%360;E=(E+8)%360;
         r=(r+6)%360;R=(R+6)%360;
         j=(j+10)%360;J=(J+4)%360;
         s=(s+9)%360;S=(S+3)%360;
         u=(u+8)%360;U=(U+2)%360;
         n=(n+7)%360;N=(N+1)%360;
         glutPostRedisplay();
         break;
case 'h':exit(0);
       break;
default:break;
}
}
void mouse(int btn ,int state,int x,int y)
{
if(btn==GLUT_LEFT_BUTTON && state==GLUT_DOWN)
{
z=(z+50)%360;
b=(b+10)%360;
c=(c+1)%360;
m=(m+3)%360;M=(M+12)%360;
v=(v+2)%360;V=(V+10)%360;
e=(e+5)%360;E=(E+8)%360;
r=(r+6)%360;R=(R+6)%360;
j=(j+10)%360;J=(J+4)%360;
s=(s+9)%360;S=(S+3)%360;
u=(u+8)%360;U=(U+2)%360;
n=(n+7)%360;N=(N+1)%360;
glutPostRedisplay();
}
if(btn==GLUT_RIGHT_BUTTON && state==GLUT_DOWN)
{
z=(z-50)%360;
b=(b-10)%360;
c=(c+1)%360;
m=(m-3)%360;M=(M-12)%360;
v=(v-2)%360;V=(V-10)%360;
e=(e-5)%360;E=(E-8)%360;
r=(r-6)%360;R=(R-6)%360;
j=(j-10)%360;J=(J-4)%360;
s=(s-9)%360;S=(S-3)%360;
u=(u-8)%360;U=(U-2)%360;
n=(n-7)%360;N=(N-1)%360;
glutPostRedisplay();
}
}
int main(int argc,char **argv)
{
glutInit(&argc,argv);
glutInitDisplayMode(GLUT_DOUBLE|GLUT_RGB|GLUT_DEPTH);
glutInitWindowSize(500,500);
glutInitWindowPosition(100,100);
glutCreateWindow("SOLAR SYSTEM");
myinit();
glutDisplayFunc(welcomedisplay);
glutReshapeFunc(reshape);
//glutKeyboardFunc(key);
glutKeyboardFunc(keyboard);
glutMouseFunc(mouse);
glEnable(GL_DEPTH_TEST);
glutMainLoop();
return 0;
}

