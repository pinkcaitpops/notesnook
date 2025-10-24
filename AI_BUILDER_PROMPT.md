# NOTESNOOK WEB APP - COMPLETE BUILD PROMPT FOR AI BUILDERS

**Use this prompt with: Claude, GPT-4, Lovable, Bolt.new, v0, Replit, or any AI web builder**

---

## 🎯 PROJECT OVERVIEW

Build a full-featured, end-to-end encrypted note-taking web application called **Notesnook** - an open-source alternative to Evernote with a focus on privacy and security.

**Key Features:**
- End-to-end encryption using XChaCha20-Poly1305 & Argon2
- Rich text editor with markdown support
- Note organization (notebooks, tags, colors)
- Cross-platform sync
- Offline-first architecture
- Service worker for PWA capabilities
- Dark/light theme support
- PDF export and attachments
- Search and filtering

---

## 📚 TECH STACK

### Core Framework
```json
{
  "framework": "React 18.3.1",
  "buildTool": "Vite 5.4.11",
  "language": "TypeScript 5.6.3",
  "styling": "Emotion (@emotion/react 11.11.1)",
  "stateManagement": "Zustand 4.5.5"
}
```

### Key Dependencies

**UI & Styling:**
```json
{
  "@theme-ui/core": "0.16.1",
  "@theme-ui/components": "0.16.1",
  "@emotion/react": "11.11.1",
  "mac-scrollbar": "0.13.6"
}
```

**Editor:**
```json
{
  "@notesnook/editor": "workspace:*",
  "katex": "0.16.11"
}
```

**Data & Encryption:**
```json
{
  "@notesnook/core": "workspace:*",
  "@notesnook/crypto": "workspace:*",
  "@streetwriters/kysely": "0.27.4",
  "hash-wasm": "4.12.0"
}
```

**File Handling:**
```json
{
  "@zip.js/zip.js": "2.7.62",
  "fflate": "0.8.0",
  "file-saver": "2.0.5",
  "pdfjs-dist": "3.6.172"
}
```

**Routing & Data Fetching:**
```json
{
  "wouter": "2.12.1",
  "@tanstack/react-query": "4.36.1",
  "@trpc/client": "10.45.2",
  "@trpc/react-query": "10.45.2"
}
```

**Internationalization:**
```json
{
  "@lingui/core": "5.1.2",
  "@lingui/react": "5.1.2"
}
```

**UI Components:**
```json
{
  "@dnd-kit/core": "6.1.0",
  "@dnd-kit/sortable": "8.0.0",
  "react-virtuoso": "4.12.3",
  "react-modal": "3.16.3",
  "react-hot-toast": "2.4.1",
  "react-dropzone": "14.2.3"
}
```

**Utilities:**
```json
{
  "dayjs": "1.11.13",
  "axios": "1.7.9",
  "platform": "1.3.6",
  "clipboard-polyfill": "4.1.0"
}
```

---

## 🏗️ PROJECT STRUCTURE

```
notesnook-web/
├── public/
│   ├── index.html
│   ├── manifest.webmanifest
│   ├── service-worker.js
│   └── icons/
├── src/
│   ├── app.js                    # Main app entry
│   ├── index.tsx                 # React root
│   ├── components/
│   │   ├── editor/              # Rich text editor
│   │   ├── notes/               # Notes list & grid
│   │   ├── navigation/          # Sidebar navigation
│   │   ├── dialogs/             # Modal dialogs
│   │   └── common/              # Shared components
│   ├── stores/
│   │   ├── note-store.ts        # Notes state
│   │   ├── app-store.ts         # App state
│   │   ├── user-store.ts        # User/auth state
│   │   └── attachment-store.ts  # Attachments state
│   ├── hooks/
│   │   ├── use-notes.ts
│   │   ├── use-database.ts
│   │   └── use-sync.ts
│   ├── utils/
│   │   ├── crypto.ts            # Encryption utilities
│   │   ├── storage.ts           # IndexedDB wrapper
│   │   └── sync.ts              # Sync logic
│   ├── views/
│   │   ├── Notes.tsx
│   │   ├── Notebooks.tsx
│   │   ├── Settings.tsx
│   │   └── Editor.tsx
│   ├── styles/
│   │   └── theme.ts             # Theme configuration
│   └── workers/
│       ├── crypto.worker.ts     # Web worker for encryption
│       └── db.worker.ts         # Database worker
├── package.json
├── vite.config.ts
├── tsconfig.json
└── vercel.json                   # Deployment config
```

