# **Workshop Booking**

> This website is for coordinators to book a workshop(s), they can book a workshop based on instructors posts or can propose a workshop date based on their convenience.


### Features
* Statistics
    1. Instructors Only
        * Monthly Workshop Count
        * Instructor/Coordinator Profile stats
        * Upcoming Workshops
        * View/Post comments on Coordinator's Profile
    2. Open to All
        * Workshops taken over Map of India
        * Pie chart based on Total Workshops taken to Type of Workshops.

* Workshop Related Features
    > Instructors can Accept, Reject or Delete workshops based on their preference, also they can postpone a workshop based on coordinators request.

__NOTE__: Check docs/Getting_Started.md for more info.

# Workshop Booking

## Project Overview

This is a Django-based web application for managing workshop bookings and statistics. The project is structured with separate apps for core workshop functionalities (`workshop_app`), statistics (`statistics_app`), and content management (`cms`).

## Project Setup Instructions

This guide will walk you through the steps to set up and run the Django project locally.

### Prerequisites

* **Python:** Ensure you have Python installed (version 3.6 or higher is recommended).
* **Git:** You need Git to clone the repository.

### 1. Clone the Repository

First, clone the project from GitHub to your local machine using the following command:

```bash
git clone [https://github.com/your-username/workshop_booking.git](https://github.com/your-username/workshop_booking.git)
cd workshop_booking

Set Up a Virtual Environment
It's highly recommended to use a virtual environment to manage the project's dependencies and avoid conflicts with other Python projects.

# Create a virtual environment
python -m venv venv

# Activate the virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

3. Install Dependencies
Install all the required packages. This project uses Django and other packages. If you have a requirements.txt file, you can install them all at once:
pip install -r requirements.txt

4. Run Database Migrations
After installing the dependencies, you need to set up the database. Django uses migrations to manage database schemas. Run the following commands to create the necessary tables:

python manage.py makemigrations
python manage.py migrate

5. Run the Development Server
You can now start the local development server and access the website.

python manage.py runserver

Open your web browser and navigate to http://127.0.0.1:8000/ to view the website.


### Reasoning

Ques - What design principles guided your improvements?
Ans- My improvements were guided by the following design principles:

Consistency: The goal was to create a uniform look and feel across all pages, ensuring the navigation bar, footer, and other common elements have a consistent style. The base.css file was structured to act as a global style guide for the entire application, so any page that includes it will have the same foundational styling.

Modularity: By separating the general, site-wide styles from the page-specific layouts, the design became more modular. The base.css file now handles the "shell" of the application (like the body, navbar, and footer), while the individual page templates (e.g., for the login page and statistics page) use Bootstrap's grid system to create their unique layouts without conflicting with the base styles. This makes the code easier to manage and debug.

Clarity and Simplicity: The designs were kept clean and uncluttered. The use of a simple color palette, clear typography, and card-based layouts helps to highlight important information and guide the user's eye.

Ques- How did you ensure responsiveness across devices?
Ans- Responsiveness was ensured by using a mobile-first approach with CSS media queries.

Flexible Layouts: The layout for the main content was changed from a rigid, centered box to a more flexible, column-based layout using display: flex on the body and flex: 1 on the main content container. This allows the page to adapt to different screen sizes without breaking.

Media Queries: I added a media query that specifically targets smaller screens (under 768px). This allowed me to adjust padding, font sizes, and other dimensions for mobile devices. For example, the padding-top on the body was reduced for mobile to prevent the content from being hidden behind the navbar, which often has a different height on smaller screens.

Bootstrap's Grid System: The project already uses Bootstrap, which has a built-in responsive grid system (.row and .col-*). By ensuring the page's HTML uses these classes correctly, the layout automatically adjusts based on the device's screen size

Ques- What trade-offs did you make between the design and performance?
Ans- A key trade-off was between design flexibility and performance.

Flexibility over Minimal CSS: The decision was made to use a single base.css file for the entire site. While this approach is less performant than loading only the necessary CSS for each page (since some pages might not need all the styles in base.css), it greatly simplifies the development workflow and ensures design consistency. The alternative would have been to have separate, smaller CSS files for each page, which is better for performance but requires more management.

Code Duplication: While the base.css is universal, a few of the styles might be specific to certain pages (e.g., card styles). If a page doesn't use cards, those lines of CSS are technically unnecessary. However, the performance impact is negligible for a small project, and the benefit of a clean, universal stylesheet outweighs the cost.

Ques- What was the most challenging part of the task and how did you approach it?
Ans- The most challenging part was resolving the CSS conflicts between the universal base.css and the specific page layouts.

The Problem: The base.css file was initially designed with a display: flex rule and centering properties for a single-card layout. This worked for the login page, but it created a major conflict on the statistics page, where a two-column layout was needed. This caused the sidebar to overlap with the main content, making the page unusable.

The Approach: The solution was to stop treating base.css as a layout file and start treating it as a universal style guide. I removed the layout-specific CSS from the base.css and added a more flexible .main-content container. This allowed the individual page templates to use Bootstrap's grid system to define their layouts without fighting against the base stylesheet. The footer's positioning was also a challenge, as position: fixed was causing it to overlap; the issue was solved by using the modern flexbox min-height: 100vh approach, which correctly places the footer at the bottom of the content without overlapping.

### Visual Showcase:

Before -
![Before Screenshot of my project](https://raw.githubusercontent.com/Kartikay-goel/PythonTask1/master/ss1.jpg)

After -
![After Screenshot of my project](https://raw.githubusercontent.com/Kartikay-goel/PythonTask1/master/ss2.jpg)
![After Screenshot of my project](https://raw.githubusercontent.com/Kartikay-goel/PythonTask1/master/ss3.jpg

