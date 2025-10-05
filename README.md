import React, { useEffect, useRef, useState } from "react";                 
                        
const skills = {                                            
  technical: [        
    { name: "Java", icon: "☕" },                
    { name: "Python", icon: "🐍" },                   
    { name: "JavaScript", icon: "🟨" },                    
    { name: "TypeScript", icon: "🔷" },                
    { name: "React.js", icon: "⚛️" },           
    { name: "HTML5", icon: "📄" },               
    { name: "CSS3", icon: "🎨" },              
    { name: "Bootstrap", icon: "🅱️" },          
    { name: "Django", icon: "🌿" },                   
    { name: "Node.js", icon: "🟩" },             
    { name: "Express.js", icon: "🚂" },                
    { name: "SQL", icon: "🗄️" },                  
    { name: "MySQL", icon: "🐬" },  
    { name: "MongoDB", icon: "🍃" },             
    { name: "Git", icon: "🔧" },                
    { name: "GitHub", icon: "🐙" },               
    { name: "Postman", icon: "📬" },             
    { name: "VS Code", icon: "🖥️" },              
    { name: "AWS (basics)", icon: "☁️" },                 
    { name: "Docker (basics)", icon: "🐳" },                      
  ],                   
  soft: [             
    "Problem Solving", 
    "Communication",          
    "Adaptability",               
    "Team Leadership",                    
  ],             
};                      
                        
const projects = [                    
  {              
    title: "Smart Health Monitoring System 🩺",                 
    description:                
      "Django-based app for real-time health & mental health monitoring with dashboards and SQL database.",                    
    github: "https://github.com/ayaantyagi/Smart-Health-Monitoring-System-",                        
  },               
  {                
    title: "Multi-language Online Bookstore Management System 📚",              
    description:                           
      "Full-stack system built with Java (backend), SQL (database), and Python (data handling). Features: inventory management, user login, payment gateway integration, multilingual support for a global user base.",             
    github:                   
      "https://github.com/ayaantyagi/Multi-language-Online-Bookstore-Management-System-",            
  },              
  {                     
    title: "Mental Health App 💙",           
    description:              
      "A web application focused on promoting mental health awareness and providing resources. Developed with Django (backend), Python, and SQL. Includes user authentication, interactive features, and support tools.",         
    github: "https://github.com/ayaantyagi/mental-health-app",             
  },             
];                      
                       
const socialLinks = {                              
  linkedin: "https://linkedin.com/in/ayaantyagi",                     
  github: "https://github.com/ayaantyagi",                     
  email: "mailto:ayan.tyagi2211@gmail.com",                       
};                          
                                  
// Hook for fade-in on scroll                   
function useFadeInOnScroll() {                             
  const ref = useRef();                            
  const [visible, setVisible] = useState(false);                  
                    
  useEffect(() => {                     
    const observer = new IntersectionObserver(              
      ([entry]) => {                     
        if (entry.isIntersecting) {                       
          setVisible(true);                        
          observer.unobserve(ref.current);                  
        }                   
      },                    
      { threshold: 0.2 }                     
    );                                                
    if (ref.current) observer.observe(ref.current);             
    return () => observer.disconnect();                 
  }, []);               
                            
  return [ref, visible];                
}                
                     
