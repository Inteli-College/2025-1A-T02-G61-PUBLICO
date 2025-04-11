# 🕊️ ANGEL – Final Public Report (MVP)

## 🔹 Project Overview

ANGEL is a digital platform for managing donations between donors and certified institutions, developed as a hands-on journey of hypothesis validation during the **Entrepreneurship and Applied Project** course at INTELI – Instituto de Tecnologia e Liderança, under the guidance of **Lisane Valdo**.

The project was born from the discomfort with the lack of trust in the donation ecosystem and was structured through continuous discovery and iterative experimentation. Rather than relying on extensive requirement documents, the development itself became the process of thinking, understanding, and shaping the solution — in other words: **code was the path to clarity**.

---

## 🎯 MVP Purpose

- Create an **auditable and transparent environment** for donations
- Test the concept of escrowed funds with conditional release
- Simulate the full cycle: donor → institution → request → approval → fund usage
- Deliver a functional and intuitive Web2 interface for both actors
- **Validate by building**: uncover real blockers and scale potential through iteration

---

## 💡 Solution

ANGEL acts as a digital intermediary between donors and recipients, guided by the following principles:

- All transactions are recorded immutably on the blockchain (Polygon Amoy), invisible to the user
- Institutions receive funds in tokenized escrows (ERC20) and may only use them upon approval
- Donors can visualize and approve fund usage through a timeline-based interface
- AI, OCR, and additional features were considered in the design but **not implemented in this cycle**
- The MVP targets **certified institutions only**, ensuring trust at launch

---

## 📦 MVP Scope Delivered

- Custom ERC20 token (`DonationToken`)
- Smart contracts for:
  - Donation registration
  - Usage requests and approvals
  - Escrow-based release mechanism
- Go backend (`angel-core`) with Clean Architecture
- Web2 frontend (React) deployed publicly via GitHub Pages
- End-to-end integration from frontend ↔ backend ↔ smart contracts

---

## 📅 Development Timeline (5 Sprints)

### Sprint 1 – Planning and Discovery

- Project planning and hypothesis definition
- Interviews with NGOs and benchmarks
- Architecture sketch and design proposal

### Sprint 2 – Token-Based Donation Core

- ERC20 contract (`DonationToken`) implemented
- First version of `DonationRegistry` and `DonationEscrow` contracts
- Initial deployments on Polygon Amoy
- Backend project setup with modular structure

### Sprint 3 – Web2 Interface and Integration

- Donor dashboard with timeline view
- Institution panel showing balance and donation history
- Frontend deployed on GitHub Pages
- First backend ↔ contract integration using Go bindings

### Sprint 4 – Requests and Approval

- Request submission flow implemented on-chain
- Approval logic wired to event handling
- `donationId` and `requestId` extracted from Solidity events
- Manual tests with real txHash returned to clients

### Sprint 5 – MVP Consolidation

- Full refactor to token-based architecture (ERC20 only)
- ETH logic removed, replaced by `transferFrom`, `mint`, `escrow`
- New tokenized versions of `DonationRegistry` and `Escrow` deployed
- Backend adapted to new contract bindings and workflows
- This final report written and project made public for presentation

---

## ⚙️ Technical Architecture

```plaintext
Frontend (React) ─────> BFF/API (Go)
                          │
                          ▼
         ┌───────────────────────────────────┐
         │           angel-core              │
         │                                   │
         │   ┌───────────────┐               │
         │   │   Registry    │ <──submit─────┤
         │   └───────────────┘               │
         │   ┌───────────────┐               │
         │   │    Escrow     │ <──release────┤
         │   └───────────────┘               │
         │   ┌───────────────┐               │
         │   │   Manager     │ <──donate─────┤
         │   └───────────────┘               │
         │   ┌───────────────┐               │
         │   │  DonationToken│               │
         │   └───────────────┘               │
         └───────────────────────────────────┘
```

---

## 🔑 Technology Stack

| Layer           | Technology                              |
| --------------- | --------------------------------------- |
| Smart Contracts | Solidity + OpenZeppelin + Proxy Pattern |
| Token           | ERC20 (`DonationToken`)                 |
| Backend         | Go + Gin + go-ethereum                  |
| Frontend        | React + Vite                            |
| Blockchain      | Polygon Amoy                            |
| Deployment      | GitHub Pages + Hardhat CLI              |