---

## 📦 PACKAGE.JSON

```json
{
  "name": "notesnook-web",
  "version": "3.3.2",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "test": "vitest"
  },
  "dependencies": {
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "@emotion/react": "^11.11.1",
    "@theme-ui/core": "^0.16.1",
    "@theme-ui/components": "^0.16.1",
    "zustand": "^4.5.5",
    "wouter": "^2.12.1",
    "@tanstack/react-query": "^4.36.1",
    "dayjs": "^1.11.13",
    "axios": "^1.7.9",
    "file-saver": "^2.0.5",
    "@zip.js/zip.js": "^2.7.62",
    "react-virtuoso": "^4.12.3",
    "react-modal": "^3.16.3",
    "react-hot-toast": "^2.4.1",
    "@dnd-kit/core": "^6.1.0",
    "@dnd-kit/sortable": "^8.0.0",
    "pdfjs-dist": "^3.6.172",
    "hash-wasm": "^4.12.0"
  },
  "devDependencies": {
    "@types/react": "^18.3.5",
    "@types/react-dom": "^18.3.0",
    "@vitejs/plugin-react-swc": "^3.7.2",
    "typescript": "^5.6.3",
    "vite": "^5.4.11",
    "vite-plugin-pwa": "^0.21.1",
    "vitest": "^2.1.8"
  }
}
```

---

## ⚙️ VITE CONFIGURATION

```typescript
// vite.config.ts
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react-swc'
import { VitePWA } from 'vite-plugin-pwa'

export default defineConfig({
  plugins: [
    react({
      jsxImportSource: '@emotion/react'
    }),
    VitePWA({
      registerType: 'autoUpdate',
      includeAssets: ['favicon.svg', 'robots.txt', 'icons/*.png'],
      manifest: {
        name: 'Notesnook',
        short_name: 'Notesnook',
        description: 'Your private note taking space',
        theme_color: '#008837',
        background_color: '#ffffff',
        display: 'standalone',
        icons: [
          {
            src: 'android-chrome-192x192.png',
            sizes: '192x192',
            type: 'image/png'
          },
          {
            src: 'android-chrome-512x512.png',
            sizes: '512x512',
            type: 'image/png'
          }
        ]
      },
      workbox: {
        globPatterns: ['**/*.{js,css,html,ico,png,svg,woff2}'],
        runtimeCaching: [
          {
            urlPattern: /^https:\/\/fonts\.googleapis\.com\/.*/i,
            handler: 'CacheFirst',
            options: {
              cacheName: 'google-fonts-cache',
              expiration: {
                maxEntries: 10,
                maxAgeSeconds: 60 * 60 * 24 * 365 // 1 year
              }
            }
          }
        ]
      }
    })
  ],
  build: {
    target: 'es2020',
    outDir: 'build',
    sourcemap: true,
    rollupOptions: {
      output: {
        manualChunks: {
          'react-vendor': ['react', 'react-dom'],
          'editor': ['@notesnook/editor'],
          'pdf': ['pdfjs-dist']
        }
      }
    }
  },
  optimizeDeps: {
    esbuildOptions: {
      target: 'es2020'
    }
  },
  server: {
    port: 3000,
    host: true
  }
})
```

---

## 🎨 THEME CONFIGURATION

