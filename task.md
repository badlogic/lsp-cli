# Package and Export Sourcemaps and Types
**Status:** InProgress
**Agent PID:** 6325

## Original Todo
also package and export the sourcemaps and types so other apps can reuse them

## Description
We need to enhance the lsp-cli build process to generate and export TypeScript declaration files (.d.ts) and sourcemaps (.js.map) so that other applications can use lsp-cli as a library with full type support and debugging capabilities. This involves modifying the build configuration to generate these artifacts and updating package.json to properly expose them. Additionally, we'll create a library entry point separate from the CLI to expose the core functionality programmatically.

## Implementation Plan
To package and export sourcemaps and types for lsp-cli:

- [ ] Create library entry point src/lib.ts that exports core classes and types (LanguageClient, ServerManager, Logger, all types from types.ts)
- [ ] Update tsconfig.json to enable declaration file generation with `"declaration": true` and `"declarationMap": true`
- [ ] Modify build script to use TypeScript compiler (tsc) for generating declaration files alongside esbuild
- [ ] Update esbuild command to generate sourcemaps with `--sourcemap` flag
- [ ] Create separate build outputs: dist/cli.js for CLI and dist/lib.js for library usage
- [ ] Update package.json with proper exports field for dual CLI/library usage and types field pointing to dist/lib.d.ts
- [ ] Add dist/**/*.d.ts and dist/**/*.js.map to files array in package.json to include in published package
- [ ] Test that types and sourcemaps work correctly when importing the package

## Notes
[Implementation notes]