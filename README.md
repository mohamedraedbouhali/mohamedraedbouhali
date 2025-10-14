<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Raed Bouhali | Data Science & DevOps Engineer</title>
    <!-- Load Inter font for professional look -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap" rel="stylesheet">
    <style>
        /* Base styles and Inter Font */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f4f7f9;
            color: #333;
            margin: 0;
            padding: 20px;
            line-height: 1.6;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background-color: #ffffff;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
        }

        /* Profile Header */
        .profile-header {
            text-align: center;
            margin-bottom: 20px;
        }

        .profile-header h1 {
            font-size: 2.8em;
            font-weight: 800;
            color: #0077B6;
            margin-bottom: 5px;
        }

        .profile-header h2 {
            font-size: 1.2em;
            color: #48CAE4;
            margin-top: 0;
            font-weight: 500;
        }

        /* Gradient Banner Section */
        .gradient-banner {
            padding: 30px 20px;
            background: linear-gradient(135deg, #0077B6 0%, #48CAE4 100%);
            color: white;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            text-align: center;
        }

        .gradient-banner h1 {
            margin: 0;
            font-size: 2.8em;
            font-weight: 900;
            letter-spacing: 2px;
        }

        .gradient-banner p {
            margin: 5px 0 0;
            font-size: 1.1em;
            font-weight: 300;
        }

        /* Bio/Summary Section */
        .bio p {
            margin-bottom: 15px;
            font-size: 1.05em;
        }

        .bio strong {
            color: #0077B6;
        }

        /* Separator */
        hr {
            border: 0;
            height: 1px;
            background-image: linear-gradient(to right, rgba(0, 0, 0, 0), #0077B6, rgba(0, 0, 0, 0));
            margin: 40px 0;
        }

        /* Technologies Section */
        .tech-section h2 {
            font-size: 1.8em;
            color: #333;
            margin-bottom: 25px;
            border-left: 5px solid #0077B6;
            padding-left: 10px;
        }

        .tech-group {
            border: 1px solid #e0e0e0;
            border-radius: 10px;
            margin-bottom: 20px;
            padding: 15px;
            background-color: #fafafa;
            transition: transform 0.2s;
        }

        .tech-group:hover {
            transform: translateY(-3px);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
        }

        .tech-group-header {
            font-weight: 700;
            font-size: 1.2em;
            margin-bottom: 10px;
            padding-bottom: 5px;
            border-bottom: 2px solid;
        }

        .languages .tech-group-header { border-color: #007396; color: #007396; }
        .devops .tech-group-header { border-color: #EE0000; color: #EE0000; }
        .web .tech-group-header { border-color: #E34F26; color: #E34F26; }
        
        .tech-group img {
            margin: 5px 5px 0 0;
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .project-card {
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            transition: box-shadow 0.3s, transform 0.3s;
            background-color: #ffffff;
            border-top: 5px solid #0077B6;
        }

        .project-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }

        .project-card h3 {
            margin-top: 0;
            font-size: 1.4em;
            color: #0077B6;
            border-bottom: 1px dashed #e0e0e0;
            padding-bottom: 10px;
        }
        
        /* Contact Alert */
        .contact-alert {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            background-color: #fff8e1; /* Light Amber/Yellow */
            color: #e65100; /* Darker Orange */
            border-radius: 10px;
            border: 2px solid #e65100;
            font-size: 1.1em;
            font-weight: 600;
        }

        .contact-alert a {
            color: #007396;
            text-decoration: none;
            font-weight: 700;
            transition: color 0.2s;
        }

        .contact-alert a:hover {
            color: #005f7d;
        }

        /* Mobile Adjustments */
        @media (max-width: 600px) {
            body {
                padding: 10px;
            }
            .container {
                padding: 15px;
            }
            .gradient-banner h1 {
                font-size: 2em;
            }
            .profile-header h1 {
                font-size: 2em;
            }
            .tech-section h2 {
                font-size: 1.5em;
            }
        }
    </style>
</head>
<body>
    <div class="container">

        <!-- Profile Title -->
        <div class="profile-header">
            <h1>RAED BOUHALI</h1>
            <h2>Data Science & AI Engineer | DevOps & Linux Expert 🚀</h2>
        </div>

        <!-- Gradient Banner -->
        <div class="gradient-banner">
            <!-- Used placeholder image text for the banner, as the original image was named "unnamed.png" -->
            <h1 style="font-family: 'Inter', sans-serif;">HELLO WORLD, I'M RAED</h1>
            <p>Leveraging Technology for Innovative Solutions ✨</p>
        </div>

        <!-- Bio / Summary -->
        <div class="bio">
            <p>
                I am an aspiring <strong>Data Science and Artificial Intelligence Engineer</strong> 💻, currently an Engineering student 🎓 at <strong>TEK-UP University</strong>. My expertise spans across AI/ML and robust infrastructure, holding a <strong>Red Hat Certified System Administrator (RHCSA)</strong> certification ✅ with a strong foundation in <strong>DevOps and Linux</strong> 🐧.
            </p>
            <p>
                I have gained valuable hands-on experience through internships 💼 at <strong>VMD</strong>, <strong>Progress Engineering</strong>, and <strong>ALL Circuits</strong>, where I applied my skills in problem-solving and technical implementation. I am proficient in core languages including <strong>Python</strong>, <strong>SQL</strong>, and <strong>Java</strong>, with a strong passion for <strong>AI, machine learning, and entrepreneurship</strong> as drivers for innovative solutions.
            </p>
        </div>

        <hr>

        <!-- Technical Mastery -->
        <div class="tech-section">
            <h2>Technical Mastery 🛠️</h2>

            <div class="tech-group languages">
                <p class="tech-group-header">Languages & Core Technologies:</p>
                <p>
                    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
                    <img src="https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=java&logoColor=white" alt="Java">
                    <img src="https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white" alt="C">
                    <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
                    <img src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="PHP">
                    <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
                </p>
            </div>

            <div class="tech-group devops">
                <p class="tech-group-header">DevOps & Infrastructure:</p>
                <p>
                    <img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux">
                    <img src="https://img.shields.io/badge/Red%20Hat-EE0000?style=for-the-badge&logo=redhat&logoColor=white" alt="Red Hat">
                    <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker">
                    <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Kubernetes">
                    <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git">
                    <img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white" alt="AWS">
                    <img src="https://img.shields.io/badge/Microsoft%20Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white" alt="Azure">
                </p>
            </div>

            <div class="tech-group web">
                <p class="tech-group-header">Web & Backend Frameworks:</p>
                <p>
                    <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5">
                    <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3">
                    <img src="https://img.shields.io/badge/Symfony-000000?style=for-the-badge&logo=symfony&logoColor=white" alt="Symfony">
                    <img src="https://img.shields.io/badge/XAMPP-FB7A24?style=for-the-badge&logo=xampp&logoColor=white" alt="XAMPP">
                </p>
            </div>
        </div>

        <hr>

        <!-- Featured Projects -->
        <div class="projects-section">
            <h2>Featured Projects 💡</h2>
            <div class="projects-grid">
                
                <div class="project-card" style="border-color: #0077B6;">
                    <h3>⛱️🛬 TUNISCO: Tourism Platform</h3>
                    <p>A comprehensive tourism platform for exploring establishments and destinations across Tunisia.</p>
                </div>

                <div class="project-card" style="border-color: #48CAE4;">
                    <h3>🧙‍♂️🏰 Wizard World: Multimedia Hub</h3>
                    <p>A multimedia platform for films, books, and games, complete with robust user authentication features.</p>
                </div>

                <div class="project-card" style="border-color: #3776AB;">
                    <h3>🤖✨ Mars Chatbot: Conversational AI</h3>
                    <p>An intelligent conversational AI system built with natural language processing (NLP) capabilities.</p>
                </div>

                <div class="project-card" style="border-color: #F05032;">
                    <h3>💀😵 Hangman Game: Single-Player</h3>
                    <p>A classic word-guessing game for a single player, featuring integrated score tracking functionality.</p>
                </div>
            </div>
        </div>

        <!-- Contact Alert -->
        <div class="contact-alert">
            🚨🚨🚨 All my projects are in private mode. For access or to check them out, please contact me at: <a href="mailto:raedbouhali@gmail.com">raedbouhali@gmail.com</a> 🚨🚨🚨
        </div>

    </div>
</body>
</html>
