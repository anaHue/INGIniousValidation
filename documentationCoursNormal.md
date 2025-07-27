# Documentation
This file contains the documentation for the implementation of an exercise for INGInious. It includes an overview of the project and a list of steps to follow to write an exercise on INGInious.

## Overview
INGInious provides a simple and secure way to execute and test untrusted code. It has been developed by the INGI department (Université catholique de Louvain) to automatic grading of programming assignments. The whole tool is written in Python (version 3.5+) and relies on Docker to provide secure execution environments and on MongoDB to keep track of submissions.

INGInious is completely language-agnostic and is able to run anything. Currently, this is limited to Linux programs as only Linux containers are provided and supported.

INGInious also provides an LTI module, allowing its integration to your existing (Open) edX, Moodle,… courses.

This tutorial supposes you are already connected to an account and have already a course created on INGInious. This tutorial starts on the courselist page.

## Steps to follow to create an exercise

<ol>
  <li>Click on your course</li>
  <li>On the left bar, click on <b>Course administration</b></li>
  <li>On the left bar of the administration page, click on <b>Tasks</b></li>
  <li>On the top right of the list of exercise, click on the three lines / the hamburger menu</li>
  <li>Click on <b>Add tasks</b></li>
  <li>Enter a unique identifier for your exercise. For example, you can put the name of your exercise (hello-world/average/...)</li>
  <li>Click on the button <b>Create new task</b></li>
  <li>On the right bottom part, click on the <b>Save changes</b> button</li>
  <li>On the right part of your exercise in the list of exercise, click on the <b>Task settings</b> button (dark blue button)</li>
  <li>Set the Accessibility to <b>Always</b> at the bottom of the modal</li>
  <li>Click on Close</li>
  <li>Click on the <b>Save changes</b> button</li>
  <li>Click on the <b>Edit task</b> button (light blue)</li>
  <li>Enter a name to the exercise. This name will be displayed to the students in the list of exercises</li>
  <li>Enter a context to the exercise. This context will act as the guidelines of the exercise. It should explain what will be the goal of students in this exercise</li>
  <li>Click on <b>Environment</b> tab</li>
  <li>Select the <b>Standard container</b> from the <b>Grading environment type</b> selection menu</li>
  <li>Select the <b>default</b> from the Grading environment selection menu</li>
  <li>Click on <b>Subproblems</b> tab</li>
  <li>Enter a problem id in <b>New problem id</b> input. This will be useful later to indicate where the code of the student will be added. The problem id for this tutorial will be <b>q1</b></li>
  <li>Click on the <b>Add</b> button to the right</li>
  <li>Click on the <b>Task files</b> tab</li>
  <br>
  This is where you will find all the files of your exercise. While there are many ways to write an exercise on INGInious, this tutorial will guide you with a given structure of files. You can directly write the following files at the root. You do not need to write folder called task.

  <ul>
    <li><b>run</b> : This is the first file executed when writing an exercise. It should at least get the code of the student, run the tests and provide a score and a feedback</li>
    <li><b>template.py</b> : This file should contain the same content as the Correction file except the code giving the solution should be replace by the following tag : @@problem_id@@. This special tag will get the code of the code editor of the student and inject the content of it at the place of the template. In our case, we will put @    @q1@@ as we gave this name to our subproblem previously. The tab between the two first @ means that the code of the student will be correctly indented to where the code of the student should be injected.</li>

    def func():
    @    @q1@@

    <li><b>Test.py</b> : This file should contain all the tests that will be used to check the solution of the student. Each test case should call the Correction code and should call the code of the student. Then, an assertion should be made to check the same output between the correction and the student code</li>
    <li>Correction.py : While it is not mandatory, you can create a correction file. This should contain the expected implementation of the solution. This file will be used in the tests to compare the expected output with the one of the student</li>
  </ul>

  <li>Once every files are written, click on <b>Save changes</b/>. The exercise is now ready</li>
</ol>

## Useful instructions for the files

### run

Here are some guidelines on how to write a run file:

<ul>
  <li>It must begin with a shebang : <b>#!/bin/bash</b></li>
  <li>To parse the template (which will inject the code of the student), you can use : <b>parsetemplate /task/template.py</b></li>
  <li>To run the tests, you can use : <b>python3 /task/Test.py 2> stderr.log</b></li>
  <li>To give a score and a feedback, you can use:
  
    if [ "$(tail -n 1 stderr.log)" != "OK" ]; then
      error=$(cat stderr.log)
      feedback-result failed
      feedback-msg -em "$error"
    else
      feedback-result success
      feedback-msg -em "Your code is correct"
    fi
  </li>
</ul>

### Test.py

Here are some guidelines on how to write a Test.py file:

<ul>
  <li>It must be a pyunit Test class</li>
  <li>To call the code of the student, you must <b>import template</b> and later use <b>template.YOUR_METHOD</b></li>
  <li>The file must end with :
  
      if __name__ == "__main__":
        unittest.main()
  </li>
</ul>

## How to test your exercise ?

Once you saved after writing every files, you should :

<ul>
  <li>Click on <b>view task</b> on top right</li>
  You are now able to submit an answer to see if the exercise works as expected.
  <br>
  If you have no code editor, make sure you defined a subproblem on the <b>Subproblems</b> tab.
  <li>On the left menu, click on edit task if you wish to make other modifications</li>
</ul>