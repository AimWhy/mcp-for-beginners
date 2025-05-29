<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "1446979020432f512c883848d7eca144",
  "translation_date": "2025-05-29T21:51:42+00:00",
  "source_file": "00-Introduction/README.md",
  "language_code": "id"
}
-->
# Pengenalan Model Context Protocol (MCP): Mengapa Ini Penting untuk Aplikasi AI yang Skalabel

Aplikasi AI generatif adalah langkah maju yang besar karena sering memungkinkan pengguna berinteraksi dengan aplikasi menggunakan perintah bahasa alami. Namun, seiring bertambahnya waktu dan sumber daya yang diinvestasikan dalam aplikasi seperti ini, Anda ingin memastikan bahwa Anda dapat dengan mudah mengintegrasikan fungsi dan sumber daya dengan cara yang mudah dikembangkan, aplikasi Anda dapat melayani lebih dari satu model yang digunakan, dan menangani berbagai kompleksitas model. Singkatnya, membangun aplikasi Gen AI mudah dimulai, tetapi saat berkembang dan menjadi lebih kompleks, Anda perlu mulai mendefinisikan arsitektur dan kemungkinan besar perlu mengandalkan standar untuk memastikan aplikasi Anda dibangun secara konsisten. Di sinilah MCP hadir untuk mengatur segala sesuatu dan menyediakan standar.

---

## **🔍 Apa Itu Model Context Protocol (MCP)?**

**Model Context Protocol (MCP)** adalah **antarmuka terbuka dan terstandarisasi** yang memungkinkan Large Language Models (LLM) berinteraksi dengan mulus dengan alat eksternal, API, dan sumber data. Ini menyediakan arsitektur konsisten untuk meningkatkan fungsi model AI di luar data pelatihannya, memungkinkan sistem AI yang lebih cerdas, skalabel, dan responsif.

---

## **🎯 Mengapa Standarisasi dalam AI Penting**

Seiring aplikasi AI generatif menjadi lebih kompleks, sangat penting untuk mengadopsi standar yang memastikan **skalabilitas, ekstensi**, dan **pemeliharaan**. MCP memenuhi kebutuhan ini dengan:

- Menyatukan integrasi model dan alat
- Mengurangi solusi kustom yang rapuh dan sekali pakai
- Memungkinkan beberapa model untuk hidup berdampingan dalam satu ekosistem

---

## **📚 Tujuan Pembelajaran**

Pada akhir artikel ini, Anda akan dapat:

- Mendefinisikan **Model Context Protocol (MCP)** dan kasus penggunaannya
- Memahami bagaimana MCP menstandarisasi komunikasi model-ke-alat
- Mengidentifikasi komponen inti arsitektur MCP
- Menjelajahi aplikasi nyata MCP dalam konteks perusahaan dan pengembangan

---

## **💡 Mengapa Model Context Protocol (MCP) Merupakan Pengubah Permainan**

### **🔗 MCP Mengatasi Fragmentasi dalam Interaksi AI**

Sebelum MCP, mengintegrasikan model dengan alat memerlukan:

- Kode kustom untuk setiap pasangan alat-model
- API yang tidak standar untuk setiap vendor
- Sering terjadi gangguan karena pembaruan
- Skalabilitas buruk dengan bertambahnya alat

### **✅ Manfaat Standarisasi MCP**

| **Manfaat**              | **Deskripsi**                                                                |
|--------------------------|-------------------------------------------------------------------------------|
| Interoperabilitas        | LLM bekerja mulus dengan alat dari berbagai vendor                            |
| Konsistensi              | Perilaku seragam di berbagai platform dan alat                               |
| Dapat Digunakan Kembali  | Alat yang dibangun sekali dapat digunakan di berbagai proyek dan sistem       |
| Percepatan Pengembangan  | Mengurangi waktu pengembangan dengan menggunakan antarmuka standar plug-and-play |

---

## **🧱 Gambaran Arsitektur MCP Tingkat Tinggi**

MCP mengikuti model **client-server**, di mana:

- **MCP Hosts** menjalankan model AI
- **MCP Clients** menginisiasi permintaan
- **MCP Servers** menyediakan konteks, alat, dan kapabilitas

