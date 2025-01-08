# TypeScript ANTLR4 Project Setup with Deno

This project provides a template for creating language tools using ANTLR4 and TypeScript, running on Deno.

## Prerequisites

- Deno 1.37.0 or higher
- Java Runtime Environment (for ANTLR4)
- TypeScript 5.0.0 or higher

## Project Structure

```
ts_antlr4/
├── grammar/               # ANTLR4 grammar files
│   └── MyLanguage.g4      # Main grammar definition
├── src/                   # TypeScript implementation
│   ├── parser/            # Generated parser files
│   ├── visitor/           # Custom visitor implementations
│   └── main.ts            # Main application entry point
├── scripts/               # Build and test scripts
│   ├── generate.ts        # Grammar generation script
│   └── test.ts            # Test runner
└── deno.json              # Deno configuration
```

## Setup Steps

1. Install Deno:
   ```bash
   curl -fsSL https://deno.land/x/install/install.sh | sh
   ```

2. Install ANTLR4:
   ```bash
   curl -O https://www.antlr.org/download/antlr-4.13.1-complete.jar
   ```

3. Create grammar file in `grammar/` directory:
   ```antlr4
   grammar MyLanguage;

   // Grammar rules here
   ```

4. Generate parser files:
   ```bash
   deno run --allow-read --allow-write scripts/generate.ts
   ```

5. Implement custom visitors in `src/visitor/`

6. Configure Deno in `deno.json`:
   ```json
   {
     "tasks": {
       "generate": "deno run --allow-read --allow-write scripts/generate.ts",
       "test": "deno test --allow-read --allow-net"
     }
   }
   ```

## Development Workflow

1. Edit grammar files in `grammar/`
2. Regenerate parser:
   ```bash
   deno task generate
   ```
3. Implement language processing in TypeScript
4. Run tests:
   ```bash
   deno task test
   ```

## AI Integration (Optional)

To enable AI-assisted development:

1. Add Cline configuration in `deno.json`:
   ```json
   {
     "cline": {
       "models": ["openai", "anthropic"],
       "context": "language-tooling"
     }
   }
   ```

2. Implement AI suggestions in visitor patterns

## Testing

The project includes a test framework for:
- Grammar validation
- Parser correctness
- Visitor implementation
- Language processing

Run all tests with:
```bash
deno test
```

## Documentation

Generate documentation with:
```bash
deno doc
```

## Deployment

Build standalone executable:
```bash
deno compile --output my-language-tool src/main.ts
