# monishwar-1st-website-
A responsive student portal showcasing names, register numbers, photos, and marks. Features a navigation bar, styled table, and interactive forms. Uses HTML for structure, CSS for design, and JavaScript for validation, dynamic updates, and theme switching, creating an attractive and functional web experience.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tech Learners Hub</title>
    <link rel="stylesheet" href="monish.css">
    <script src="script.js"></script>
</head>
<body>
    <!-- HEADER -->
    <header>
        <h1>Welcome to Tech Learners Hub</h1>
    </header>

    <!-- NAVIGATION -->
    <nav>
        <a href="#">Home</a>
        <a href="#">Courses</a>
        <a href="#">Contact</a>
    </nav>

    <!-- MAIN CONTENT -->
    <main>
        <!-- STUDENT TABLE -->
        <section>
            <h2>Our Learners</h2>
            <p id="studentCount"></p>
            <table id="studentTable">
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Age</th>
                        <th>Skill</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Ravi</td>
                        <td>21</td>
                        <td>Python</td>
                    </tr>
                    <tr>
                        <td>Meena</td>
                        <td>22</td>
                        <td>JavaScript</td>
                    </tr>
                    <tr>
                        <td>Arun</td>
                        <td>20</td>
                        <td>UI/UX</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- ADD STUDENT FORM -->
        <section>
            <h3>Add New Learner</h3>
            <form id="addStudentForm">
                <label>Name: <input type="text" id="newName"></label>
                <label>Age: <input type="number" id="newAge"></label>
                <label>Skill: <input type="text" id="newSkill"></label>
                <button type="submit">Add Learner</button>
            </form>
        </section>

        <!-- CONTACT FORM -->
        <section>
            <h3>Contact Us</h3>
            <form id="contactForm">
                <label>Name: <input type="text" id="name"></label>
                <label>Email: <input type="email" id="email"></label>
                <label>Message: <textarea id="message"></textarea></label>
                <button type="submit">Submit</button>
            </form>
            <p id="formMessage"></p>
        </section>

        <!-- THEME BUTTON -->
        <button id="themeToggle">Change Theme</button>
    </main>

    <!-- FOOTER -->
    <footer>
        <p>&copy; 2025 Tech Learners Hub</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>

css :
body {
    font-family: 'Segoe UI', sans-serif;
    margin: 0;
    padding: 0;
    background: linear-gradient(to right, #ece9e6, #ffffff);
    color: #333;
    transition: all 0.3s ease-in-out;
}

header {
    background: #0077b6;
    color: white;
    padding: 1rem;
    text-align: center;
}

nav {
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    background: #023e8a;
    padding: 0.7rem;
}

nav a {
    color: white;
    text-decoration: none;
    font-weight: bold;
    transition: 0.3s;
}

nav a:hover {
    color: #ffd60a;
    text-shadow: 0 0 5px #fff;
}

main {
    padding: 1.5rem;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 1rem;
}

th, td {
    border: 1px solid #ccc;
    padding: 0.6rem;
    text-align: center;
}

tbody tr:nth-child(even) {
    background: #f9f9f9;
}

form {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    margin-bottom: 1.5rem;
    background: white;
    padding: 1rem;
    border-radius: 8px;
    box-shadow: 0 2px 6px rgba(0,0,0,0.1);
}

form input, form textarea, form button {
    padding: 0.5rem;
    border-radius: 5px;
    border: 1px solid #ccc;
}

form button {
    background: #0077b6;
    color: white;
    cursor: pointer;
    border: none;
}

form button:hover {
    background: #023e8a;
}

#themeToggle {
    padding: 0.6rem 1rem;
    background: #ff7f50;
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
}

#themeToggle:hover {
    background: #ff5a36;
}

footer {
    text-align: center;
    background: #0077b6;
    color: white;
    padding: 0.7rem;
}

/* Dark Mode */
.dark-mode {
    background: #121212;
    color: white;
}

.dark-mode header, .dark-mode footer {
    background: #1e1e1e;
}

.dark-mode nav {
    background: #333;
}

.dark-mode form {
    background: #1e1e1e;
    border: 1px solid #444;
}

js :
window.onload = function () {
    alert("Welcome to the Skills Test!");
    updateStudentCount();
};

// Contact Form Validation
document.getElementById("contactForm").addEventListener("submit", function (event) {
    event.preventDefault();
    let name = document.getElementById("name").value.trim();
    let email = document.getElementById("email").value.trim();
    let message = document.getElementById("message").value.trim();
    let formMessage = document.getElementById("formMessage");

    if (!name || !email || !message) {
        formMessage.style.color = "red";
        formMessage.textContent = "Please fill out all fields.";
    } else {
        formMessage.style.color = "green";
        formMessage.textContent = "Form submitted successfully!";
    }
});

// Theme Toggle
document.getElementById("themeToggle").addEventListener("click", function () {
    document.body.classList.toggle("dark-mode");
});

// Student Counter
function updateStudentCount() {
    let table = document.getElementById("studentTable").getElementsByTagName("tbody")[0];
    let count = table.rows.length;
    document.getElementById("studentCount").textContent = "Total Learners: " + count;
}

// Add Student Form
document.getElementById("addStudentForm").addEventListener("submit", function (event) {
    event.preventDefault();
    let newName = document.getElementById("newName").value.trim();
    let newAge = document.getElementById("newAge").value.trim();
    let newSkill = document.getElementById("newSkill").value.trim();

    if (!newName || !newAge || !newSkill) {
        alert("Please fill in all learner details!");
        return;
    }

    let tableBody = document.getElementById("studentTable").getElementsByTagName("tbody")[0];
    let newRow = tableBody.insertRow();
    newRow.insertCell(0).textContent = newName;
    newRow.insertCell(1).textContent = newAge;
    newRow.insertCell(2).textContent = newSkill;

    updateStudentCount();

    // Clear fields
    document.getElementById("newName").value = "";
    document.getElementById("newAge").value = "";
    document.getElementById("newSkill").value = "";
});
;