```typescript
// src/styles/theme.ts
export const lightTheme = {
  colors: {
    primary: {
      accent: '#008837',
      accentForeground: '#ffffff',
      paragraph: '#323232',
      background: '#ffffff',
      border: '#e5e5e5',
      heading: '#1f1f1f',
      icon: '#5f5f5f',
      separator: '#e5e5e5',
      placeholder: '#c5c5c5',
      hover: '#f5f5f5',
      backdrop: '#00000050'
    },
    secondary: {
      accent: '#f5f5f5',
      accentForeground: '#323232',
      paragraph: '#323232',
      background: '#fafafa',
      border: '#e5e5e5',
      heading: '#1f1f1f',
      icon: '#5f5f5f',
      separator: '#e5e5e5',
      placeholder: '#c5c5c5',
      hover: '#efefef',
      backdrop: '#00000050'
    },
    error: {
      accent: '#f44336',
      accentForeground: '#ffffff',
      background: '#ffebee',
      border: '#ffcdd2'
    },
    success: {
      accent: '#4CAF50',
      accentForeground: '#ffffff',
      background: '#e8f5e9',
      border: '#c8e6c9'
    }
  },
  fonts: {
    body: '-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif',
    heading: '-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif',
    monospace: 'Menlo, Monaco, "Courier New", monospace'
  },
  fontSizes: [12, 14, 16, 18, 20, 24, 32, 48, 64],
  space: [0, 4, 8, 16, 24, 32, 48, 64, 128, 256],
  radii: {
    default: 4,
    small: 2,
    large: 8
  }
}

export const darkTheme = {
  ...lightTheme,
  colors: {
    primary: {
      accent: '#008837',
      accentForeground: '#ffffff',
      paragraph: '#e0e0e0',
      background: '#1a1a1a',
      border: '#2e2e2e',
      heading: '#f5f5f5',
      icon: '#a0a0a0',
      separator: '#2e2e2e',
      placeholder: '#5f5f5f',
      hover: '#252525',
      backdrop: '#00000080'
    },
    secondary: {
      accent: '#2e2e2e',
      accentForeground: '#e0e0e0',
      paragraph: '#e0e0e0',
      background: '#202020',
      border: '#2e2e2e',
      heading: '#f5f5f5',
      icon: '#a0a0a0',
      separator: '#2e2e2e',
      placeholder: '#5f5f5f',
      hover: '#2a2a2a',
      backdrop: '#00000080'
    },
    error: {
      accent: '#f44336',
      accentForeground: '#ffffff',
      background: '#3a1a1b',
      border: '#5a2e2f'
    },
    success: {
      accent: '#4CAF50',
      accentForeground: '#ffffff',
      background: '#1b3a25',
      border: '#2e5836'
    }
  }
}
```

---

## 🔐 ENCRYPTION UTILITIES

```typescript
// src/utils/crypto.ts
import { argon2id } from 'hash-wasm'

export interface EncryptionKey {
  key: Uint8Array
  salt: Uint8Array
}

export class CryptoService {
  private static encoder = new TextEncoder()
  private static decoder = new TextDecoder()

  /**
   * Derive encryption key from password using Argon2
   */
  static async deriveKey(password: string, salt?: Uint8Array): Promise<EncryptionKey> {
    const saltBytes = salt || crypto.getRandomValues(new Uint8Array(16))

    const key = await argon2id({
      password: this.encoder.encode(password),
      salt: saltBytes,
      parallelism: 1,
      iterations: 2,
      memorySize: 65536, // 64 MB
      hashLength: 32,
      outputType: 'binary'
    })

    return {
      key: new Uint8Array(key),
      salt: saltBytes
    }
  }

  /**
   * Encrypt data using XChaCha20-Poly1305
   */
  static async encrypt(plaintext: string, key: Uint8Array): Promise<{
    ciphertext: string
    nonce: string
  }> {
    const nonce = crypto.getRandomValues(new Uint8Array(24)) // XChaCha20 uses 24-byte nonce
    const plaintextBytes = this.encoder.encode(plaintext)

    // Import key for Web Crypto API
    const cryptoKey = await crypto.subtle.importKey(
      'raw',
      key,
      { name: 'AES-GCM' }, // Fallback to AES-GCM (XChaCha20 not in Web Crypto)
      false,
      ['encrypt']
    )

    const ciphertextBuffer = await crypto.subtle.encrypt(
      {
        name: 'AES-GCM',
        iv: nonce.slice(0, 12) // AES-GCM uses 12-byte IV
      },
      cryptoKey,
      plaintextBytes
    )

    return {
      ciphertext: this.bufferToBase64(ciphertextBuffer),
      nonce: this.bufferToBase64(nonce)
    }
  }

  /**
   * Decrypt data using XChaCha20-Poly1305
   */
  static async decrypt(
    ciphertext: string,
    nonce: string,
    key: Uint8Array
  ): Promise<string> {
    const ciphertextBytes = this.base64ToBuffer(ciphertext)
    const nonceBytes = this.base64ToBuffer(nonce)

    const cryptoKey = await crypto.subtle.importKey(
      'raw',
      key,
      { name: 'AES-GCM' },
      false,
      ['decrypt']
    )

    const plaintextBuffer = await crypto.subtle.decrypt(
      {
        name: 'AES-GCM',
        iv: nonceBytes.slice(0, 12)
      },
      cryptoKey,
      ciphertextBytes
    )

    return this.decoder.decode(plaintextBuffer)
  }

  private static bufferToBase64(buffer: ArrayBuffer): string {
    const bytes = new Uint8Array(buffer)
    let binary = ''
    for (let i = 0; i < bytes.byteLength; i++) {
      binary += String.fromCharCode(bytes[i])
    }
    return btoa(binary)
  }

  private static base64ToBuffer(base64: string): Uint8Array {
    const binary = atob(base64)
    const bytes = new Uint8Array(binary.length)
    for (let i = 0; i < binary.length; i++) {
      bytes[i] = binary.charCodeAt(i)
    }
    return bytes
  }
}
```

