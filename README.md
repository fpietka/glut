# glut

## Abstract
This is freeglut binding for the programming language Go. It works on linux.

## Installation

	go get github.com/vitalibaumtrok/glut
	go install github.com/vitalibaumtrok/glut

To update the package type

	go get -u github.com/vitalibaumtrok/glut

_Note: You need the programming language Go and git to run these commands._

## Development
Programming language Go is used.

## Example
	package main

	import (
		"github.com/vitalibaumtrok/glut"
	)

	func main() {
		glut.Init()
		glut.InitDisplayMode(glut.SINGLE | glut.RGBA)
		glut.InitWindowSize(640, 480)
		glut.CreateWindow("Testing GLUT binding for Go");
		glut.ReshapeFunc(reshape)
		glut.DisplayFunc(display)
		glut.KeyboardFunc(keyboard)
		glut.MainLoop()
	}

	func reshape(width, height int) {
		println("reshape")
	}

	func display() {
		println("display")
	}

	func keyboard(key uint8, x, y int) {
		if key==27 { // escape
			glut.DestroyWindow(glut.GetWindow())
		} else {
			if (glut.GetModifiers() & glut.ACTIVE_CTRL) > 0 {
				println("key pressed: ctrl +", key)
			} else {
				println("key pressed:", key)
			}
		}
	}

## Coverage

	Initialization (100%)
	  void glutInit(int *argcp, char **argv)
	  void glutInitWindowSize(int width, int height)
	  void glutInitWindowPosition(int x, int y)
	  void glutInitDisplayMode(unsigned int mode)

	Event Processing (100%)
	  void glutMainLoop(void)

	Window Management (100%)
	  int glutCreateWindow(char *name)
	  int glutCreateSubWindow(int win, int x, int y, int width, int height)
	  void glutSetWindow(int win);
	  int glutGetWindow(void);
	  void glutDestroyWindow(int win)
	  void glutPostRedisplay(void)
	  void glutSwapBuffers(void)
	  void glutPositionWindow(int x, int y)
	  void glutReshapeWindow(int width, int height)
	  void glutFullScreen(void)
	  void glutPopWindow(void)
	  void glutPushWindow(void)
	  void glutShowWindow(void)
	  void glutHideWindow(void)
	  void glutIconifyWindow(void)
	  void glutSetWindowTitle(char *name)
	  void glutSetIconTitle(char *name)
	  void glutSetCursor(int cursor)

	Overlay Management (100%)
	  void glutEstablishOverlay(void)
	  void glutUseLayer(GLenum layer)
	  void glutRemoveOverlay(void)
	  void glutPostOverlayRedisplay(void)
	  void glutWindowPostOverlayRedisplay(int win)
	  void glutShowOverlay(void)
	  void glutHideOverlay(void)

	Menu Management (0%)

	Callback Registration (48%)
	  void glutDisplayFunc(void (*func)(void))
	  void glutOverlayDisplayFunc(void (*func)(void))
	  void glutReshapeFunc(void (*func)(int width, int height))
	  void glutKeyboardFunc(void (*func)(unsigned char key, int x, int y))
	  void glutMouseFunc(void (*func)(int button, int state, int x, int y))
	  void glutMotionFunc(void (*func)(int x, int y))
	  void glutPassiveMotionFunc(void (*func)(int x, int y))
	  void glutVisibilityFunc(void (*func)(int state))
	  void glutEntryFunc(void (*func)(int state))
	  void glutTimerFunc(unsigned int msecs, void (*func)(int value), int value)
	  void glutIdleFunc(void (*func)(void))

	Colormap Management (100%)
	  void glutSetColor(int cell, GLfloat red, GLfloat green, GLfloat blue)
	  GLfloat glutGetColor(int cell, int component)
	  void glutCopyColormap(int win)

	State Retrieval (100%)
	  int glutGet(GLenum state)
	  int glutLayerGet(GLenum info)
	  int glutDeviceGet(GLenum info)
	  int glutGetModifiers(void)
	  int glutExtensionSupported(char *extension)

	Font Rendering (0%)

	Geometric Object Rendering (0%)

## Copyright
Copyright 2014 Vitali Baumtrok

This program is distributed under the terms of the Boost Software License,
Version 1.0. (See accompanying file LICENSE_1_0.txt or copy
at http://www.boost.org/LICENSE_1_0.txt)