const App = () => {                   
  const scrollToSection = (id) => {               
    const el = document.getElementById(id);                  
    if (el) el.scrollIntoView({ behavior: "smooth" });              
  };                   
                                                           
  const [aboutRef, aboutVisible] = useFadeInOnScroll();           
  const [skillsRef, skillsVisible] = useFadeInOnScroll();             
  const [projectsRef, projectsVisible] = useFadeInOnScroll();                
  const [experienceRef, experienceVisible] = useFadeInOnScroll();            
  const [educationRef, educationVisible] = useFadeInOnScroll();                
  const [contactRef, contactVisible] = useFadeInOnScroll();                
                             
  return (                      
    <>               
      <style>{`                                                                                                      
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;600;800&display=swap');                                            
        * { box-sizing: border-box; }                                          
        body {                                    
          margin: 0;                                                 
          font-family: 'Poppins', sans-serif;                                                
          background: #0f0f23;                                                 
          color: #e0e0e0;                                   
          scroll-behavior: smooth;                                             
        }                                                                     
        a { color: #00fff7; text-decoration: none; }                                           
        a:hover, a:focus { text-decoration: underline; outline: none; }                                   
        button {                                                
          cursor: pointer;                                 
          border: none;                                   
          border-radius: 40px;                                         
          padding: 14px 36px;                                                   
          font-weight: 600;                  
          font-size: 1.1rem;                           
          color: #0f0f23;                                           
          background: linear-gradient(90deg, #00fff7, #00b894);                         
          box-shadow: 0 0 15px #00fff7cc;               
          transition: all 0.3s ease;                            
          user-select: none;                      
        }                                
        button:hover, button:focus {                 
          box-shadow: 0 0 25px #00fff7ff;                  
          transform: scale(1.05);                 
          outline: none;                   
        }                    
        h1, h2, h3 {                     
          margin: 0 0 12px 0;                                 
          font-weight: 800;                            
          letter-spacing: 0.1em;                        
        }                                      
        h1 {                   
          font-size: 4rem;                   
          color: white;                
          text-shadow: 0 0 20px #00fff7cc;           
        }              
        h2 {                      
          font-size: 2.8rem;                        
          color: #8f94fb;                       
          text-shadow: 0 0 10px #4e54c8cc;                      
          text-align: center;                    
          margin-bottom: 60px;                       
        }                       
        h3 {                         
          font-size: 1.6rem;                     
          color: #00fff7;                       
          text-shadow: 0 0 8px #00fff7cc;                     
        }                   
        p {                         
          font-weight: 300;                 
          font-size: 1.1rem;                  
          line-height: 1.6;                  
          color: #c0d6e4cc;                   
        }                    
        nav {                    
          position: fixed;               
          top: 0;                 
          width: 100%;                            
          background: rgba(15, 15, 35, 0.85);            
          backdrop-filter: saturate(180%) blur(20px);             
          box-shadow: 0 2px 10px #00fff7aa;          
          z-index: 1000;         
          display: flex;           
          justify-content: center;                  
          padding: 12px 0;                
        }                 
        nav ul {                    
          list-style: none;                  
          display: flex;                
          gap: 40px;                
          margin: 0;            
          padding: 0;          
        }                  
        nav li {                   
          font-weight: 600;              
          font-size: 1rem;                   
          color: #00fff7;                       
          cursor: pointer;                   
          transition: color 0.3s ease;                    
        }                                
        nav li:hover, nav li:focus {                  
          color: #00b894;                        
          outline: none;                           
        }                       
        #hero {                     
          height: 100vh;                                             
          background: linear-gradient(135deg, #4e54c8, #8f94fb);                
          display: flex;             
          flex-direction: column;              
          justify-content: center;                
          align-items: center;                    
          text-align: center;                  
          padding: 0 20px;                   
          color: white;                  
          position: relative;                 
          overflow: hidden;                     
        }                      
        #hero p {                    
          font-weight: 600;             
          font-size: 1.5rem;             
          margin-bottom: 40px;                  
          letter-spacing: 0.1em;                   
          color: #d0e8f2cc;                       
          text-shadow: 0 0 10px #00fff7aa;                
        }                
        .btn-group {               
          display: flex;          
          gap: 20px;                  
          flex-wrap: wrap;                 
          justify-content: center;               
        }                   
        .btn-link {                                                 
          background: linear-gradient(90deg, #00fff7, #00b894);                 
          border-radius: 40px;             
          padding: 14px 36px;             
          font-weight: 600;            
          font-size: 1.1rem;             
          color: #0f0f23;                      
          box-shadow: 0 0 15px #00fff7cc;           
          transition: all 0.3s ease;             
          user-select: none;           
          display: inline-flex;             
          align-items: center;            
          justify-content: center;         
          text-decoration: none;              
        }                                       
        .btn-link:hover, .btn-link:focus {           
          box-shadow: 0 0 25px #00fff7ff;           
          transform: scale(1.05);            
          outline: none;            
          color: #0f0f23;             
        }             
        section {              
          max-width: 1100px;           
          margin: 0 auto;              
          padding: 80px 20px;          
          opacity: 0;                    
          transform: translateY(40px);                          
          transition: opacity 0.8s ease, transform 0.8s ease;           
        }                       
        section.visible {             
          opacity: 1;                  
          transform: translateY(0);             
        }                       
        #about {                        
          display: flex;                 
          flex-wrap: wrap;                  
          justify-content: center;             
          align-items: center;            
          gap: 40px;                 
        }              
        #about img {               
          width: 100%;           
          max-width: 320px;            
          border-radius: 20px;            
          box-shadow: 0 8px 30px #00fff7aa;                     
          object-fit: cover;                            
          filter: drop-shadow(0 0 10px #00fff7cc);                  
          transition: transform 0.3s ease;                  
          cursor: default;              
        }                                          
        #about img:hover, #about img:focus {           
          transform: scale(1.05);            
          outline: none;             
        }                      
        #about div.text {              
          flex: 2 1 400px;              
          max-width: 600px;               
        }               
        .skills-category {           
          margin-bottom: 40px;           
        }                       
        .skills-list {           
          display: flex;           
          flex-wrap: wrap;                    
          gap: 16px;                   
          justify-content: center;                       
        }                       
        .skill-item {                               
          background: rgba(30, 30, 60, 0.7);               
          padding: 10px 20px;          
          border-radius: 40px;       
          font-weight: 600;        
          font-size: 1rem;        
          color: #00fff7;                     
          box-shadow: 0 0 12px #00fff7aa;           
          display: flex;          
          align-items: center;           
          gap: 8px;            
          user-select: none;                         
          transition: background-color 0.3s ease;           
        }                                          
        .skill-item:hover, .skill-item:focus {        
          background-color: #00b894;           
          box-shadow: 0 0 20px #00fff7ff;          
          outline: none;               
          cursor: default;           
        }                  
        .projects-grid {        
          display: grid;                                                    
          grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));        
          gap: 40px;          
        }                   
        .project-card {                       
          background: rgba(30, 30, 60, 0.7);            
          border-radius: 20px;            
          padding: 30px 24px;                   
          box-shadow: 0 8px 30px #00fff7aa;                            
          transition: transform 0.3s ease, box-shadow 0.3s ease;             
          display: flex;             
          flex-direction: column;                
          justify-content: space-between;              
          cursor: default;                
        }                                               
        .project-card:hover, .project-card:focus {               
          transform: translateY(-15px);           
          box-shadow: 0 15px 40px #00fff7ff;    
          background: rgba(30, 30, 60, 0.85);           
          outline: none;           
        }                    
        .project-card h3 {              
          margin-bottom: 16px;           
        }                      
        .project-card p {           
          flex-grow: 1;                
          margin-bottom: 24px;          
        }                    
        .github-link {                 
          align-self: flex-start;                  
          background: #00b894;           
          color: #0f0f23;                 
          font-weight: 600;          
          padding: 10px 22px;             
          border-radius: 40px;                   
          box-shadow: 0 0 12px #00b894cc;            
          text-decoration: none;                                             
          transition: background-color 0.3s ease, box-shadow 0.3s ease;            
        }                                           
        .github-link:hover, .github-link:focus {        
          background: #00fff7;             
          box-shadow: 0 0 20px #00fff7ff;         
          color: #0f0f23;             
          outline: none;              
        }                   
        .exp-edu-list {           
          max-width: 700px;           
          margin: 0 auto;           
          font-size: 1.1rem;         
          color: #c0d6e4cc;         
          line-height: 1.6;      
          list-style: none;          
          padding-left: 0;            
        }                       
        .exp-edu-list li {           
          margin-bottom: 12px;          
        }                           
        .exp-edu-list strong {           
          color: #00fff7;            
        }                
        #contact p {              
          font-size: 1.2rem;          
          margin-bottom: 12px;         
          color: #c0d6e4cc;           
          text-align: center;                
        }                  
        #contact a {            
          color: #00fff7;            
          font-weight: 600;           
        }                                        
        #contact a:hover, #contact a:focus {             
          color: #00b894;                
          outline: none;          
        }              
        .social-links {
          display: flex;
          justify-content: center;
          gap: 40px;
          margin-top: 30px;
        }
        .social-links a {
          font-size: 2.4rem;
          color: #00fff7;
          transition: color 0.3s ease;
        }
        .social-links a:hover, .social-links a:focus {
          color: #00b894;
          outline: none;
        }
        footer {
          background: #0f0f23;
          text-align: center;
          padding: 20px 10px;
          color: #555;
          font-size: 0.9rem;
          box-shadow: inset 0 1px 5px #00b89444;
          margin-top: 60px;
        }
        footer .social-icons a {
          margin: 0 10px;
          font-size: 1.5rem;
          color: #00fff7;
          transition: color 0.3s ease;
        }
        footer .social-icons a:hover, footer .social-icons a:focus {
          color: #00b894;
          outline: none;
        }
        @media (max-width: 768px) {
          nav ul {
            gap: 20px;
          }
          #hero h1 {
            font-size: 2.8rem;
          }
          #hero p {
            font-size: 1.2rem;
          }
          button, .btn-link {
            padding: 12px 28px;
            font-size: 1rem;
          }
          section {
            padding: 60px 15px;
          }
          .projects-grid {
            grid-template-columns: 1fr;
            gap: 30px;
          }
          #about {
            flex-direction: column;
          }
          #about div.text {
            max-width: 100%;
          }
          #about img {
            max-width: 280px;
          }
        }
      `}</style>    
 
      <nav aria-label="Primary Navigation"> 
        <ul>
          <li tabIndex="0" onClick={() => scrollToSection("hero")}>Home</li>
          <li tabIndex="0" onClick={() => scrollToSection("about")}>About</li>
          <li tabIndex="0" onClick={() => scrollToSection("skills")}>Skills</li>
          <li tabIndex="0" onClick={() => scrollToSection("projects")}>Projects</li>
          <li tabIndex="0" onClick={() => scrollToSection("experience")}>Experience</li>
          <li tabIndex="0" onClick={() => scrollToSection("education")}>Education</li>
          <li tabIndex="0" onClick={() => scrollToSection("contact")}>Contact</li>
        </ul>
      </nav>

      <section id="hero" aria-label="Hero Section">
        <h1>Hi, I'm Ayan Tyagi</h1>
        <p>Full Stack Developer | Problem Solver | Innovator</p>
        <div className="btn-group" role="group" aria-label="Hero action buttons">
          <button onClick={() => scrollToSection("projects")}>View My Work</button>
          <a
            href="/Ayan_Tyagi_Resume.pdf"
            download="Ayan_Tyagi_Resume.pdf"
            className="btn-link"
            aria-label="Download Resume"
          >
            Download Resume
          </a>
          <button onClick={() => scrollToSection("contact")}>Get In Touch</button>
        </div>
      </section>

      <section
        id="about"
        aria-label="About Me Section"
        ref={aboutRef}
        className={aboutVisible ? "visible" : ""}
      >
        <img
          src="https://i.postimg.cc/MT3x0qXJ/ayan-photo.jpg"
          alt="Ayan Tyagi"
          tabIndex="0"
        />
        <div className="text">
          <h2>About Me</h2>
          <p>
            I am a Computer Science graduate from SRM Institute of Science and Technology, Delhi-NCR Campus.
            Passionate about full-stack development, I create modern and impactful web solutions using Java, Python, React, Django, and SQL.
            Apart from coding, I’m a basketball 🏀 & badminton 🏸 enthusiast, bringing teamwork, discipline, and persistence into my professional journey.
            I’m currently seeking opportunities as a Software Developer / Full Stack Developer.
          </p>
        </div>
      </section>

      