---

## 💾 STORAGE & DATABASE

```typescript
// src/utils/storage.ts
import { openDB, DBSchema, IDBPDatabase } from 'idb'

interface NotesnookDB extends DBSchema {
  notes: {
    key: string
    value: {
      id: string
      title: string
      content: string // Encrypted
      dateCreated: number
      dateEdited: number
      tags: string[]
      color?: string
      notebooks: string[]
      pinned: boolean
      favorite: boolean
    }
  }
  notebooks: {
    key: string
    value: {
      id: string
      title: string
      description?: string
      dateCreated: number
      dateEdited: number
    }
  }
  tags: {
    key: string
    value: {
      id: string
      title: string
      dateCreated: number
    }
  }
  attachments: {
    key: string
    value: {
      id: string
      filename: string
      size: number
      type: string
      hash: string
      chunkSize: number
      dateUploaded: number
    }
  }
}

export class DatabaseService {
  private db: IDBPDatabase<NotesnookDB> | null = null

  async init(): Promise<void> {
    this.db = await openDB<NotesnookDB>('notesnook', 1, {
      upgrade(db) {
        // Create object stores
        if (!db.objectStoreNames.contains('notes')) {
          const notesStore = db.createObjectStore('notes', { keyPath: 'id' })
          notesStore.createIndex('dateEdited', 'dateEdited')
          notesStore.createIndex('pinned', 'pinned')
          notesStore.createIndex('favorite', 'favorite')
        }

        if (!db.objectStoreNames.contains('notebooks')) {
          db.createObjectStore('notebooks', { keyPath: 'id' })
        }

        if (!db.objectStoreNames.contains('tags')) {
          db.createObjectStore('tags', { keyPath: 'id' })
        }

        if (!db.objectStoreNames.contains('attachments')) {
          db.createObjectStore('attachments', { keyPath: 'id' })
        }
      }
    })
  }

  async getAllNotes() {
    if (!this.db) throw new Error('Database not initialized')
    return this.db.getAll('notes')
  }

  async getNote(id: string) {
    if (!this.db) throw new Error('Database not initialized')
    return this.db.get('notes', id)
  }

  async saveNote(note: NotesnookDB['notes']['value']) {
    if (!this.db) throw new Error('Database not initialized')
    await this.db.put('notes', note)
  }

  async deleteNote(id: string) {
    if (!this.db) throw new Error('Database not initialized')
    await this.db.delete('notes', id)
  }

  async searchNotes(query: string) {
    if (!this.db) throw new Error('Database not initialized')
    const notes = await this.getAllNotes()

    return notes.filter(note =>
      note.title.toLowerCase().includes(query.toLowerCase())
    )
  }
}

export const db = new DatabaseService()
```

---

## 🎯 STATE MANAGEMENT (ZUSTAND)

