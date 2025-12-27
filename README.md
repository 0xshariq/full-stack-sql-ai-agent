# SQL AI Agent 🤖

A powerful full-stack AI agent that enables natural language querying of SQL databases. Built with Next.js, OpenAI, and Turso (LibSQL), this application converts conversational queries into SQL and returns results in a user-friendly format.

## 🌟 Features

- **Natural Language to SQL**: Ask questions in plain English, get SQL results
- **Real-time Streaming**: Responses stream in real-time using AI SDK
- **Database Schema Awareness**: AI understands your database structure
- **Safe Query Execution**: Read-only SQL queries (SELECT only)
- **Modern UI**: Clean, responsive interface with dark mode support
- **Tool-based Architecture**: Modular AI tools for schema inspection and query execution

## 🏗️ Tech Stack

- **Frontend**: Next.js 16.1.1, React 19, TypeScript
- **AI/LLM**: OpenAI GPT-5-nano, Vercel AI SDK
- **Database**: Turso (LibSQL) - Serverless SQLite
- **ORM**: Drizzle ORM
- **Styling**: Tailwind CSS 4
- **Type Safety**: Zod for runtime validation

## 📁 Project Structure

```
sql-ai-agent/
├── src/
│   ├── app/
│   │   ├── api/chat/route.ts    # Chat API endpoint with AI tools
│   │   ├── page.tsx             # Main chat interface
│   │   ├── layout.tsx           # App layout
│   │   └── globals.css          # Global styles
│   └── db/
│       ├── db.ts                # Database client setup
│       ├── schema.ts            # Drizzle schema definitions
│       └── db.seed.ts           # Database seeding script
├── drizzle.config.ts            # Drizzle configuration
├── package.json                 # Dependencies
└── README.md                    # This file
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- pnpm (recommended) or npm
- Turso account ([sign up](https://turso.tech))

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/0xshariq/full-stack-sql-ai-agent.git
   cd sql-ai-agent
   ```

2. **Install dependencies**

   ```bash
   pnpm install
   ```

3. **Set up environment variables**

   Create a `.env` file in the root directory:

   ```env
   TURSO_DATABASE_URL=your_turso_database_url
   TURSO_AUTH_TOKEN=your_turso_auth_token
   OPENAI_API_KEY=your_openai_api_key
   ```

4. **Push database schema**

   ```bash
   pnpm drizzle-kit push
   ```

5. **Seed the database (optional)**

   ```bash
   pnpm tsx src/db/db.seed.ts
   ```

6. **Run the development server**

   ```bash
   pnpm dev
   ```

7. **Open your browser**

   Navigate to [http://localhost:3000](http://localhost:3000)

## 💡 Usage Examples

Try asking questions like:

- "Show me all products in the Electronics category"
- "What are the top 5 best-selling products?"
- "Show sales by region"
- "Which products are low in stock?"
- "What's the total revenue from the North region?"

## 🛠️ How It Works

1. **User Input**: User types a natural language question
2. **AI Processing**: OpenAI GPT processes the query with access to two tools:
   - `schema` tool: Retrieves database schema
   - `db` tool: Executes SQL queries
3. **Query Generation**: AI generates appropriate SQL SELECT query
4. **Execution**: Query runs against Turso database
5. **Response**: Results stream back to the user interface

## 📊 Database Schema

The application includes two main tables:

### Products

- `id`: Auto-increment primary key
- `name`: Product name
- `category`: Product category
- `price`: Product price
- `stock`: Current stock level
- `created_at`: Timestamp

### Sales

- `id`: Auto-increment primary key
- `product_id`: Foreign key to products
- `quantity`: Quantity sold
- `total_amount`: Total sale amount
- `sale_date`: Sale timestamp
- `customer_name`: Customer name
- `region`: Sales region

## 🔒 Security Features

- **Query Restrictions**: Only SELECT queries allowed
- **Schema Validation**: Zod schemas for input validation
- **Environment Variables**: Sensitive data stored securely
- **Read-only Operations**: No data modification capabilities

## 🚀 Deployment

### Deploy on Vercel

1. Push your code to GitHub
2. Import project in [Vercel](https://vercel.com)
3. Add environment variables
4. Deploy!

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/0xshariq/full-stack-sql-ai-agent)

## 📝 Scripts

```bash
pnpm dev          # Start development server
pnpm build        # Build for production
pnpm start        # Start production server
pnpm lint         # Run ESLint
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/)
- [Vercel AI SDK](https://sdk.vercel.ai/)
- [Turso](https://turso.tech/)
- [Drizzle ORM](https://orm.drizzle.team/)
- [OpenAI](https://openai.com/)

## 📞 Support

For questions or issues, please open an issue on GitHub.

---

Built with ❤️ by [0xshariq](https://github.com/0xshariq)
