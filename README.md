# SlotSwapper

**SlotSwapper** is a peer-to-peer time-slot scheduling application built for the ServiceHive Full Stack Intern technical challenge.

- Users create calendar events and mark busy events as *swappable*.
- Other users can request swaps by offering one of their swappable slots.
- Swap requests can be accepted or rejected by the target owner; accepted swaps atomically swap slot ownership.

---

## Live demo (optional)
- Frontend: `<your-frontend-deploy-url>`  
- Backend: `<your-backend-deploy-url>`  

(If not deployed, skip or add the link later.)

---

## Tech stack

- Backend: Node.js, Express
- Auth: JWT (Bearer token)
- Database: SQLite (Sequelize ORM) — easy local setup; can be swapped for Postgres in prod
- Frontend: React (Vite / CRA)
- Dev tools: nodemon, dotenv, cors

---

## Design choices & tradeoffs

- **SQLite + Sequelize** for simplicity and reproducibility in a challenge environment.
- **JWT** for stateless, simple session handling and easy curl/postman testing.
- **Atomic swap logic** implemented in a DB transaction to avoid race conditions.
- UI kept minimal to emphasize correctness of swap logic and API clarity.

---

## Assumptions & notes

- Event times are ISO timestamps; the server stores them as `DATE`.
- A slot can only participate in one pending swap at a time (server sets `SWAP_PENDING`).
- No overlap/time-conflict checks implemented (left as improvement).
- No email verification or password recovery included (out-of-scope for this challenge).
- For production, move to PostgreSQL and secure the JWT secret in environment variables.

---

## Repo structure (high level)