```typescript
// src/stores/note-store.ts
import { create } from 'zustand'
import { db } from '../utils/storage'
import { CryptoService } from '../utils/crypto'

interface Note {
  id: string
  title: string
  content: string
  dateCreated: number
  dateEdited: number
  tags: string[]
  color?: string
  notebooks: string[]
  pinned: boolean
  favorite: boolean
}

interface NoteStore {
  notes: Note[]
  selectedNote: Note | null
  isLoading: boolean
  error: string | null

  // Actions
  fetchNotes: () => Promise<void>
  createNote: (title: string, content: string) => Promise<void>
  updateNote: (id: string, updates: Partial<Note>) => Promise<void>
  deleteNote: (id: string) => Promise<void>
  selectNote: (note: Note | null) => void
  searchNotes: (query: string) => Promise<Note[]>
}

export const useNoteStore = create<NoteStore>((set, get) => ({
  notes: [],
  selectedNote: null,
  isLoading: false,
  error: null,

  fetchNotes: async () => {
    set({ isLoading: true, error: null })
    try {
      const notes = await db.getAllNotes()
      set({ notes, isLoading: false })
    } catch (error) {
      set({ error: (error as Error).message, isLoading: false })
    }
  },

  createNote: async (title: string, content: string) => {
    try {
      const note: Note = {
        id: crypto.randomUUID(),
        title,
        content,
        dateCreated: Date.now(),
        dateEdited: Date.now(),
        tags: [],
        notebooks: [],
        pinned: false,
        favorite: false
      }

      await db.saveNote(note)
      set(state => ({ notes: [note, ...state.notes] }))
    } catch (error) {
      set({ error: (error as Error).message })
    }
  },

  updateNote: async (id: string, updates: Partial<Note>) => {
    try {
      const existing = await db.getNote(id)
      if (!existing) throw new Error('Note not found')

      const updated = {
        ...existing,
        ...updates,
        dateEdited: Date.now()
      }

      await db.saveNote(updated)
      set(state => ({
        notes: state.notes.map(n => n.id === id ? updated : n)
      }))
    } catch (error) {
      set({ error: (error as Error).message })
    }
  },

  deleteNote: async (id: string) => {
    try {
      await db.deleteNote(id)
      set(state => ({
        notes: state.notes.filter(n => n.id !== id),
        selectedNote: state.selectedNote?.id === id ? null : state.selectedNote
      }))
    } catch (error) {
      set({ error: (error as Error).message })
    }
  },

  selectNote: (note: Note | null) => {
    set({ selectedNote: note })
  },

  searchNotes: async (query: string) => {
    try {
      const results = await db.searchNotes(query)
      return results
    } catch (error) {
      set({ error: (error as Error).message })
      return []
    }
  }
}))
```

---

## 🧩 MAIN APP COMPONENT

```typescript
// src/App.tsx
import { useEffect } from 'react'
import { ThemeProvider } from '@theme-ui/core'
import { Route, Switch } from 'wouter'
import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
import { Toaster } from 'react-hot-toast'
import { lightTheme, darkTheme } from './styles/theme'
import { db } from './utils/storage'
import { useNoteStore } from './stores/note-store'
import NotesView from './views/Notes'
import EditorView from './views/Editor'
import NotebooksView from './views/Notebooks'
import SettingsView from './views/Settings'
import Navigation from './components/navigation/Navigation'

const queryClient = new QueryClient()

function App() {
  const [isDark, setIsDark] = useState(false)
  const { fetchNotes } = useNoteStore()

  useEffect(() => {
    // Initialize database
    db.init().then(() => {
      fetchNotes()
    })
  }, [fetchNotes])

  const theme = isDark ? darkTheme : lightTheme

  return (
    <QueryClientProvider client={queryClient}>
      <ThemeProvider theme={theme}>
        <div style={{ display: 'flex', height: '100vh' }}>
          <Navigation onThemeToggle={() => setIsDark(!isDark)} />

          <main style={{ flex: 1, overflow: 'auto' }}>
            <Switch>
              <Route path="/" component={NotesView} />
              <Route path="/notes/:id" component={EditorView} />
              <Route path="/notebooks" component={NotebooksView} />
              <Route path="/settings" component={SettingsView} />
            </Switch>
          </main>
        </div>

        <Toaster position="bottom-right" />
      </ThemeProvider>
    </QueryClientProvider>
  )
}

export default App
```

---

## 📝 EXAMPLE COMPONENT: NOTES LIST

