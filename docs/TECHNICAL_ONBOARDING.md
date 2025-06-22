# Technical Onboarding Guide: Namma Yatri Project

## 1. Project Overview
Namma Yatri is like the “Linux of mobility platforms”—open, community-driven, and built for scale. Imagine a city’s public transport system, but open for anyone to improve, audit, or extend. Our backend is a Haskell monorepo (think of it as a central train station with many lines), and our frontend is a suite of apps (like ticket counters for web and mobile users). All code, infrastructure, and documentation live in this single repository, making collaboration seamless.

## 2. Repository Structure
- **Backend/**: The engine room—Haskell backend services, libraries, and utilities. Like the machinery and control systems running a metro network.
- **Frontend/**: The passenger interface—web and mobile code. Think of this as the ticketing kiosks and mobile apps commuters use.
- **docs/**: The operations manual—project documentation, guides, and diagrams.
- **test/**: The safety checks—test suites and related code to ensure everything runs smoothly.

## 3. Prerequisites
- **Git**: Your version control passport—lets you board, collaborate, and contribute.
- **Nix package manager**: Like a universal toolkit—ensures everyone has the same tools, no matter their OS.
- **direnv**: The automatic gatekeeper—loads the right environment as you enter the project directory.
- **(Optional) cabal**: The Haskell project manager—like a conductor for building and running backend services.

## 4. Environment Setup
1. **Clone the repository:**
   _Analogy: Like getting a copy of the city’s blueprint before you start building._
   ```sh
   git clone <repo-url>
   cd namm...yatri-ash
   ```
2. **Install Nix:**
   _Analogy: Equipping your workstation with the exact tools used by the rest of the team._
   ```sh
   sh <(curl -L https://nixos.org/nix/install) --no-daemon
   . ~/.nix-profile/etc/profile.d/nix.sh
   ```
3. **Install direnv:**
   _Analogy: Setting up an automatic badge scanner at the office entrance—loads your tools as you walk in._
   ```sh
   nix-env -iA nixpkgs.direnv
   ```
4. **Link and allow backend environment:**
   _Analogy: Tuning your workstation to the backend’s frequency—ensures you’re in sync with the backend team._
   ```sh
   ln -sf .envrc.backend .envrc
   direnv allow
   ```
   This loads the Nix shell with all dependencies, like stepping into a ready-made workshop.

## 5. Building and Running Backend
- _Analogy: Like assembling and starting the engines in the train yard._
- Enter the Nix shell (should happen automatically with direnv):
  ```sh
  cd /workspaces/nammayatri-ash
  ```
- Build all backend packages:
  ```sh
  cd Backend
  cabal build all
  ```
  _Example: If you change a ticket validation rule, rebuild to see your update in action._
- Run a backend service (example):
  ```sh
  cabal run lib/location-updates
  ```
  _Example: This could be like running the location tracking system for all city buses._

## 6. Frontend Setup
- _Analogy: Setting up the ticket counters and mobile kiosks for commuters._
- See `Frontend/README.md` for instructions on setting up and running the frontend apps.
- _Example: You might run the customer app to simulate booking a ride, or the driver app to accept a trip._

## 7. Testing
- _Analogy: Running safety drills and system checks before opening the metro to the public._
- Tests are located in the `test/` directory.
- Run tests using cabal or the appropriate frontend test runner.
- _Example: Add a new feature, write a test to ensure it works, and run all tests to make sure nothing else broke._

## 8. Coding Standards & Contribution
- _Analogy: Following city building codes and submitting blueprints for approval._
- Follow the guidelines in `docs/CONTRIBUTING.md`.
- Use feature branches and submit pull requests for review.
- Ensure all code passes CI and tests before merging.
- _Example: Before merging a new payment method, ensure it’s reviewed and tested, just like a new metro line needs inspection._

## 9. Documentation
- _Analogy: The city’s operations manual—maps, emergency procedures, and maintenance guides._
- High-level docs: `docs/`
- Backend-specific: `Backend/doc/`
- Frontend-specific: `Frontend/README.md`
- _Example: If you’re lost, check the docs for directions or troubleshooting tips._

## 10. Support
- _Analogy: The help desk and control center—where you go when you hit a roadblock._
- For technical issues, reach out to the lead architect or designated tech leads.
- Use team communication channels for questions and updates.
- _Example: If your build fails or you’re unsure about a process, ask in the team chat or contact your onboarding buddy._

---
Welcome to the team! For any setup issues, contact the lead architect or your onboarding buddy. Think of us as your guides as you explore and help build this city of mobility.
