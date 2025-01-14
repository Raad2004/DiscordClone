# Milestone #7 - Final Delivery  

## Video Walkthrough  
A video walkthrough of our project showcasing the implemented features, system architecture, and deployment process is available at the following link:  
[Discord Clone Demo](https://youtu.be/j640v_kySnI)  

---

## General Development  

### 1. What did your team build?  
We built a simplified Discord clone, a web-based communication platform designed for real-time messaging and user interaction. The key features include:  
#### a. Authentication  
- Integrated a secure authentication system using **Clerk**, allowing users to:  
  - Sign up with an email or supported third-party services.  
  - Log in with their credentials for a seamless experience.  
  - Log out securely when their session ends.  

#### b. Real-Time Messaging  
- Implemented real-time messaging capabilities, enabling users to:  
  - Send and receive messages in **dedicated channels** instantly.  
  - Switch between channels without losing context.  

#### c. Channel-Based Communication  
- Created **multiple channels**, allowing users to organize discussions by topic or purpose.  
- Designed functionality to create channels and categories

#### d. UI/UX Design  
- Built an **intuitive and responsive interface** using **Next.js** with a focus on:  
  - Clean navigation to access channels and settings effortlessly.  
  - A visually appealing layout inspired by Discord’s simplicity while adding our unique touch.  

---

### 2. Requirements Checklist  
| Feature                | State (Complete/Incomplete) | Notes                          |
|------------------------|-----------------------------|--------------------------------|
| Authentication         | Complete                   | Using Clerk for seamless integration.  
| Real-time Messaging    | Complete                   | Fully functional utilizing Stream.  
| Server and Channel Creation    | Complete                   | Fully functional using APIs, Next.js, and Tailwind CSS
| Notification System | Complete | Visual cues for new notifications implemented
| Audio Channels | Incomplete | 


---

### 3. System Architecture  
The system uses a **client-server architecture** with the following components:  
- **Frontend:** Built with Next.js and TypeScript for a dynamic user experience.  
- **Backend:** Node.js server with REST APIs for user and messaging services.  
- **Database:** Clerk and Stream both host and store data related to users and messaging.

---

### 4. Code Reuse  
Our team achieved a moderate to high degree of code re-use by leveraging third-party libraries. The focus was on minimizing redundant code and utilizing pre-existing solutions where appropriate.

- Authentication with Clerk: We utilized the Clerk authentication library, which provided robust and pre-built components for user sign-up, log-in, and session management. This saved significant development time while ensuring secure and reliable authentication.
- Channel Management: Instead of building real-time messaging and state synchronization from scratch, we used well-supported libraries to handle WebSocket connections and updates efficiently.
- UI Components: Pre-built UI libraries were used for styling and responsiveness, ensuring that the interface adhered to modern design standards without creating components from the ground up.

---

### 5. Backlog  
There are no major tasks left in the backlog. The remaining items are minor enhancements and non-essential features.  

---

## CI/CD  

### 1. Testing Strategies  
- **Unit Tests:** Components that could be tested using mocking were tested using the Jest library.
- **Integration Tests:** End-to-end tests for key workflows. Due to the nature of the project, this was mostly done by running the application and verifying the added functionality works as well as old functionality. 
- **Future Improvements:** Increase test coverage and establish automated testing earlier in development to minimize debugging overhead.  

---

### 2. Branching Workflow  
Our team followed a **feature-branch workflow**:  
- Each branch underwent code reviews via detailed pull requests and requiring approvals from the rest of the development team.  
- Workflow and merging was smooth with minimal to no conflicts established through good communication and distribution of tasks.  

---

### 3. Deployment  

Our application is fully dockerized and tested for a development environment. It contains a Dockerfile and docker-compose file which defines some instructions on building an image and allows us to configure and manage our docker application, respectively. The Dockerfile uses a lightweight node image, installs dependencies, and runs the application using 'npm run dev'. 

To deploy, we run docker-compose up which will build and run the container which will make it accessible at localhost:3000. In our docker-compose, we mount the current directory to the app directory inside the container (where the app is held). Therefore, when changes are made in the code, it will be reflected in real time in the container.


---

## Reflections  

### 1. Project Management  

For project management, we used a combination of Kanban and weekly sprints. The Kanban board allowed us to visualize the flow of tasks and prioritize work, while the weekly sprints kept us on track and ensured steady progress. The hardest part was integrating the Stream Chat API with user authentication, as it required managing state across multiple components. Also, none of us have used StreamChat before so it required some time to research documentation and videos to help with integrating into our project. In the future, we would focus more on detailed planning in the early stages to address edge cases, and improve our documentation to make collaboration smoother.

---

### 2. Requirements  
We believe that the requirements were detailed but we may have overlooked a few things. For example, we probably should have done some research on audio channels before making them a requirement. We ended up not implementing it but the requirement could be a future one that we end up implementing on our own time. 

Our requirements were sufficient but we should have done a slightly deeper analysis on all of our requirements in order to make sure that they were feasable in the time frame given. We could have listed some future requirements and moved the audio channel requirement to that section.

---

### 3. Planning Gaps  
Missed accounting for deployment challenges and setting up CI/CD pipelines early. We also did not account much for other classes and responsibilities for our team members. This made it difficult when we had super busy weeks but we still had to stay on track for the weekly milestones.  

---

### 4. Process Management and Observations
We used a kanban board to keep track of our backlog, read, in progress, review, and done issues. This gave us a nice visualization to show our progress and what still needs to be done. We would, once a week, meet with the team and discuss what needed to be done for the next week to hit our goals and meet for the milestone with the TA -- we would use the kanban board as a resource during this meeting.

---

### 5. IDE and Environment Issues  
We encountered minor issues with differing IDE setups, especially when it came to different OS. There were some minor tweaks here and there but overall, the system runs smoothly no matter the OS and IDE. We also all agreed to use VSC as our IDE so it made it easier to debug issues. 

---

### 6. Effort Estimation  
Initial estimations underestimated testing and debugging time. In the future, we have discussed that testing and debugging should always be estimated with a large cushion. This gives the development team enough time to debug and also have enough time to implement new features.

We also have seen this issue in other projects/teams so we think that this is a common issue of estimation.

---

### 7. Unique Contribution and Learning
In our project, one of the most unique challenges we faced was integrating the Clerk.io API for authentication. For a long time, it wasn't working correctly, and we kept encountering errors that were difficult to diagnose. After extensive debugging and scouring online forums, we discovered the issue: windows 10 time was slightly desynchronized off by just two seconds.

Since Clerk.io generates authentication keys that are only valid for a few seconds, our keys were expiring before they could be used, making authentication fail every time. This was a big learning moment for us. In the end it was a simple fix. All we had to do is synchronize our times on windows and the everything was working as expected.


It taught us that not all issues are logical or syntax-based. Sometimes, the problems lie outside the code, in areas like system settings or environment configurations. This experience emphasized the importance of looking beyond the obvious and reinforced the value of persistence and thorough investigation in problem-solving.

---

### 8. AI's Impact  
The impact of AI in our project was mainly used for debugging. AI helped us understand the error messages and possible causes that pointed us to the correct direction on where to make the changes which resulted in an easier debugging process. This was an extremely useful tool when working with unknown libraries as, even with good documentation, we needed to understand where in the documentation to look which could only be done by understanding the error messages. This also helped us with minor UI improvements where a div would be hard to place in the layout.

---
