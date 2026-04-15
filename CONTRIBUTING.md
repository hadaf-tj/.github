# Contributing to Hadaf

First off, thank you for considering contributing to Hadaf! It is people like you who make this platform a reality, helping us build a transparent, zero-transaction digital bridge for social good in Tajikistan.

As a contributor, here are the guidelines we would like you to follow to keep our codebase clean, secure, and maintainable:

- [Got a Question or Problem?](#question)
- [Found a Security Vulnerability?](#security)
- [Issues and Bugs](#issue)
- [Feature Requests](#feature)
- [Submission Guidelines](#submit)
- [Commit Message Format](#commit)

## <a name="question"></a> Got a Question or Problem?

If you have a question about the architecture, need help setting up your local environment, or want community support:

- You can ask in our [Developer & Community Telegram Channel](https://t.me/hadaf_tjk).
- You can open a "Question" issue in the relevant repository.

## <a name="security"></a> Found a security vulnerability?

**Please do not report security vulnerabilities on the public GitHub issue tracker.** Because Hadaf deals with the needs of social institutions, security is our top priority. If you find a vulnerability, please contact the core team directly via Telegram at [@siyovush_hamidov](https://t.me/siyovush_hamidov).

## <a name="issue"></a> Found a Bug?

If you find a bug in the source code, you can help us by [submitting an issue](#submit-issue) to the corresponding repository (Backend, Frontend, or Mobile).
Even better, you can [submit a Pull Request](#submit-pr) with a fix!

## <a name="feature"></a> Missing a Feature?

You can *request* a new feature by submitting an issue to our GitHub Repository. If you would like to *implement* a new feature, please submit an issue with a proposal for your work first, to be sure that it aligns with our roadmap.

- For a **Major Feature** (e.g., a new user role, a complex dashboard module), first open an issue and outline your proposal so that it can be discussed with the CTO. This prevents duplication of work.
- **Small Features** (e.g., UI tweaks, minor optimizations) can be crafted and directly [submitted as a Pull Request](#submit-pr).

## <a name="submit"></a> Submission Guidelines

### <a name="submit-issue"></a> Submitting an Issue

Before you submit an issue, please search the issue tracker; maybe an issue for your problem already exists and the discussion might inform you of workarounds readily available.

In order to reproduce bugs, we ask you to provide a minimal, clear set of steps to reproduce the problem, along with your environment details (OS, browser, or device).

### <a name="submit-pr"></a> Submitting a Pull Request (PR)

**The Golden Rule:** The `main` branch is strictly protected. You must never push directly to `main`. 

Before you submit your Pull Request (PR) consider the following guidelines:

1. Search the repository for an open or closed PR that relates to your submission.
2. Fork the repository and make your changes in a new git branch:
   ```shell
   git checkout -b feat/my-new-feature main
   ```
3. Create your patch. **Do not commit secrets, `.env` files, or API keys.**
4. Commit your changes using descriptive commit messages. See our [commit message conventions](#commit) below.
   ```shell
   git commit -a
   ```
5. Push your branch to GitHub:
   ```shell
   git push origin feat/my-new-feature
   ```
6. In GitHub, open a Pull Request against the `main` branch of the upstream Hadaf repository.
7. Wait for a code review from the core maintainers. If changes are requested, simply push new commits to your branch—the PR will update automatically.

## <a name="commit"></a> Commit Message Guidelines

We follow the [Conventional Commits](https://www.conventionalcommits.org/) format to help generate changelogs and keep our commit history readable. 

```text
<type>: <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

Any line of the commit message should not be longer than 100 characters.

### Type

Must be one of the following:

- **build**: Changes that affect the build system or external dependencies (e.g., Go modules, npm packages)
- **chore**: Other changes that don't amend functionality (e.g., formatting, updating scripts)
- **ci**: Changes to our CI/CD configuration files (e.g., GitHub Actions)
- **docs**: Documentation only changes
- **feat**: A new feature
- **fix**: A bug fix
- **perf**: A code change that improves performance
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc.)
- **test**: Adding missing tests or correcting existing tests

### Subject

The subject contains a succinct description of the change:

- Use the imperative, present tense: "change" not "changed" nor "changes"
- Don't capitalize the first letter
- No dot (.) at the end

### Body & Footer

Just as in the subject, use the imperative, present tense. The body should include the motivation for the change.
If your commit introduces a **Breaking Change**, the footer must start with `BREAKING CHANGE:` followed by a description. If your PR closes an open issue, add `Closes #123` in the footer.

## Grants & Infrastructure Support

Hadaf does not process financial donations for charity. However, maintaining high-availability enterprise servers and CI/CD pipelines requires resources. If you represent an NGO, an accelerator, or a corporate sponsor interested in supporting our **infrastructure and operational costs**, please reach out to the project lead on [LinkedIn](https://www.linkedin.com/company/hadaftj).

## Credits

Thank you to all the developers, designers, and QA engineers who volunteer their time to build a transparent future for charity in Tajikistan!

<a href="https://github.com/hadaf-tj/hadaf-backend/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=hadaf-tj/hadaf-backend" alt="Contributors" />
</a>

---

## Style Guide — Go Backend

### Formatting

- Always run `gofmt` (or `gofumpt`) before committing — CI will reject unformatted code.
- Run `go vet ./...` and `golangci-lint run` locally before opening a PR.

### Imports

Group imports in the following order, separated by blank lines:

```go
import (
    // 1. Standard library
    "context"
    "fmt"

    // 2. Third-party
    "github.com/gin-gonic/gin"
    "github.com/rs/zerolog"

    // 3. Internal packages
    "shb/internal/models"
    "shb/pkg/myerrors"
)
```

### Naming Conventions

| Entity | Convention | Example |
|---|---|---|
| Packages | `lowercase`, single word | `services`, `handlers` |
| Exported types | `PascalCase` | `BookingService` |
| Unexported variables | `camelCase` | `userID` |
| Interfaces | Noun or `-er` suffix | `IRepository`, `Limiter` |
| Error vars | `Err` prefix | `ErrNotFound` |

> **No transliteration.** All identifiers must be in English.

### GoDoc Comments

Every exported symbol **must** have a GoDoc comment beginning with its name:

```go
// CreateBooking registers a volunteer's intent to fulfil a specific need.
func (s *Service) CreateBooking(ctx context.Context, ...) (int, error) { ... }
```

### Error Codes (i18n-Ready)

User-facing errors passed to `myerrors.New*Err()` must use `UPPER_SNAKE_CASE` machine-readable codes. The frontend maps these to localised UI text.

```go
// ✅ Correct
return myerrors.NewConflictErr("ERR_BOOKING_ALREADY_EXISTS")

// ❌ Wrong — natural language in user-facing errors
return myerrors.NewConflictErr("у вас уже есть заявка")
```

Internal `fmt.Errorf` strings (for logging) remain as natural English prose.

### License Header

Every new source file must begin with:

```go
// SPDX-License-Identifier: AGPL-3.0-or-later
// Copyright (C) 2026 Siyovush Hamidov and The Hadaf Contributors
```

Do **not** add headers to config files (`.yaml`, `.json`, `go.mod`, `go.sum`) or auto-generated files.

### Dead Code

- Remove all commented-out code blocks.
- Remove obvious no-op comments (e.g., `// returns user` above `GetUser`).

---

## Style Guide — React / Next.js Frontend

### Formatting

- Use **Prettier** (config in `.prettierrc`) and **ESLint** before committing.
- Run `npm run lint` locally before opening a PR.

### Naming Conventions

| Entity | Convention | Example |
|---|---|---|
| Components | `PascalCase` | `BookingCard.tsx` |
| Hooks | `camelCase` with `use` prefix | `useBookings.ts` |
| Utilities | `camelCase` | `formatDate.ts` |
| Constants | `UPPER_SNAKE_CASE` | `MAX_RETRY_COUNT` |

### i18n Error Codes

Map API error codes to localised strings via the i18n layer. Never display raw codes to users.

```ts
// ✅ Correct
const message = t(`errors.${error.message}`) ?? t('errors.GENERIC')

// ❌ Wrong
toast.error(error.message) // shows "ERR_BOOKING_ALREADY_EXISTS" to the user
```
