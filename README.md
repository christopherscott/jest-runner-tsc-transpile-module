# jest-runner-tsc-transpile-module

Reproducing an issue where recent PR to `jest-runner-tsc` caused it to stop type-checking files.

To repro:

```
yarn
yarn test
```

Expect: jest fails with TSC type error on index.ts file

Actual: jest passes

Setup to match instructions in jest-runner-tsc readme.

Relevant issues:
- original issue (builds are slow) https://github.com/azz/jest-runner-tsc/issues/5 
- PR for the fix: https://github.com/azz/jest-runner-tsc/pull/14
- What's the point? https://github.com/azz/jest-runner-tsc/issues/15
    - user points out that the fix actually stops reporting type errors (becuase it uses method `transpileModule`)
- transpileModule() does not generate diagnostics https://github.com/Microsoft/TypeScript/issues/4864
  - old issue where TypeScript team is responding to users who expect `transpileModule()` to report diagnostics, they explain why it's not feasible 
