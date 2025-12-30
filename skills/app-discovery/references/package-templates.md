# Package Configuration Templates

Templates for generating `package.json` (Node/React) or `pyproject.toml` (Python) during the finalize step.

---

## When to Generate

During **app-creator:finalize**, after generating docs, also create the package configuration:

1. Read tech stack from CLAUDE.md
2. Apply sensible defaults for that stack
3. Add project-specific dependencies identified during discovery
4. Include standard testing libraries

---

## Node/React: package.json Template

### Base Template (React + TypeScript + Vite)

```json
{
  "name": "[project-name-kebab-case]",
  "version": "0.1.0",
  "private": true,
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "test": "vitest",
    "test:ui": "vitest --ui",
    "test:coverage": "vitest --coverage",
    "lint": "eslint . --ext ts,tsx",
    "typecheck": "tsc --noEmit"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.0",
    "@types/react-dom": "^18.2.0",
    "@vitejs/plugin-react": "^4.2.0",
    "typescript": "^5.3.0",
    "vite": "^5.0.0",
    "vitest": "^1.0.0",
    "@vitest/ui": "^1.0.0",
    "eslint": "^8.55.0",
    "@typescript-eslint/eslint-plugin": "^6.0.0",
    "@typescript-eslint/parser": "^6.0.0"
  }
}
```

### Common Add-ons (include based on features)

**Environment Variables:**
```json
{
  "dependencies": {
    "dotenv": "^16.3.0"
  }
}
```

**Canvas/Graphics:**
```json
{
  "devDependencies": {
    "@types/offscreencanvas": "^2019.7.0"
  }
}
```

**Audio/Web Audio API:**
```json
{
  "devDependencies": {
    "standardized-audio-context": "^25.3.0",
    "@types/audioworklet": "^0.0.0"
  }
}
```

**State Management:**
```json
{
  "dependencies": {
    "zustand": "^4.4.0"
  }
}
```

**API/HTTP:**
```json
{
  "dependencies": {
    "axios": "^1.6.0"
  }
}
```

**AI/LLM Integration:**
```json
{
  "dependencies": {
    "ai": "^2.2.0",
    "openai": "^4.20.0"
  }
}
```

**TTS Providers:**
```json
{
  "dependencies": {
    "elevenlabs": "^0.1.0"
  }
}
```

**Styling:**
```json
{
  "dependencies": {
    "tailwindcss": "^3.4.0",
    "postcss": "^8.4.0",
    "autoprefixer": "^10.4.0"
  }
}
```

---

## Python: pyproject.toml Template

### Base Template (Modern Python)

```toml
[project]
name = "[project-name-kebab-case]"
version = "0.1.0"
description = "[Brief project description from CLAUDE.md]"
readme = "README.md"
requires-python = ">=3.11"
dependencies = [
    "pydantic>=2.5.0",
    "python-dotenv>=1.0.0",
]

[project.optional-dependencies]
dev = [
    "pytest>=7.4.0",
    "pytest-cov>=4.1.0",
    "pytest-asyncio>=0.21.0",
    "ruff>=0.1.0",
    "mypy>=1.7.0",
]

[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[tool.pytest.ini_options]
testpaths = ["tests"]
asyncio_mode = "auto"

[tool.ruff]
line-length = 100
target-version = "py311"

[tool.mypy]
python_version = "3.11"
strict = true
```

### Common Add-ons (include based on features)

**Web Framework (FastAPI):**
```toml
dependencies = [
    "fastapi>=0.104.0",
    "uvicorn[standard]>=0.24.0",
]
```

**Web Framework (Flask):**
```toml
dependencies = [
    "flask>=3.0.0",
    "flask-cors>=4.0.0",
]
```

**Database (SQLAlchemy):**
```toml
dependencies = [
    "sqlalchemy>=2.0.0",
    "alembic>=1.13.0",
]
```

**Database (async):**
```toml
dependencies = [
    "sqlalchemy[asyncio]>=2.0.0",
    "asyncpg>=0.29.0",
]
```

**HTTP Client:**
```toml
dependencies = [
    "httpx>=0.25.0",
]
```

**AI/LLM Integration:**
```toml
dependencies = [
    "openai>=1.3.0",
    "anthropic>=0.7.0",
]
```

**Audio Processing:**
```toml
dependencies = [
    "pydub>=0.25.0",
    "soundfile>=0.12.0",
    "numpy>=1.26.0",
]
```

**Data Processing:**
```toml
dependencies = [
    "pandas>=2.1.0",
    "numpy>=1.26.0",
]
```

---

## How to Use in app-creator:finalize

### Step 1: Determine Stack

Read CLAUDE.md and identify:
- Primary language (Node/Python)
- Framework (React, Next.js, FastAPI, Flask)
- Key features that need dependencies

### Step 2: Build Configuration

Start with base template, then:
1. Add add-ons based on features in features.md
2. Add any dependencies explicitly mentioned during discovery
3. Keep it minimal — only what's needed for v1

### Step 3: Generate File

**For Node projects:**
- Create `package.json` at project root
- Do NOT run `npm install` (that's dev-protocol:init's job)

**For Python projects:**
- Create `pyproject.toml` at project root
- Do NOT create venv or install (that's dev-protocol:init's job)

### Step 4: Document in CLAUDE.md

Add a section noting what was included:

```markdown
## Dependencies

Generated in `package.json` / `pyproject.toml`:

**Core:**
- React, TypeScript, Vite

**Project-specific:**
- Web Audio API types (for audio processing)
- Zustand (state management)

**Testing:**
- Vitest + UI

**To install:** Run `/dev-protocol:init` or `npm install`
```

---

## Example: TTS Visualizer package.json

Based on the discovery session:

```json
{
  "name": "elyse-speech-visualizer",
  "version": "0.1.0",
  "private": true,
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "test": "vitest",
    "test:ui": "vitest --ui",
    "lint": "eslint . --ext ts,tsx",
    "typecheck": "tsc --noEmit"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "dotenv": "^16.3.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.0",
    "@types/react-dom": "^18.2.0",
    "@vitejs/plugin-react": "^4.2.0",
    "typescript": "^5.3.0",
    "vite": "^5.0.0",
    "vitest": "^1.0.0",
    "@vitest/ui": "^1.0.0",
    "eslint": "^8.55.0",
    "@typescript-eslint/eslint-plugin": "^6.0.0",
    "@typescript-eslint/parser": "^6.0.0"
  }
}
```

**Notes:**
- Web Audio API is browser-native (no package needed)
- Canvas 2D is browser-native (no package needed)
- Eleven Labs SDK can be added when needed (env var dependency)
- Kept minimal for v1 — add packages as features require them

---


