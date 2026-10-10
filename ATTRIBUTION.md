# Attribution

This master skill bundles copies of third-party agent skills so the workflow can run without `npx skills add`. Original licenses still apply. Do not treat this package as relicensing those works.

| Bundled folder | Upstream | License |
| --- | --- | --- |
| `skills/expo-*`, `skills/eas-*` | [expo/skills](https://github.com/expo/skills) | MIT |
| `skills/mobile-design` | [RubenGlez/mobile-design](https://github.com/RubenGlez/mobile-design) | MIT |
| `skills/frontend-design` | [anthropics/skills](https://github.com/anthropics/skills) `skills/frontend-design` | Apache-2.0 (`LICENSE.txt`) |
| `skills/react-native-best-practices`, `skills/react-navigation` | [callstackincubator/agent-skills](https://github.com/callstackincubator/agent-skills) | MIT |
| `skills/react-native-testing` | Vendored inside Callstack agent-skills (RNTL guide) | See that folder |
| `skills/react-native-skills` | [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) `skills/react-native-skills` | MIT |
| `skills/theming`, `skills/local-build`, `skills/app-icon` | [code-with-beto/skills](https://github.com/code-with-beto/skills) | See upstream repo |
| `skills/design-studio` | Original to Monzer | — |
| `skills/quality` | Original to Monzer. Orchestrates the four quality jobs | — |
| `skills/qe/` | [RBraga01/Quality-Engineering-Skills](https://github.com/RBraga01/Quality-Engineering-Skills) (ISO audit, DFMEA, PFMEA, DVP, NCR, CAR, 5-Why, fishbone, 8D, PDCA, DMAIC) | MIT (`skills/qe/LICENSE`) |
| `skills/qa-testing` | [laurenceputra/agent-skills](https://github.com/laurenceputra/agent-skills) `skills/qa-testing` | MIT |
| `skills/critique-review` | [repath500/critique-review](https://github.com/repath500/critique-review) | MIT |
| `skills/sentry-react-native` | [getsentry/sentry-agent-skills](https://github.com/getsentry/sentry-agent-skills) `skills/sentry-react-native-sdk` | Apache-2.0 (declared in the skill) |
| `skills/amplitude-expo` | [amplitude/wizard](https://github.com/amplitude/wizard) `skills/integration/integration-expo` | MIT |
| `skills/push-notifications`, `camera-scan`, `maps-location`, `i18n-rtl` | Original to Monzer | — |
| `skills/expo-web-to-native` | [expo/skills](https://github.com/expo/skills) | MIT |
| `skills/upgrading-react-native` | [callstackincubator/agent-skills](https://github.com/callstackincubator/agent-skills) | MIT |
| `skills/maestro-mobile-testing` | [tovimx/maestro-mobile-testing-skill](https://github.com/tovimx/maestro-mobile-testing-skill) | MIT |
| `skills/react-native-accessibility` | [rushatgabhane/react-native-accessibility-skill](https://github.com/rushatgabhane/react-native-accessibility-skill) | MIT |
| `skills/masvs-checklist`, `secure-storage-audit`, `auth-assessment`, `network-security-check` | [dweinstein/mobile-security-skills](https://github.com/dweinstein/mobile-security-skills) (MASVS v2) | See upstream |
| `skills/secrets-scan`, `skills/prompt-injection-test` | [OWASP/secure-agent-playbook](https://github.com/OWASP/secure-agent-playbook) | CC-BY-4.0 |

Not bundled: TV, brownfield, App Clip, Expo DOM, Vercel hosting, Platano `ship`. OWASP full MASTG data pack is not copied (too large); use public MASVS/MASTG URLs from the checklist skill. AZANIR/qa-skills is GPL-3.0 and is not copied. Automotive-only methods (PPAP, IATF, VDA, gauge R&R) are not copied.

The M0–M10 product workflow, Golden Rule, and discovery deliverables are original to this master skill.
