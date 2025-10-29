---
applyTo: "**/*.ps1"
---

# PowerShell Language-Specific Copilot Instructions

## Core Syntax & Operators
- Use `;` to chain commands (NOT `&&` which is bash)
- Use `-and`, `-or`, `-not` for logical operations
- Use `-eq`, `-ne`, `-gt`, `-lt`, `-ge`, `-le` for comparisons
- Use `-like`, `-match` for pattern matching
- Use `$()` for command substitution

## Variable & Parameter Handling
- Variables: `$variableName` (case-insensitive)
- Arrays: `$array = @("item1", "item2")`
- Hash tables: `$hash = @{key1="value1"; key2="value2"}`
- Splatting: `$params = @{Name="value"}; Command @params`

## Error Handling & Best Practices
- Always use `$ErrorActionPreference = "Stop"` for scripts
- Use `try/catch/finally` blocks for error handling
- Check `$?` for last command success status
- Use `Write-Error`, `Write-Warning`, `Write-Verbose` appropriately

## File & Path Operations
- Use `Join-Path` instead of string concatenation for paths
- Use `Test-Path` to check file/folder existence
- Use `Get-ChildItem` instead of `ls` or `dir`
- Use `Set-Location` instead of `cd`

## Common Commands (PowerShell 7 equivalents)
- `Get-Content` instead of `cat`
- `Set-Content` instead of `echo >`
- `Copy-Item` instead of `cp`
- `Remove-Item` instead of `rm`
- `Move-Item` instead of `mv`
- `New-Item` to create files/folders

## Command Chaining Examples
```powershell
# Correct PowerShell 7 chaining
mvn clean ; mvn package
Get-Process ; Get-Service

# Use pipeline for data flow
Get-ChildItem | Where-Object {$_.Extension -eq ".java"} | ForEach-Object {$_.Name}
```