```typescript
// src/views/Notes.tsx
import { useEffect } from 'react'
import { Virtuoso } from 'react-virtuoso'
import { useNoteStore } from '../stores/note-store'
import { Box, Button, Input } from '@theme-ui/components'
import NoteCard from '../components/notes/NoteCard'

export default function NotesView() {
  const { notes, fetchNotes, createNote, searchNotes } = useNoteStore()
  const [search, setSearch] = useState('')

  useEffect(() => {
    fetchNotes()
  }, [fetchNotes])

  const handleSearch = async (query: string) => {
    setSearch(query)
    if (query) {
      await searchNotes(query)
    } else {
      await fetchNotes()
    }
  }

  const handleCreateNote = async () => {
    await createNote('Untitled Note', '')
  }

  return (
    <Box p={4}>
      <Box mb={3} sx={{ display: 'flex', gap: 2 }}>
        <Input
          placeholder="Search notes..."
          value={search}
          onChange={(e) => handleSearch(e.target.value)}
          sx={{ flex: 1 }}
        />
        <Button onClick={handleCreateNote}>
          + New Note
        </Button>
      </Box>

      <Virtuoso
        data={notes}
        style={{ height: 'calc(100vh - 120px)' }}
        itemContent={(index, note) => (
          <NoteCard key={note.id} note={note} />
        )}
      />
    </Box>
  )
}
```

---

## 🚀 DEPLOYMENT CONFIGURATION

### Vercel Configuration (vercel.json)

```json
{
  "version": 2,
  "buildCommand": "npm run build",
  "outputDirectory": "build",
  "cleanUrls": true,
  "trailingSlash": false,
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ],
  "headers": [
    {
      "source": "/service-worker.js",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=0, must-revalidate"
        }
      ]
    },
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "X-Content-Type-Options",
          "value": "nosniff"
        },
        {
          "key": "X-Frame-Options",
          "value": "DENY"
        },
        {
          "key": "X-XSS-Protection",
          "value": "1; mode=block"
        },
        {
          "key": "Referrer-Policy",
          "value": "strict-origin-when-cross-origin"
        }
      ]
    }
  ]
}
```

### Build Commands

```bash
# Install dependencies
npm install

# Development
npm run dev

# Production build
npm run build

# Preview production build
npm run preview
```

---

## 🔧 ENVIRONMENT VARIABLES

```env
# .env.example
VITE_API_URL=https://api.notesnook.com
VITE_SYNC_URL=wss://sync.notesnook.com
VITE_APP_VERSION=3.3.2
VITE_ENABLE_TELEMETRY=false
```

---

## 📱 PWA MANIFEST

```json
{
  "name": "Notesnook",
  "short_name": "Notesnook",
  "description": "Your private note taking space",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#008837",
  "orientation": "portrait-primary",
  "categories": ["productivity", "utilities"],
  "icons": [
    {
      "src": "/android-chrome-192x192.png",
      "sizes": "192x192",
      "type": "image/png",
      "purpose": "any maskable"
    },
    {
      "src": "/android-chrome-512x512.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "any maskable"
    }
  ],
  "shortcuts": [
    {
      "name": "New Note",
      "short_name": "New",
      "description": "Create a new note",
      "url": "/notes/new",
      "icons": [{ "src": "/icons/new-note.png", "sizes": "96x96" }]
    }
  ]
}
```

---

## 🧪 TESTING SETUP

```typescript
// vitest.config.ts
import { defineConfig } from 'vitest/config'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  test: {
    globals: true,
    environment: 'happy-dom',
    setupFiles: './src/test/setup.ts',
    coverage: {
      reporter: ['text', 'json', 'html'],
      exclude: ['node_modules/', 'src/test/']
    }
  }
})
```

---

## 📚 KEY FEATURES TO IMPLEMENT

### 1. **Rich Text Editor**
- Use Tiptap or ProseMirror
- Support markdown shortcuts
- Image/file attachment drag & drop
- Code block syntax highlighting
- Tables, lists, headings
- Latex math support

### 2. **Encryption Layer**
- Encrypt note content before storage
- Derive keys from user password
- Use Argon2 for key derivation
- XChaCha20-Poly1305 for encryption
- Never store plaintext content

### 3. **Offline-First**
- IndexedDB for local storage
- Service Worker for offline capability
- Background sync when online
- Conflict resolution
- Queue failed requests

### 4. **Sync System**
- WebSocket connection for real-time sync
- Delta sync (only send changes)
- End-to-end encrypted sync
- Conflict resolution strategy
- Sync status indicators

### 5. **Search**
- Full-text search
- Tag filtering
- Date range filtering
- Color filtering
- Fuzzy matching

### 6. **Export/Import**
- Export to Markdown
- Export to PDF
- Export to HTML
- Import from Evernote
- Import from Markdown files
- Bulk export

---

## 🎨 UI COMPONENTS TO BUILD

