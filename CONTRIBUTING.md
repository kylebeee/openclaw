# Contributing to OpenHearth

Welcome! OpenHearth is a group-native AI assistant for multi-party coordination.

## Quick Links

- **GitHub:** https://github.com/kylebeee/openhearth
- **Discord:** https://discord.gg/openhearth

## Maintainers

- **Kyle Breeding** — Creator & maintainer
  - GitHub: [@kylebeee](https://github.com/kylebeee)

## How to Contribute

1. **Bugs & small fixes** — Open a PR!
2. **New features / architecture** — Start a [GitHub Discussion](https://github.com/kylebeee/openhearth/discussions) or ask in Discord first
3. **Questions** — Discord #setup-help

## Before You PR

- Test locally with your OpenHearth instance
- Run tests: `pnpm build && pnpm check && pnpm test`
- Ensure CI checks pass
- Keep PRs focused (one thing per PR)
- Describe what & why

## Control UI Decorators

The Control UI uses Lit with **legacy** decorators (current Rollup parsing does not support
`accessor` fields required for standard decorators). When adding reactive fields, keep the
legacy style:

```ts
@state() foo = "bar";
@property({ type: Number }) count = 0;
```

The root `tsconfig.json` is configured for legacy decorators (`experimentalDecorators: true`)
with `useDefineForClassFields: false`. Avoid flipping these unless you are also updating the UI
build tooling to support standard decorators.

## AI-Assisted PRs Welcome

Built with AI tools? Just mark it in your PR description, note your testing level, and confirm you understand the code.

## Current Focus

- **Hearth system** — Group coordination, member identity, privacy layers
- **Stability** — Channel connection edge cases (WhatsApp/Telegram)
- **UX** — Onboarding wizard and error messages
- **Skills** — Visit [HearthHub](https://hearthub.com/) for community skills

Check the [GitHub Issues](https://github.com/kylebeee/openhearth/issues) for "good first issue" labels!

## Report a Vulnerability

We take security reports seriously. Report vulnerabilities at [GitHub Issues](https://github.com/kylebeee/openhearth/issues) or email **security@openhearth.ai**.

### Required in Reports

1. **Title**
2. **Severity Assessment**
3. **Impact**
4. **Affected Component**
5. **Technical Reproduction**
6. **Demonstrated Impact**
7. **Environment**
8. **Remediation Advice**
