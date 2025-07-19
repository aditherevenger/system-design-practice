# System Design Practice

![GitHub last commit](https://img.shields.io/github/last-commit/aditherevenger/system-design-practice)
![GitHub license](https://img.shields.io/github/license/aditherevenger/system-design-practice)
![GitHub issues](https://img.shields.io/github/issues/aditherevenger/system-design-practice)
![GitHub pull requests](https://img.shields.io/github/issues-pr/aditherevenger/system-design-practice)

---

## **📌 Overview**
This repository is my **personal system design playground** where I practice, explore, and document **Low-Level Design (LLD)** and **High-Level Design (HLD)** concepts.  
The goal is to:
- Enhance my problem-solving skills for system design.
- Write clean, maintainable, and testable code.
- Document design choices with diagrams and trade-offs.
- Practice real-world design scenarios inspired by companies like **Swiggy, Uber, Netflix, etc.**

---

## **📂 Repository Structure**
```bash
system-design-practice/
│
├── LLD/ # Low-Level Design projects
│ ├── README.md # List of all LLD projects
│ ├── project-A/
│ │ ├── README.md # Project-specific details
│ │ ├── src/ # Source code
│ │ ├── tests/ # Unit tests
│ │ └── diagrams/ # UML/Class diagrams
│ └── ...
│
├── HLD/ # High-Level Design projects
│ ├── README.md # List of all HLD projects
│ ├── project-X/
│ │ ├── README.md # Project-specific details
│ │ ├── architecture/ # System/Sequence diagrams
│ │ └── notes.md # Design decisions
│ └── ...
│
├── docs/ # General system design notes & resources
│ ├── best-practices.md
│ └── resources.md
│
├── .github/workflows/ # GitHub Actions (security & tests)
├── LICENSE # MIT License
└── README.md # This file
```


---

## **📘 What’s Inside?**

### **Low-Level Design (LLD)**
- Focused on **class diagrams, OOP principles, and design patterns**.
- Each project includes:
  - UML diagrams (Class, Sequence).
  - Unit tests and clean code.

### **High-Level Design (HLD)**
- Focused on **system architecture and scalability**.
- Includes:
  - Component diagrams.
  - Trade-offs between design choices.
  - System constraints & scaling techniques.

---

## **🚀 Projects**
### **LLD**
- [Project A - Parking Lot Design](./LLD/project-A/README.md) *(example)*
- [Project B - Book My Show Design](./LLD/project-B/README.md)

### **HLD**
- [Project X - Food Delivery System (Swiggy-like)](./HLD/project-X/README.md)
- [Project Y - Distributed Cache (like Redis)](./HLD/project-Y/README.md)

---

## **🧪 Testing**
- Every LLD project includes **unit test cases** under the `tests/` folder.
- To run all tests:
  ```bash
  # Example for Go/Java/Python (modify as per language)
  make test

## 🔒 Security
- Integrated GitHub Security Actions (.github/workflows/security.yml) to perform:
- CodeQL analysis
- Dependency scanning

## 📄 License
This repository is  [LICENSE](LICENSE) under the MIT License.

## 📚 Resources
I’m actively learning from:

- Grokking the System Design Interview
- Low-Level Design blogs and Swiggy ASDE learnings.

## 👤 Author
**Aditya Yadav**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/aditya-yadav-1b36a2163/)
