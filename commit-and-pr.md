# Commit Message

```
feat: improve CLI logging 

- Add LogLevel enum with normal and verbose levels
- Replace direct print statements with structured logging functions
- Default to minimal output, use --verbose flag for detailed logs
- Consolidate log output through centralized log utility

Fixes #312
```

# Pull Request

## Title
feat: improve CLI logging with verbose flag

## Description

### Summary
Improves the Slang CLI logging system to reduce console output clutter by making verbose logging opt-in via the `--verbose` flag, addressing issue #312.

### Changes
- **New logging system**: Added `slang/lib/src/utils/log.dart` with structured logging levels
- **Default behavior**: Changed from verbose-by-default to minimal output showing only essential info and errors
- **Verbose flag**: Added `--verbose` flag support to enable detailed logging (previous default behavior)
- **Consistent output**: Replaced scattered `print()` calls with centralized logging functions (`log.info()`, `log.verbose()`, `log.error()`)

### Breaking Changes
- **CLI output**: Default output is now more minimal. Users who want the previous verbose behavior need to use the `--verbose` flag

### Test Plan
- [ ] Verify default CLI output shows only essential information
- [ ] Test `--verbose` flag enables detailed logging output
- [ ] Confirm error messages still display properly
- [ ] Test watch mode output formatting
- [ ] Verify all runner modes work with both logging levels

### Files Changed
- `slang/bin/slang.dart` - Updated main CLI logic with log levels
- `slang/lib/src/builder/builder/slang_file_collection_builder.dart` - Replaced prints with structured logging  
- `slang/lib/src/builder/model/raw_config.dart` - Updated config printing to use verbose logging
- `slang/lib/src/runner/stats.dart` - Updated stats output to use info logging
- `slang/lib/src/utils/log.dart` - **New file** containing logging utilities

Closes #312