---

## 📊 Validation and Deliverables

- ✅ Full functional cycle from donation to fund release
- ✅ ID values (`donationId`, `requestId`) returned via Solidity events
- ✅ Go backend using `abigen` for contract bindings
- ✅ Interfaces are modular, scalable and testable
- ✅ MVP architecture ready for AI and future governance integrations

---

## 🔐 What Was Not Included (By Design)

- ❌ AI, OCR, or NER integration
- ❌ Real-time notifications (e-mail, SMS, push)
- ❌ Authentication / user management
- ❌ Governance, voting, or reputation system

These features were planned conceptually and scoped for future implementation.

---

## 🧠 Learnings

Throughout the development of the ANGEL MVP, several critical insights emerged, shaping both the product and the business strategy:

- **Strategic Pivot from B2C to B2B**: Initially, ANGEL was envisioned as a platform enabling individuals to donate to NGOs of their choice. However, during the discovery phase, it became evident that focusing on facilitating corporate donations to certified institutions offered a more viable and scalable path. This shift was influenced by:

  - **Simplified Revenue Model**: Businesses are more inclined to pay for services that directly add value to their operations and corporate social responsibility goals.
  - **Reduced Customer Acquisition Costs**: Targeting a smaller number of corporate clients streamlined marketing and sales efforts.
  - **Institutional Support**: The INTELI environment provided resources and mentorship aligned with B2B initiatives, facilitating strategic partnerships.

- **Agility in Product Development**: The iterative process of developing the MVP underscored the importance of flexibility. Being open to pivoting and making course corrections based on real-world feedback was crucial in navigating the uncertainties.

- **Importance of Validated Learning**: Embracing the principles of the Lean Startup methodology, we prioritized building a Minimum Viable Product (MVP) to test our hypotheses and gather actionable feedback. This approach allowed us to make informed decisions, adapt to user needs, and avoid investing in features that did not resonate with our target market.

- **Development as a Tool for Understanding**: Building the product proved to be the most effective way to comprehend user needs and validate decisions, reinforcing the idea that clarity comes through practice.

- **Abstraction of Technological Complexity**: Implementing blockchain in a manner transparent to the end-user underscored the importance of simplifying complex technologies to enhance user experience.

- **Importance of Clean Architecture**: Adopting Clean Architecture in the backend facilitated scalability and system maintenance, allowing domain logic to evolve independently.

- **Utilization of Solidity Events**: Emitting and decoding events in Solidity proved to be an effective strategy for maintaining the integrity and traceability of on-chain transactions.

These learnings were crucial for the maturation of the project and will serve as a foundation for future iterations and initiatives.

---

## 🔭 Next Steps: Q2 – Validation and Iteration

With the foundational MVP in place, the focus for Q2 will shift towards rigorous validation and iterative improvement. This phase aims to ensure that ANGEL not only functions effectively but also resonates deeply with its intended users. The key initiatives for this phase include:

- **Conducting In-Depth User Interviews**: Engaging with a diverse group of stakeholders, including corporate donors and certified institutions, to gather qualitative insights into their experiences, needs, and expectations.

- **Implementing Feedback Loops**: Establishing structured mechanisms to collect, analyze, and act upon user feedback, ensuring that the platform evolves in alignment with user requirements.

- **Refining the User Experience**: Utilizing insights from user interactions to enhance the platform's usability, accessibility, and overall user satisfaction.

- **Validating Business Hypotheses**: Testing the core assumptions underlying ANGEL's business model to ensure viability and scalability in real-world scenarios.

- **Preparing for Feature Expansion**: Laying the groundwork for the integration of advanced features such as AI-driven document analysis and automated notifications, based on validated user needs.

This upcoming phase is crucial for transitioning from a functional MVP to a user-centric platform that delivers tangible value to its users and stakeholders.

---

## 🤝 Final Remarks

ANGEL is the result of a **discovery-driven development journey**, where code was used as a thinking tool. The MVP served not only as a deliverable, but as a **framework for learning, testing, and evolving the business vision**.

Developed independently by **Moises Cazé**, under the academic guidance of **Lisane Valdo**, ANGEL stands as a solid foundation to scale digital philanthropy with trust and transparency.

> GitHub: [@cazemoises](https://github.com/cazemoises)  
> Email: cazemoises2@gmail.com
