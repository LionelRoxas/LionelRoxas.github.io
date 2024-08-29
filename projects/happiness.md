---
layout: project
type: project
image: img/plot_display.png
title: "Exploring the Global Impacts of Covid-19"
date: 2024
published: true
labels:
  - Python
  - Numpy
  - Scikit-Learn
  - Pandas
  - GeoPandas
  - Seaborn
  - Matplotlib
  - Paired T-Test
  - Regression and Predictive Model
  - Jupyter Labs
  - Kaggle
summary: "Analyzed the impact of COVID-19 on global happiness scores and identified regional and national variations."
---

<div class="text-center p-4">
  <img width="500px" src="../img/happiness_title.png" class="img-thumbnail" >
  <img width="500px" src="../img/table_of_contents.png" class="img-thumbnail" >
</div>

<h2>
  <strong>Research Question and Hypothesis</strong>
</h2>
<div class="text-center p-4">
  <img width="500px" src="../img/research_question.png" class="img-thumbnail" >
  <img width="500px" src="../img/hypothesis.png" class="img-thumbnail" >
</div>

For this project, I served as the lead developer, responsible for designing and implementing the app's core functionalities. I started by developing the backend using <strong>Node.js</strong> and <strong>Express.js</strong>, creating <strong>APIs</strong> to manage user authentication, student data, and point allocation. I also worked on integrating a <strong>MongoDB</strong> database to store and retrieve information efficiently. On the frontend, I used <strong>React</strong> to build a user-friendly interface, allowing admins and members to interact with the app seamlessly. I implemented features such as a group code system for secure student access, real-time updates to reflect point changes, and a leaderboard to display student rankings. By focusing on both the backend and frontend, I ensured a cohesive and scalable application that successfully engages users and meets their needs.

Here is an example of <strong>'useState'</strong> and <strong>'useEffect'</strong> hooks to demonstrate how React was used:

```cpp
import React, { useState, useEffect } from 'react';

function App() {
  const [students, setStudents] = useState([]);
  const [userRole, setUserRole] = useState(null);
  const [showPasswordPrompt, setShowPasswordPrompt] = useState(false);
  const [showClassCodePrompt, setShowClassCodePrompt] = useState(false);
  const [token, setToken] = useState(localStorage.getItem('token') || '');
  const [classCode, setClassCode] = useState(localStorage.getItem('classCode') || '');

  useEffect(() => {
    if (token && classCode) {
      // Fetch students from API when token and classCode are available
    }
  }, [token, classCode]);
}
```
Next, here is an example of API integration using <strong>Axios</strong> to interact with the backend:

```cpp
const addPoints = (studentId, points, reason) => {
  axios.post(`${apiUrl}/students/${studentId}/addPoints`, { points, reason, classCode }, {
    headers: { Authorization: `Bearer ${token}` }
  })
  .then(response => setStudents(students.map(student =>
    student._id === studentId ? response.data : student
  )))
  .catch(error => console.error(error));
};

useEffect(() => {
  if (token && classCode) {
    axios.get(`${apiUrl}/students`, {
      headers: { Authorization: `Bearer ${token}` },
      params: { classCode }
    })
    .then(response => setStudents(response.data))
    .catch(error => console.error(error));
  }
}, [token, classCode]);
```
Overall, I utilized React's 'useState' and 'useEffect' hooks for effective state management and to handle side effects such as data fetching from an API. I implemented conditional rendering to dynamically display different views based on user roles and authentication status. I integrated Axios for seamless API communication, allowing the app to manage student data and user sessions efficiently. To enhance user experience, I used local storage to persist user sessions, ensuring that key information such as authentication tokens and class codes remain available across sessions.

You can learn more at the [Point System App](https://lionelroxas.github.io/point-system-app-frontend).
