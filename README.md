## 🎬 Next.js 15 + Tailwind TMDB Challenge

### 1. Purpose
You will build a small, production‑style web application that showcases your ability to work with **Next.js 15 (App Router)**, **Tailwind CSS**, **Axios**, and **React Query** while consuming the **TMDB (The Movie Database) REST API**. The app must allow anonymous browsing of trending content and authenticated users to save favourites.

### 2. High‑Level Goals
* Solid Next.js architecture (App Router, Server/Client Components split)
* Clean data‑fetching & caching with React Query and Axios
* Responsive, accessible UI built with Tailwind
* Authentication & protected routes
* Persistent favourite logic
* Git workflow & documentation that mirrors real‑world engineering standards

### 3. Functional Requirements
| ID | Feature | Details |
|----|---------|---------|
| F1 | **Home – Trending** | Show today’s trending Movies & TV Shows (2 carousels). Data: `/trending/{media_type}/day` |
| F2 | **Global Search** | Search movies, TV shows, and people with `/search/multi`. Display results in an infinite scroll grid. |
| F3 | **Movie Detail Page** | Route: `/movie/[id]`. Show poster, title, tagline, genres, runtime, rating, overview, top‑billed cast (6), trailer embed, and “Similar titles”. |
| F4 | **TV Show Detail Page** | Route: `/tv/[id]`. Show poster, name, seasons, status, rating, overview, cast, trailer, similar shows. |
| F5 | **Authentication** | Implement login & signup (email+password *or* OAuth via Google/GitHub). Use **NextAuth.js** with JWT session strategy. |
| F6 | **Favourites** | Logged‑in users can **add/remove** favourites from movie & TV pages. A dedicated **“My Favourites”** page lists them (paginated). Persist to a lightweight DB (Supabase, Planetscale, SQLite with Prisma, or mock JSON server). |
| F7 | **Account Menu** | Navbar avatar → dropdown: My Favourites, Logout. |
| F8 | **Responsive Design** | Mobile‑first; graceful desktop enhancements. |
| F9 | **Loading & Error States** | Skeletons/spinners while fetching; toasts or inline banners on error. |
| F10 | **SEO & Metadata** | Dynamic `<title>` & `<meta>` tags using `generateMetadata` for each detail page. |

### 4. Technical Requirements
1. **Next.js 15**
   * Use the **App Router** (`app/` directory) & React Server Components by default.
   * Route Handlers for any custom API endpoints (e.g., favourites CRUD).
2. **TypeScript** with `"strict": true`.
3. **Tailwind CSS** (PostCSS plugins allowed). Implement a light/dark theme toggle.
4. **Axios** for HTTP calls, wrapped in a thin abstraction (`src/lib/tmdb.ts`).
5. **React Query v5**
   * `QueryClientProvider` at root.
   * Proper query keys & staleTime settings.
   * Prefetching where it improves UX (e.g., hover on poster).
6. **State Management**
   * React Query cache for server data.
   * Local component/Context/Zustand for UI state (theme toggle, modals).
7. **Auth**
   * NextAuth.js v5 with credentials or OAuth provider.
   * Protect `/favourites` route via `auth()` in Server Component.
8. **Testing** (Nice‑to‑have but scored):
   * Vitest or Jest + React Testing Library for at least 3 critical components.
9. **Linting & Formatting**
   * ESLint (Next.js preset) & Prettier. CI should fail on lint errors.
10. **CI/CD**
    * GitHub Actions: install, lint, type‑check, test, then deploy preview to **Vercel**.

### 5. TMDB Integration
1. Register for a **free API key** at <https://www.themoviedb.org/settings/api>.
2. Add the key as `TMDB_API_KEY` in `.env.local` (never commit!).
3. Base URL: `https://api.themoviedb.org/3`.
4. Required endpoints (non‑exhaustive):
   * `/trending/{media_type}/{time_window}`
   * `/movie/{movie_id}`
   * `/tv/{tv_id}`
   * `/movie/{movie_id}/videos` & `/tv/{tv_id}/videos`
   * `/movie/{movie_id}/credits` & `/tv/{tv_id}/credits`
   * `/movie/{movie_id}/similar` & `/tv/{tv_id}/similar`
   * `/search/multi`

### 6. Acceptance Criteria
* All **F1–F9** implemented.
* Lighthouse score ≥ 80 on mobile (Performance & Accessibility).
* No console errors or unhandled promise rejections.
* Build succeeds on Vercel.
* README explains setup, env vars, and design decisions.

### 7. Deliverables
1. **Public GitHub repo** named `next15-tmdb-challenge-<your‑name>`.
2. **README.md** containing:
   * Project overview + link to live demo.
   * Setup & run instructions (`pnpm dev`, etc.).
   * Architectural diagram or explanation (RSC vs CSC, data‑flow).
   * Assumptions & trade‑offs.
   * Future work ideas.
3. **Live deployment** (Vercel). Provide URL.
4. (Optional) 2‑minute Loom walkthrough.

### 8. Evaluation Rubric
| Area | Weight |
|------|--------|
| Code Quality & Architecture | 30% |
| Feature Completeness | 25% |
| UI/UX & Responsiveness | 15% |
| Data‑fetching & Caching Strategy | 15% |
| Git & Documentation | 10% |
| Bonus (tests, animations, etc.) | 5% |


### 9. Bonus Ideas (Not required, impress us!)
* Service Worker + Offline support.
* Framer‑motion animations on route change.
* Internationalisation (i18n) using `next-intl`.
* Use **TMDB images** with `next/image` and blurred placeholders.
* Dark mode preference saved to `localStorage`.

---
### 10. Submission
Send us:
1. GitHub repo link
2. Live URL
3. (Optional) Loom video
4. Short email summarising what you’d improve with more time

Good luck & have fun building! 🍿