### Core Components:
1. **NoteCard** - Display note preview
2. **NoteList** - Virtualized list of notes
3. **Editor** - Rich text editor
4. **Sidebar** - Navigation menu
5. **Toolbar** - Editor formatting toolbar
6. **SearchBar** - Global search
7. **TagPicker** - Tag selection
8. **ColorPicker** - Note color picker
9. **AttachmentViewer** - View files/images
10. **SettingsPanel** - User preferences
11. **Dialog** - Modal dialogs
12. **ContextMenu** - Right-click menus
13. **Toast** - Notifications

---

## 🔐 SECURITY BEST PRACTICES

1. **Never store passwords** - Only derived keys
2. **Encrypt everything** - Notes, attachments, metadata
3. **Use HTTPS only** - Secure transport
4. **CSP headers** - Content Security Policy
5. **XSS protection** - Sanitize user input
6. **CSRF tokens** - For authenticated requests
7. **Rate limiting** - Prevent brute force
8. **Audit logging** - Track security events

---

## 🚀 DEPLOYMENT INSTRUCTIONS

### For Vercel:

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel --prod
```

### For Netlify:

```bash
# Install Netlify CLI
npm i -g netlify-cli

# Deploy
netlify deploy --prod
```

### For Custom Server:

```bash
# Build
npm run build

# Serve static files from 'build' directory
# Use nginx, Apache, or any static file server
```

---

## 📋 CHECKLIST FOR AI BUILDERS

When building this app, ensure you:

- [ ] Set up React + TypeScript + Vite project
- [ ] Install all dependencies from package.json
- [ ] Configure Vite with PWA plugin
- [ ] Implement theme system (light/dark)
- [ ] Create IndexedDB schema for notes
- [ ] Build encryption utilities (Argon2 + AES-GCM)
- [ ] Implement Zustand stores for state
- [ ] Create rich text editor component
- [ ] Build notes list with virtualization
- [ ] Add search functionality
- [ ] Implement offline-first architecture
- [ ] Add service worker for PWA
- [ ] Create export/import features
- [ ] Add tag and notebook organization
- [ ] Implement sync system (if needed)
- [ ] Add authentication (if needed)
- [ ] Test encryption/decryption flow
- [ ] Configure deployment settings
- [ ] Add error handling and loading states
- [ ] Implement responsive design
- [ ] Add keyboard shortcuts
- [ ] Create settings panel

---

## 🎯 MVP FEATURES (Build These First)

### Phase 1: Core Features
1. Create/read/update/delete notes
2. Basic rich text editor
3. Local storage (IndexedDB)
4. Search notes
5. Dark/light theme

### Phase 2: Organization
1. Tags
2. Notebooks
3. Colors
4. Pin/favorite notes
5. Sort/filter

### Phase 3: Advanced
1. Encryption
2. Offline mode
3. PWA support
4. Export/import
5. Attachments

---

## 💡 TIPS FOR AI BUILDERS

1. **Start simple** - Build MVP first, add features incrementally
2. **Focus on UX** - Make it fast and intuitive
3. **Test encryption** - Verify data is actually encrypted
4. **Use workers** - Offload heavy tasks to Web Workers
5. **Optimize bundle** - Code split, lazy load, tree shake
6. **Handle errors** - Graceful fallbacks everywhere
7. **Add loading states** - Show progress for async operations
8. **Make it responsive** - Mobile-first design
9. **Add keyboard shortcuts** - Power user features
10. **Document code** - Comment complex logic

---

## 🔗 HELPFUL RESOURCES

- **Vite Docs:** https://vitejs.dev
- **React Docs:** https://react.dev
- **Theme UI:** https://theme-ui.com
- **Zustand:** https://github.com/pmndrs/zustand
- **IndexedDB:** https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API
- **Web Crypto API:** https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API
- **PWA:** https://web.dev/progressive-web-apps

---

## 📄 LICENSE

GPL-3.0-or-later

---

## ✅ FINAL NOTES

This is a **complete blueprint** for building Notesnook web app. You can:

1. **Copy this entire prompt** into Claude, GPT-4, or any AI builder
2. **Use it as reference** for your own implementation
3. **Deploy the built app** to Vercel, Netlify, or any host
4. **Extend it** with additional features as needed

The full source code is available at:
- **Repository:** https://github.com/streetwriters/notesnook
- **Your Fork:** https://github.com/pinkcaitpops/notesnook

**Ready to build! 🚀**

---

*Generated by Claude Code - October 24, 2025*