### **Komponen Utama:**

- **Resources** – Data statis atau dinamis untuk model  
- **Prompts** – Alur kerja yang sudah ditentukan untuk generasi yang terarah  
- **Tools** – Fungsi yang dapat dijalankan seperti pencarian, perhitungan  
- **Sampling** – Perilaku agen melalui interaksi rekursif

---

## Cara Kerja MCP Servers

MCP server beroperasi dengan cara berikut:

- **Alur Permintaan**: 
    1. MCP Client mengirimkan permintaan ke Model AI yang berjalan di MCP Host.
    2. Model AI mengidentifikasi saat membutuhkan alat atau data eksternal.
    3. Model berkomunikasi dengan MCP Server menggunakan protokol standar.

- **Fungsi MCP Server**:
    - Registri Alat: Menjaga katalog alat yang tersedia dan kapabilitasnya.
    - Autentikasi: Memverifikasi izin akses alat.
    - Pengelola Permintaan: Memproses permintaan alat yang masuk dari model.
    - Pengatur Format Respon: Menyusun output alat dalam format yang dapat dipahami model.

- **Eksekusi Alat**: 
    - Server mengarahkan permintaan ke alat eksternal yang sesuai
    - Alat menjalankan fungsi khususnya (pencarian, perhitungan, query database, dll.)
    - Hasil dikembalikan ke model dalam format yang konsisten.

- **Penyelesaian Respon**: 
    - Model AI menggabungkan output alat ke dalam responnya.
    - Respon akhir dikirim kembali ke aplikasi klien.

```mermaid
---
title: MCP Server Architecture and Component Interactions
description: A diagram showing how AI models interact with MCP servers and various tools, depicting the request flow and server components including Tool Registry, Authentication, Request Handler, and Response Formatter
---
graph TD
    A[AI Model in MCP Host] <-->|MCP Protocol| B[MCP Server]
    B <-->|Tool Interface| C[Tool 1: Web Search]
    B <-->|Tool Interface| D[Tool 2: Calculator]
    B <-->|Tool Interface| E[Tool 3: Database Access]
    B <-->|Tool Interface| F[Tool 4: File System]
    
    Client[MCP Client/Application] -->|Sends Request| A
    A -->|Returns Response| Client
    
    subgraph "MCP Server Components"
        B
        G[Tool Registry]
        H[Authentication]
        I[Request Handler]
        J[Response Formatter]
    end
    
    B <--> G
    B <--> H
    B <--> I
    B <--> J
    
    style A fill:#f9d5e5,stroke:#333,stroke-width:2px
    style B fill:#eeeeee,stroke:#333,stroke-width:2px
    style Client fill:#d5e8f9,stroke:#333,stroke-width:2px
    style C fill:#c2f0c2,stroke:#333,stroke-width:1px
    style D fill:#c2f0c2,stroke:#333,stroke-width:1px
    style E fill:#c2f0c2,stroke:#333,stroke-width:1px
    style F fill:#c2f0c2,stroke:#333,stroke-width:1px    
```

## 👨‍💻 Cara Membangun MCP Server (Dengan Contoh)

MCP server memungkinkan Anda memperluas kapabilitas LLM dengan menyediakan data dan fungsi.

Siap mencoba? Berikut contoh membuat MCP server sederhana dalam berbagai bahasa:

- **Contoh Python**: https://github.com/modelcontextprotocol/python-sdk

- **Contoh TypeScript**: https://github.com/modelcontextprotocol/typescript-sdk

- **Contoh Java**: https://github.com/modelcontextprotocol/java-sdk

- **Contoh C#/.NET**: https://github.com/modelcontextprotocol/csharp-sdk

## 🌍 Kasus Penggunaan MCP di Dunia Nyata

MCP memungkinkan berbagai aplikasi dengan memperluas kapabilitas AI:

| **Aplikasi**               | **Deskripsi**                                                                |
|----------------------------|-------------------------------------------------------------------------------|
| Integrasi Data Perusahaan  | Menghubungkan LLM ke database, CRM, atau alat internal                        |
| Sistem AI Agenik           | Mengaktifkan agen otonom dengan akses alat dan alur pengambilan keputusan     |
| Aplikasi Multi-modal       | Menggabungkan teks, gambar, dan alat audio dalam satu aplikasi AI terpadu    |
| Integrasi Data Real-time   | Membawa data langsung ke interaksi AI untuk hasil yang lebih akurat dan terkini |

### 🧠 MCP = Standar Universal untuk Interaksi AI

Model Context Protocol (MCP) bertindak sebagai standar universal untuk interaksi AI, mirip seperti USB-C yang menstandarisasi koneksi fisik untuk perangkat. Dalam dunia AI, MCP menyediakan antarmuka konsisten, memungkinkan model (klien) terintegrasi mulus dengan alat eksternal dan penyedia data (server). Ini menghilangkan kebutuhan protokol kustom yang beragam untuk setiap API atau sumber data.

Di bawah MCP, alat yang kompatibel MCP (disebut MCP server) mengikuti standar terpadu. Server ini dapat mencantumkan alat atau aksi yang mereka tawarkan dan menjalankan aksi tersebut saat diminta oleh agen AI. Platform agen AI yang mendukung MCP mampu menemukan alat yang tersedia dari server dan memanggilnya melalui protokol standar ini.

### 💡 Memudahkan akses ke pengetahuan

Selain menawarkan alat, MCP juga memudahkan akses ke pengetahuan. Ini memungkinkan aplikasi memberikan konteks kepada large language models (LLM) dengan menghubungkannya ke berbagai sumber data. Misalnya, MCP server bisa mewakili repositori dokumen perusahaan, memungkinkan agen mengambil informasi relevan sesuai permintaan. Server lain bisa menangani aksi spesifik seperti mengirim email atau memperbarui catatan. Dari perspektif agen, ini hanyalah alat yang bisa digunakan—beberapa alat mengembalikan data (konteks pengetahuan), sementara yang lain melakukan aksi. MCP mengelola keduanya secara efisien.

Agen yang terhubung ke MCP server secara otomatis mempelajari kapabilitas yang tersedia dan data yang dapat diakses melalui format standar. Standarisasi ini memungkinkan ketersediaan alat secara dinamis. Misalnya, menambahkan MCP server baru ke sistem agen membuat fungsinya langsung dapat digunakan tanpa perlu kustomisasi lebih lanjut pada instruksi agen.

Integrasi yang lancar ini sesuai dengan alur yang digambarkan dalam diagram mermaid, di mana server menyediakan alat dan pengetahuan, memastikan kolaborasi yang mulus antar sistem.

### 👉 Contoh: Solusi Agen yang Skalabel

```mermaid
---
title: Scalable Agent Solution with MCP
description: A diagram illustrating how a user interacts with an LLM that connects to multiple MCP servers, with each server providing both knowledge and tools, creating a scalable AI system architecture
---
graph TD
    User -->|Prompt| LLM
    LLM -->|Response| User
    LLM -->|MCP| ServerA
    LLM -->|MCP| ServerB
    ServerA -->|Universal connector| ServerB
    ServerA --> KnowledgeA
    ServerA --> ToolsA
    ServerB --> KnowledgeB
    ServerB --> ToolsB

    subgraph Server A
        KnowledgeA[Knowledge]
        ToolsA[Tools]
    end

    subgraph Server B
        KnowledgeB[Knowledge]
        ToolsB[Tools]
    end
```

### 🔄 Skenario MCP Lanjutan dengan Integrasi LLM di Sisi Klien

Selain arsitektur MCP dasar, ada skenario lanjutan di mana klien dan server sama-sama mengandung LLM, memungkinkan interaksi yang lebih canggih:

