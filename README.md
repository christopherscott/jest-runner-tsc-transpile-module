# jest-runner-tsc-transpile-module

Reproducing an issue where recent PR to `jest-runner-tsc` caused it to stop type-checking files.

Relevant issues:
1. original issue (builds are slow) https://github.com/azz/jest-runner-tsc/issues/5 
2. PR for the fix: https://github.com/azz/jest-runner-tsc/pull/14
3. What's the point? https://github.com/azz/jest-runner-tsc/issues/15
  - user points out that the fix in #2 actually stops reporting type errors (becuase it uses method `transpileModule`)
4. transpileModule() does not generate diagnostics https://github.com/Microsoft/TypeScript/issues/4864
  - old issue where TypeScript team is responding to users who expect `transpileModule()` to report diagnostics, they explain why it's not feasible 
