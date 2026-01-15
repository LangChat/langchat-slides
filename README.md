# LangChat Slides - Next-Gen AI Slide Generator

<div align="center">

**LangChat Slides** is an intelligent slide generation tool powered by Generative AI. Built by the LangChat Team.

<img src="docs/slides.gif" alt="LangChat Slides Demo" width="800" />

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Star](https://img.shields.io/github/stars/langchat/langchat-slides?style=social)](https://github.com/LangChat/langchat-slides)
[![Fork](https://img.shields.io/github/forks/langchat/langchat-slides?style=social)](https://github.com/LangChat/langchat-slides)

[Website](https://www.langchat.cn) · [Preview](https://slides.langchat.cn) · [Documentation](docs) · [GitHub](https://github.com/LangChat/langchat-slides) · [Report Bug](mailto:langchat@outlook.com)

**[🇨🇳 中文文档](README_CN.md)** | **[English README](README.md)**

**加入微信交流群：LangchainChat（备注：AI应用开发学习）**

</div>

---

## 📖 About LangChat Pro

**LangChat Pro** is an enterprise-level AIGC (AI-Generated Content) platform and a full-stack AI application system built on Spring Boot 3 + LangChain4j + Vue3 + VueFlow.

**LangChat Slides** is one of the flagship products of LangChat Pro, leveraging the powerful model capabilities of LangChat and the visualization engine of `@antv/infographic`. Users can simply input natural language descriptions to instantly generate clear, well-designed infographic slides.

### 💎 About LangChat Pro Commercial Edition

**LangChat Pro** is an **enterprise-grade AIGC application development platform commercial edition** built on the Java ecosystem, providing enterprises with complete AI large model integration solutions. Built on Spring Boot 3 and Vue 3, it supports rapid development of intelligent knowledge bases, multimodal AI applications, and intelligent workflows, helping enterprises achieve AI-driven digital transformation.

**Official Website**: http://langchat.cn/

**Open Source Edition**: https://github.com/tycoding/langchat (Basic features)

**Commercial Edition Consultation**: Add WeChat **LangchainChat** (Note: Company Name + [Consultation Content])

![workflows](docs/workflows.jpg)

---

## 🎯 Product Features

![slides](docs/slides.png)

### 🎨 Core Capabilities

- **🤖 AI-Powered Generation**: Generate professional slides instantly with natural language descriptions
- **⚡ Real-Time Streaming**: Watch slides render in real-time as AI generates content (WYSIWYG)
- **🎯 Intelligent Layout**: Declarative syntax auto-adapts to optimal visual layouts,告别繁琐的 PPT 拖拽
- **💬 Conversational Editing**: Chat with AI to refine - "Change title to red" or "Add a timeline"
- **📄 Multi-Page Support**: Generate multiple pages with thumbnail navigation
- **🎨 Rich Templates**: 30+ built-in infographic templates (timeline, charts, lists, etc.)
- **🌐 Theme Customization**: Light/Dark modes with multiple color palettes
- **📤 Easy Export**: One-click export to PDF, PNG, SVG, JPG, WebP, or PPT

### 🎨 Visual Experience

- **Modern UI**: Built with Shadcn UI and Tailwind CSS for a premium, minimal design
- **Responsive Layout**: Adapts perfectly to different screen sizes
- **Real-Time Preview**: Instant feedback as you type or adjust
- **Code Editor**: View and edit slide syntax directly with live rendering

### 🧠 AI Intelligence

- **Smart Understanding**: Interprets natural language to generate appropriate layouts
- **Streaming Response**: Real-time content updates as AI thinks and generates
- **Markdown Compatibility**: Automatically handles AI responses with markdown code blocks
- **Multi-Model Support**: Compatible with OpenAI GPT-4, GPT-3.5, and other models

### 🛠️ Advanced Features

- **Split/Append Mode**: Choose to replace or append new slides
- **Custom Slides**: Manually create slides with infographic syntax
- **Slide Management**: Add empty slides, clear all slides, switch between pages
- **Zoom Controls**: Adjust canvas scale from 50% to 250%
- **Keyboard Shortcuts**: Efficient workflow with hotkeys
- **i18n Support**: Built-in English and Chinese language options

---

## 🏗️ Project Architecture

### Overall Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     LangChat Slides                        │
│                   (Vue 3 + TypeScript)                    │
├─────────────────────────────────────────────────────────────┤
│  UI Layer                                                  │
│  ├── App.vue (Main Container)                               │
│  ├── Layout Components                                       │
│  │   ├── Header (Navigation & Settings)                      │
│  │   └── ResizablePanel (Split View)                        │
│  │       ├── Left Panel (Input & Code)                       │
│  │       │   ├── ControlBar (Theme & Page Count)              │
│  │       │   ├── PromptInput (Chat Input)                    │
│  │       │   ├── ExampleGenerator (Quick Templates)            │
│  │       │   └── CodeEditor (Syntax Editor)                 │
│  │       └── Right Panel (Preview & Navigation)               │
│  │           ├── SlidesContainer                             │
│  │           │   ├── SlideThumbnail (Page Navigation)          │
│  │           │   └── SlidesCanvas                           │
│  │           │       ├── SlidesHeader (Toolbar)              │
│  │           │       └── SlidePreview (Canvas)              │
│  │           └── SlideWelcome (Empty State)                   │
│  └── Dialog Components                                      │
│      ├── SettingsDialog (API Configuration)                    │
│      └── CustomSlideDialog (Manual Input)                    │
├─────────────────────────────────────────────────────────────┤
│  Business Logic Layer                                        │
│  ├── useSlideGenerator (Slide Generation Logic)               │
│  │   ├── Streaming Response Handling                         │
│  │   ├── Markdown Cleaning                                 │
│  │   └── Multi-Page Generation                           │
│  └── useI18n (Internationalization)                         │
├─────────────────────────────────────────────────────────────┤
│  State Management (Pinia Store)                               │
│  └── useAppStore                                           │
│      ├── Slides State (slides[], currentIndex)                 │
│      ├── Theme State (dark/light, palette, sketch)             │
│      ├── API Configuration (apiKey, baseUrl, model)            │
│      ├── UI State (isStreaming, canvasScale)                 │
│      └── Export State (exportRequest)                        │
├─────────────────────────────────────────────────────────────┤
│  Integration Layer                                          │
│  ├── useAI (OpenAI API Integration)                         │
│  │   ├── Stream Chat (Real-time)                           │
│  │   └── Error Handling                                  │
│  └── @antv/infographic (Visualization Engine)              │
│      ├── Slide Rendering                                    │
│      ├── Theme Application                                  │
│      └── Export (PNG/SVG/PDF)                            │
├─────────────────────────────────────────────────────────────┤
│  Utility Layer                                              │
│  ├── slide-utils.ts (Template Management)                     │
│  └── utils.ts (Helper Functions)                           │
└─────────────────────────────────────────────────────────────┘
```

### Data Flow

```
User Input (Prompt)
       ↓
┌─────────────────────────────────────────┐
│ 1. Input Processing                  │
│    - Prompt captured                 │
│    - Theme & page count selected     │
│    - AI model configured            │
└─────────────────────────────────────────┘
       ↓
┌─────────────────────────────────────────┐
│ 2. AI Request (Streaming)           │
│    - Send to OpenAI API             │
│    - Receive chunks in real-time      │
│    - Clean markdown code blocks       │
└─────────────────────────────────────────┘
       ↓
┌─────────────────────────────────────────┐
│ 3. Content Parsing                 │
│    - Extract infographic syntax      │
│    - Validate structure            │
│    - Create slide objects          │
└─────────────────────────────────────────┘
       ↓
┌─────────────────────────────────────────┐
│ 4. State Update (Pinia)            │
│    - Update slides array             │
│    - Set current slide index        │
│    - Trigger reactive updates      │
└─────────────────────────────────────────┘
       ↓
┌─────────────────────────────────────────┐
│ 5. Real-Time Rendering              │
│    - Update CodeEditor (left)      │
│    - Update SlidePreview (right)    │
│    - Check syntax completeness     │
│    - Render with @antv/infographic │
└─────────────────────────────────────────┘
       ↓
┌─────────────────────────────────────────┐
│ 6. User Interaction                │
│    - Manual editing in CodeEditor   │
│    - Click thumbnails to navigate   │
│    - Adjust theme/settings         │
│    - Trigger re-render            │
└─────────────────────────────────────────┘
       ↓
┌─────────────────────────────────────────┐
│ 7. Export (Optional)               │
│    - Canvas to image (html2canvas)  │
│    - Image to PDF (jspdf)          │
│    - Download file                 │
└─────────────────────────────────────────┘
```

---

## 📁 Directory Structure

```
langchat-slides/
├── docs/                           # Documentation
│   ├── infographic-api.md           # Infographic API reference
│   ├── PPT_EXPORT_GUIDE.md        # Export guide
│   ├── PRODUCT.md                 # Product documentation
│   ├── REQUIREMENTS.md            # Requirements & implementation
│   ├── slides.gif                # Demo GIF
│   └── workflows.jpg            # Workflow diagram
│
├── public/                        # Static assets
│   └── favicon.ico              # Website icon
│
├── src/
│   ├── api/                      # API integration layer
│   │   └── ai.ts               # OpenAI API wrapper with streaming
│   │
│   ├── assets/                   # Static resources
│   │   └── prompts/            # System prompts for AI
│   │       ├── prompt.md         # English prompt template
│   │       └── prompt.zh-CN.md  # Chinese prompt template
│   │
│   ├── components/               # Vue components
│   │   ├── chat/              # Chat-related components (legacy)
│   │   │   ├── ChatContainer.vue
│   │   │   ├── ChatInput.vue
│   │   │   ├── ChatMessage.vue
│   │   │   └── ChatOverlay.vue
│   │   │
│   │   ├── layout/            # Layout components
│   │   │   ├── CustomSlideDialog.vue  # Manual slide input
│   │   │   ├── Header.vue           # Top navigation
│   │   │   ├── SettingsDialog.vue    # API settings
│   │   │   └── index.ts
│   │   │
│   │   ├── panel/            # Left panel components
│   │   │   ├── CodeEditor.vue       # Syntax code editor
│   │   │   ├── ControlBar.vue       # Theme & page controls
│   │   │   ├── PromptInput.vue      # Chat input
│   │   │   └── index.ts
│   │   │
│   │   ├── slides/           # Slide rendering components
│   │   │   ├── SlidePreview.vue     # Main preview canvas
│   │   │   ├── SlidesCanvas.vue    # Canvas container
│   │   │   ├── SlidesContainer.vue # Slide list & thumbnails
│   │   │   ├── SlidesHeader.vue    # Toolbar (zoom, export, etc.)
│   │   │   ├── SlidesWelcome.vue   # Empty state
│   │   │   ├── SlideThumbnail.vue  # Page thumbnail
│   │   │   └── SlideControlPanel.vue
│   │   │
│   │   ├── ui/               # Shadcn UI components
│   │   │   ├── avatar/
│   │   │   ├── button/
│   │   │   ├── card/
│   │   │   ├── dialog/
│   │   │   ├── dropdown-menu/
│   │   │   ├── input/
│   │   │   ├── label/
│   │   │   ├── navigation-menu/
│   │   │   ├── resizable/
│   │   │   ├── scroll-area/
│   │   │   ├── select/
│   │   │   ├── switch/
│   │   │   ├── textarea/
│   │   │   └── tooltip/
│   │   │
│   │   └── ExampleGenerator.vue  # Example templates selector
│   │
│   ├── composables/           # Vue composition functions
│   │   ├── useI18n.ts       # Internationalization hook
│   │   └── useSlideGenerator.ts  # Slide generation logic
│   │
│   ├── examples/              # Example templates
│   │   ├── ExampleGenerator.vue  # Example selector component
│   │   └── examples.ts      # Example data (16 templates)
│   │
│   ├── lib/                  # Utility functions
│   │   ├── slide-utils.ts    # Infographic templates & utilities
│   │   └── utils.ts         # General utilities
│   │
│   ├── locales/             # i18n translations
│   │   ├── en.json         # English translations
│   │   └── zh.json         # Chinese translations
│   │
│   ├── stores/              # Pinia state management
│   │   └── useAppStore.ts  # Main application state
│   │
│   ├── types/               # TypeScript type definitions
│   │   └── index.ts        # Shared types
│   │
│   ├── App.vue              # Root component
│   ├── env.d.ts            # Environment variable types
│   ├── main.ts             # Application entry point
│   └── style.css           # Global styles
│
├── components.json         # Shadcn UI configuration
├── Dockerfile            # Docker build configuration
├── docker-compose.yml    # Docker Compose configuration
├── index.html           # HTML entry point
├── LICENSE              # Apache 2.0 License
├── package.json         # Dependencies & scripts
├── pnpm-lock.yaml      # Lock file
├── README.md          # This file (English)
├── README_CN.md       # Chinese documentation
├── tsconfig.app.json   # TypeScript config (app)
├── tsconfig.json      # TypeScript config (base)
├── tsconfig.node.json # TypeScript config (node)
├── vite.config.d.ts   # Vite types
└── vite.config.mts    # Vite build configuration
```

---

## 🛠️ Technology Stack

### Frontend Framework
- **Vue 3**: Progressive JavaScript framework with Composition API
- **TypeScript**: Type-safe development experience
- **Vite 7**: Next-generation frontend build tool

### UI & Styling
- **Tailwind CSS v4**: Utility-first CSS framework for rapid UI development
- **Shadcn Vue**: Beautiful, accessible, customizable UI components
- **Lucide Vue Next**: Modern icon library

### State Management
- **Pinia**: Intuitive, type-safe, and flexible state management for Vue

### Visualization Engine
- **@antv/infographic**: Powerful infographic visualization library
  - 30+ built-in infographic templates
  - Real-time rendering and editing
  - Export to PNG, SVG, PDF
  - Theme and palette support

### AI Integration
- **OpenAI API**: Direct frontend integration
  - Streaming responses (Server-Sent Events)
  - Support for GPT-4, GPT-3.5-turbo
  - Customizable model selection
  - Markdown code block handling

### Export Functionality
- **html2canvas**: Convert DOM to canvas
- **jspdf**: Generate PDF from images
- **PptxGenJS**: Generate PowerPoint files

### Development Tools
- **ESLint**: Code quality and style checking
- **TypeScript Strict Mode**: Enhanced type safety
- **pnpm**: Fast, disk space efficient package manager

---

## 🚀 Quick Start

### Prerequisites

- Node.js >= 20.x
- pnpm >= 8.x
- OpenAI API Key (or compatible API)

### Local Development

1. **Clone repository**
   ```bash
   git clone https://github.com/LangChat/langchat-slides.git
   cd langchat-slides
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env
   # Edit .env and add your OpenAI API key
   ```

4. **Start development server**
   ```bash
   pnpm dev
   ```

   Access at `http://localhost:5173`

5. **Build for production**
   ```bash
   pnpm build
   ```

### Docker Deployment

#### Using Docker Compose (Recommended)

```bash
# Clone and configure
git clone https://github.com/LangChat/langchat-slides.git
cd langchat-slides
cp .env.example .env
# Edit .env with your API key

# Build and start
docker-compose up -d

# View logs
docker-compose logs -f

# Stop service
docker-compose down
```

#### Using Docker directly

```bash
# Build image
docker build -t langchat-slides .

# Run container
docker run -d \
  --name langchat-slides \
  -p 5173:5173 \
  -e VITE_OPENAI_API_KEY=your-api-key \
  langchat-slides
```

---

## 🌐 Environment Variables

Create a `.env` file in the root directory:

```env
# OpenAI Configuration
VITE_OPENAI_API_KEY=sk-your-api-key-here
VITE_OPENAI_BASE_URL=https://api.openai.com/v1
VITE_OPENAI_MODEL=gpt-4o

# Application Configuration
VITE_DEFAULT_LOCALE=en
VITE_APP_THEME=auto
```

---

## 📖 Usage Guide

### Creating Slides

1. **Describe your needs**: Type your slide requirements in natural language
   - Example: "Create a timeline showing AI history from 1950 to 2024"
   - Example: "Generate a SWOT analysis for a tech startup"

2. **Select template**: Choose from 30+ infographic templates (timeline, charts, lists, etc.)

3. **Set page count**: Specify how many pages to generate (1-10)

4. **Real-time generation**: Watch as AI generates and renders slides instantly

5. **Manual editing**: Edit the infographic syntax directly in the code editor

6. **Export**: Click export button to download as PDF, PNG, SVG, JPG, WebP, or PPT

### Advanced Features

**Conversational Editing**
- "Change the color theme to blue"
- "Add more details about machine learning"
- "Make the timeline horizontal"

**Manual Slides**
- Click "Custom Slide" to manually input infographic syntax
- Supports all @antv/infographic templates

**Slide Management**
- Click "+" to add empty slides
- Click thumbnails to navigate between pages
- Use toolbar to clear all slides or switch between replace/append mode

---

## 🎯 Use Cases

- **📊 Business Presentations**: Quick slide generation for meetings and reports
- **📚 Education**: Transform complex concepts into visual timelines and hierarchies
- **📈 Data Visualization**: Present structured data in engaging infographic formats
- **🎨 Creative Work**: Rapid prototyping and idea visualization
- **📝 Documentation**: Create visual documentation and guides
- **💼 Marketing**: Generate promotional materials and presentations

---

## 🤝 Contributing

We welcome contributions! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📝 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

---

## 📧 Contact

- **Website**: https://www.langchat.cn
- **Email**: langchat@outlook.com
- **Team**: LangChat Team

---

## 🙏 Acknowledgments

- [OpenAI](https://openai.com/) - Powerful AI models
- [AntV](https://antv.vision/) - Infographic visualization engine
- [Vue.js](https://vuejs.org/) - Progressive JavaScript framework
- [Shadcn](https://ui.shadcn.com/) - Beautiful UI components
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first styling
- [Vercel](https://vercel.com/) - Deployment platform

---

**Developed with ❤️ by the LangChat Team**