```mermaid
---
title: Advanced MCP Scenarios with Client-Server LLM Integration
description: A sequence diagram showing the detailed interaction flow between user, client application, client LLM, multiple MCP servers, and server LLM, illustrating tool discovery, user interaction, direct tool calling, and feature negotiation phases
---
sequenceDiagram
    autonumber
    actor User as 👤 User
    participant ClientApp as 🖥️ Client App
    participant ClientLLM as 🧠 Client LLM
    participant Server1 as 🔧 MCP Server 1
    participant Server2 as 📚 MCP Server 2
    participant ServerLLM as 🤖 Server LLM
    
    %% Discovery Phase
    rect rgb(220, 240, 255)
        Note over ClientApp, Server2: TOOL DISCOVERY PHASE
        ClientApp->>+Server1: Request available tools/resources
        Server1-->>-ClientApp: Return tool list (JSON)
        ClientApp->>+Server2: Request available tools/resources
        Server2-->>-ClientApp: Return tool list (JSON)
        Note right of ClientApp: Store combined tool<br/>catalog locally
    end
    
    %% User Interaction
    rect rgb(255, 240, 220)
        Note over User, ClientLLM: USER INTERACTION PHASE
        User->>+ClientApp: Enter natural language prompt
        ClientApp->>+ClientLLM: Forward prompt + tool catalog
        ClientLLM->>-ClientLLM: Analyze prompt & select tools
    end
    
    %% Scenario A: Direct Tool Calling
    alt Direct Tool Calling
        rect rgb(220, 255, 220)
            Note over ClientApp, Server1: SCENARIO A: DIRECT TOOL CALLING
            ClientLLM->>+ClientApp: Request tool execution
            ClientApp->>+Server1: Execute specific tool
            Server1-->>-ClientApp: Return results
            ClientApp->>+ClientLLM: Process results
            ClientLLM-->>-ClientApp: Generate response
            ClientApp-->>-User: Display final answer
        end
    
    %% Scenario B: Feature Negotiation (VS Code style)
    else Feature Negotiation (VS Code style)
        rect rgb(255, 220, 220)
            Note over ClientApp, ServerLLM: SCENARIO B: FEATURE NEGOTIATION
            ClientLLM->>+ClientApp: Identify needed capabilities
            ClientApp->>+Server2: Negotiate features/capabilities
            Server2->>+ServerLLM: Request additional context
            ServerLLM-->>-Server2: Provide context
            Server2-->>-ClientApp: Return available features
            ClientApp->>+Server2: Call negotiated tools
            Server2-->>-ClientApp: Return results
            ClientApp->>+ClientLLM: Process results
            ClientLLM-->>-ClientApp: Generate response
            ClientApp-->>-User: Display final answer
        end
    end
```

## 🔐 Manfaat Praktis MCP

Berikut manfaat praktis menggunakan MCP:

- **Kebaruan**: Model dapat mengakses informasi terkini di luar data pelatihannya
- **Perluasan Kapabilitas**: Model dapat memanfaatkan alat khusus untuk tugas yang tidak dilatih sebelumnya
- **Mengurangi Halusinasi**: Sumber data eksternal memberikan dasar fakta
- **Privasi**: Data sensitif dapat tetap berada dalam lingkungan aman tanpa harus disematkan dalam prompt

## 📌 Poin Penting

Berikut poin penting dalam penggunaan MCP:

- **MCP** menstandarisasi cara model AI berinteraksi dengan alat dan data
- Mendorong **ekstensibilitas, konsistensi, dan interoperabilitas**
- MCP membantu **mengurangi waktu pengembangan, meningkatkan keandalan, dan memperluas kapabilitas model**
- Arsitektur client-server **memungkinkan aplikasi AI yang fleksibel dan dapat dikembangkan**

## 🧠 Latihan

Pikirkan tentang aplikasi AI yang ingin Anda bangun.

- Alat atau data eksternal apa yang bisa meningkatkan kapabilitasnya?
- Bagaimana MCP dapat membuat integrasi menjadi lebih sederhana dan lebih andal?

## Sumber Tambahan

- [MCP GitHub Repository](https://github.com/modelcontextprotocol)

## Apa Selanjutnya

Berikutnya: [Chapter 1: Core Concepts](/01-CoreConcepts/README.md)

**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berusaha untuk akurasi, harap diketahui bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang otoritatif. Untuk informasi penting, disarankan menggunakan terjemahan profesional oleh manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau salah tafsir yang timbul dari penggunaan terjemahan ini.