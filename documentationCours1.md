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
  <li>On the left bar, click on course administration</li>
  <li>On the left bar of the administration page, click on <b>Tasks</b></li>
  <li>On the top right of the list of exercise, click on the three lines / the hamburger menu</li>
  <li>Click on <b>Add tasks</b></li>
  <li>Enter a unique identifier for your exercise</li>
  <li>Click on the button <b>Create new task</b></li>
  <li>On the right bottom part, click on the <b>Save changes</b> button</li>
  <li>On the right part of your exercise in the list of exercise, click on the <b>Task settings</b> button (dark blue button)</li>
  <li>Set the accessibility to <b>Always</b></li>
  <li>Click on close</li>
  <li>Click on the <b>Save changes</b> button</li>
  <li>Click on the <b>Edit task</b> button (light blue)</li>
  <li>Enter a name to the exercise. This name will be displayed to the students in the list of exercises</li>
  <li>Enter a context to the exercise. This context will act as the guidelines of the exercise. It should explain what will be the goal of students in this exercise</li>
  <li>Click on <b>Environment</b> tab</li>
  <li>Select the <b>Standard container</b> from the `Grading environment type` selection menu</li>
  <li>Select the <b>default</b> from the `Grading environment` selection menu</li>
  <li>Click on <b>Subproblems</b> tab</li>
  <li>Enter a problem id in <b>New problem id</b> input. This will be useful later to indicate where the code of the student will be added. The problem id for this tutorial will be <b>q1</b></li>
  <li>Click on the <b>Add</b> button to the right</li>
  <li>Click on the <b>Task files</b> tab</li>
  <br>
  This is where you will find all the files of your exercise. While there are many ways to write an exercise on INGInious, we will guide you with a given structure of files.

  <ul>
    <li><b>run</b> : This is the first file executed when writing an exercise. It should at least get the code of the student, run the tests and provide a score and a feedback</li>
    <li><b>src/Correction.py</b> : This should contain the expected implementation of the solution. This file will be used in the tests to compare the expected output with the one of the student</li>
    <li><b>src/Templates/template</b> : This file should contain the same content as the Correction file except the code giving the solution should be replace by the following tag : @@problem_id@@. This special tag will get the code of the code editor of the student and inject the content of it at the place of the template. In our case, we will put @@q1@@ as we gave this name to our subproblem previously</li>
    <li><b>src/Test.py</b> : This file should contain all the tests that will be used to check the solution of the student. Each test case should call the Correction code and should call the code of the student. Then, an assertion should be made to check the same output between the correction and the student code</li>
  </ul>

  <li>Once every files are written, click on <b>Save changes</b/>. The exercise is now ready</li>
</ol>
