## Hi there 👋

<!--
**Darlin7701/Darlin7701** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
```jsx
import { useState, useEffect } from "react";

export default function App() {
  const [activeSection, setActiveSection] = useState("home");
  const [isMenuOpen, setIsMenuOpen] = useState(false);

  // Handle scroll to detect active section
  useEffect(() => {
    const handleScroll = () => {
      const sections = ["home", "about", "education", "projects", "contact"];
      const scrollPosition = window.scrollY + 100;

      for (const section of sections) {
        const element = document.getElementById(section);
        if (
          element.offsetTop <= scrollPosition &&
          element.offsetTop + element.offsetHeight > scrollPosition
        ) {
          setActiveSection(section);
          break;
        }
      }
    };

    window.addEventListener("scroll", handleScroll);
    return () => window.removeEventListener("scroll", handleScroll);
  }, []);

  // Navigation links
  const navLinks = [
    { id: "home", label: "Home" },
    { id: "about", label: "About Me" },
    { id: "education", label: "Education" },
    { id: "projects", label: "Projects" },
    { id: "contact", label: "Contact" },
  ];

  // Project data
  const projects = [
    {
      title: "Portfolio Website",
      description:
        "A personal portfolio built with React and TailwindCSS showcasing my work and skills.",
      tags: ["React", "TailwindCSS", "JavaScript"],
      image: "https://placehold.co/600x400?text=Portfolio+Website",
    },
    {
      title: "E-Commerce Platform",
      description:
        "Full-stack e-commerce platform with user authentication, cart system, and payment integration.",
      tags: ["Node.js", "MongoDB", "Express", "React"],
      image: "https://placehold.co/600x400?text=E-Commerce+Platform",
    },
    {
      title: "Task Management App",
      description:
        "A productivity app that allows users to manage tasks, set deadlines, and track progress.",
      tags: ["React Native", "Firebase", "Redux"],
      image: "https://placehold.co/600x400?text=Task+Management+App",
    },
    {
      title: "Weather Forecast App",
      description:
        "Real-time weather app using OpenWeatherMap API with location-based forecasts.",
      tags: ["HTML", "CSS", "JavaScript", "API"],
      image: "https://placehold.co/600x400?text=Weather+Forecast+App",
    },
  ];

  return (
    <div className="bg-gray-50 text-gray-900">
      {/* Header / Navigation */}
      <header className="fixed top-0 left-0 w-full bg-white shadow-md z-50">
        <nav className="container mx-auto px-6 py-4 flex justify-between items-center">
          <a href="#home" className="text-2xl font-bold text-indigo-600">
            Jane Doe
          </a>
          <div className="hidden md:flex space-x-8">
            {navLinks.map((link) => (
              <a
                key={link.id}
                href={`#${link.id}`}
                onClick={() => setActiveSection(link.id)}
                className={`capitalize transition duration-300 hover:text-indigo-600 ${
                  activeSection === link.id ? "text-indigo-600 font-semibold" : ""
                }`}
              >
                {link.label}
              </a>
            ))}
          </div>
          <button
            className="md:hidden focus:outline-none"
            onClick={() => setIsMenuOpen(!isMenuOpen)}
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              strokeWidth="2"
              strokeLinecap="round"
              strokeLinejoin="round"
            >
              <line x1="3" y1="12" x2="21" y2="12"></line>
              <line x1="3" y1="6" x2="21" y2="6"></line>
              <line x1="3" y1="18" x2="21" y2="18"></line>
            </svg>
          </button>
        </nav>

        {/* Mobile Menu */}
        {isMenuOpen && (
          <div className="md:hidden bg-white border-t border-gray-200">
            <div className="flex flex-col p-4 space-y-4">
              {navLinks.map((link) => (
                <a
                  key={link.id}
                  href={`#${link.id}`}
                  onClick={() => {
                    setActiveSection(link.id);
                    setIsMenuOpen(false);
                  }}
                  className={`capitalize py-2 transition duration-300 hover:text-indigo-600 ${
                    activeSection === link.id ? "text-indigo-600 font-semibold" : ""
                  }`}
                >
                  {link.label}
                </a>
              ))}
            </div>
          </div>
        )}
      </header>

      {/* Hero Section */}
      <section
        id="home"
        className="min-h-screen pt-24 flex items-center bg-gradient-to-r from-indigo-50 to-blue-50"
      >
        <div className="container mx-auto px-6 py-12 flex flex-col-reverse md:flex-row items-center">
          <div className="md:w-1/2 mb-10 md:mb-0">
            <h1 className="text-4xl md:text-5xl lg:text-6xl font-extrabold text-gray-900 leading-tight">
              Hi, I'm Jane Doe
            </h1>
            <p className="mt-4 text-lg md:text-xl text-gray-700">
              A passionate software engineer specializing in full-stack web development.
            </p>
            <div className="mt-6 flex space-x-4">
              <a
                href="#projects"
                className="px-6 py-3 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 transition duration-300"
              >
                View My Work
              </a>
              <a
                href="#contact"
                className="px-6 py-3 border border-indigo-600 text-indigo-600 rounded-md hover:bg-indigo-50 transition duration-300"
              >
                Contact Me
              </a>
            </div>
          </div>
          <div className="md:w-1/2 flex justify-center">
            <img
              src="https://placehold.co/400x400?text=Jane+Doe"
              alt="Profile"
              className="rounded-full w-64 h-64 object-cover shadow-lg"
            />
          </div>
        </div>
      </section>

      {/* About Section */}
      <section id="about" className="py-20 bg-white">
        <div className="container mx-auto px-6">
          <h2 className="text-3xl md:text-4xl font-bold text-center mb-12">About Me</h2>
          <div className="max-w-3xl mx-auto">
            <p className="text-lg text-gray-700 leading-relaxed mb-6">
              I'm a dedicated software engineer with over 5 years of experience building scalable,
              user-friendly applications. My passion lies in creating elegant solutions to complex
              problems through clean code and intuitive design.
            </p>
            <p className="text-lg text-gray-700 leading-relaxed mb-6">
              With expertise in both frontend and backend technologies, I thrive in collaborative
              environments where innovation is encouraged and challenges are embraced. I'm always
              eager to learn new technologies and improve my craft.
            </p>
            <div className="grid grid-cols-2 gap-6 mt-8">
              <div>
                <h3 className="font-semibold text-gray-900 mb-2">Email</h3>
                <p className="text-gray-700">janedoe@example.com</p>
              </div>
              <div>
                <h3 className="font-semibold text-gray-900 mb-2">Location</h3>
                <p className="text-gray-700">San Francisco, CA</p>
              </div>
              <div>
                <h3 className="font-semibold text-gray-900 mb-2">Experience</h3>
                <p className="text-gray-700">5+ Years</p>
              </div>
              <div>
                <h3 className="font-semibold text-gray-900 mb-2">Freelance</h3>
                <p className="text-gray-700">Available</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Education Section */}
      <section id="education" className="py-20 bg-gray-50">
        <div className="container mx-auto px-6">
          <h2 className="text-3xl md:text-4xl font-bold text-center mb-12">Education Background</h2>
          <div className="max-w-3xl mx-auto">
            <div className="bg-white p-6 rounded-lg shadow-sm mb-6">
              <h3 className="text-xl font-bold text-indigo-600">Bachelor of Science in Computer Science</h3>
              <p className="text-gray-600">University of California, Berkeley</p>
              <p className="text-gray-500 text-sm">Graduated: May 2019</p>
              <ul className="mt-4 list-disc pl-5 space-y-1 text-gray-700">
                <li>GPA: 3.8/4.0</li>
                <li>Relevant Coursework: Data Structures & Algorithms, Web Development, Machine Learning</li>
                <li>Honors: Dean's List (2016-2019)</li>
              </ul>
            </div>
            <div className="bg-white p-6 rounded-lg shadow-sm">
              <h3 className="text-xl font-bold text-indigo-600">Full Stack Developer Bootcamp</h3>
              <p className="text-gray-600">General Assembly</p>
              <p className="text-gray-500 text-sm">Completed: December 2019</p>
              <ul className="mt-4 list-disc pl-5 space-y-1 text-gray-700">
                <li>Hands-on training in modern web development stacks</li>
                <li>Capstone project: E-commerce platform using MERN stack</li>
              </ul>
            </div>
          </div>
        </div>
      </section>

      {/* Projects Section */}
      <section id="projects" className="py-20 bg-white">
        <div className="container mx-auto px-6">
          <h2 className="text-3xl md:text-4xl font-bold text-center mb-12">My Projects</h2>
          <div className="grid grid-cols-1 md:grid-cols-2 gap-10">
            {projects.map((project, index) => (
              <div
                key={index}
                className="bg-white rounded-lg overflow-hidden shadow-lg transform transition duration-300 hover:-translate-y-2 hover:shadow-xl"
              >
                <img
                  src={project.image}
                  alt={project.title}
                  className="w-full h-48 object-cover"
                />
                <div className="p-6">
                  <h3 className="text-xl font-bold text-gray-900 mb-2">{project.title}</h3>
                  <p className="text-gray-600 mb-4">{project.description}</p>
                  <div className="flex flex-wrap gap-2">
                    {project.tags.map((tag, tagIndex) => (
                      <span
                        key={tagIndex}
                        className="text-xs px-3 py-1 bg-indigo-100 text-indigo-800 rounded-full"
                      >
                        {tag}
                      </span>
                    ))}
                  </div>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section id="contact" className="py-20 bg-gray-50">
        <div className="container mx-auto px-6">
          <h2 className="text-3xl md:text-4xl font-bold text-center mb-12">Get In Touch</h2>
          <div className="max-w-3xl mx-auto">
            <form className="bg-white p-8 rounded-lg shadow-md">
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
                <div>
                  <label htmlFor="name" className="block text-gray-700 font-medium mb-2">
                    Name
                  </label>
                  <input
                    type="text"
                    id="name"
                    className="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500"
                    placeholder="Your name"
                  />
                </div>
                <div>
                  <label htmlFor="email" className="block text-gray-700 font-medium mb-2">
                    Email
                  </label>
                  <input
                    type="email"
                    id="email"
                    className="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500"
                    placeholder="your@email.com"
                  />
                </div>
              </div>
              <div className="mb-6">
                <label htmlFor="subject" className="block text-gray-700 font-medium mb-2">
                  Subject
                </label>
                <input
                  type="text"
                  id="subject"
                  className="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500"
                  placeholder="What's this about?"
                />
              </div>
              <div className="mb-6">
                <label htmlFor="message" className="block text-gray-700 font-medium mb-2">
                  Message
                </label>
                <textarea
                  id="message"
                  rows="5"
                  className="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500"
                  placeholder="Let me know how I can help..."
                ></textarea>
              </div>
              <button
                type="submit"
                className="w-full px-6 py-3 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 transition duration-300"
              >
                Send Message
              </button>
            </form>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-white border-t border-gray-200 py-8">
        <div className="container mx-auto px-6 text-center text-gray-600">
          <p>&copy; {new Date().getFullYear()} Jane Doe. All rights reserved.</p>
        </div>
      </footer>
    </div>
  );
}
```