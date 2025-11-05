---
layout: two-cols
layoutClass: gap-16
---

# Configuration

<div class="mt-2">

```js {1-9}
// config.mjs
import { getBuiltInRatings } from
  'web-codegen-scorer';

export default {
  skipInstall: true,
  displayName: 'agentic-coding-scorer',
  clientSideFramework: 'angular',
  sourceDirectory: 'project',
  ratings: [...getBuiltInRatings()],
  generationSystemPrompt:
    './<your-instructions>.md',
  executablePrompts:
    ['./example-prompts/**/*.md'],
}
```

</div>

::right::

<div class="mt-6">

**Usage:**

```bash
export GEMINI_API_KEY="..🤖.." && \
  web-codegen-scorer eval \
  --env=angular-example
```

</div>

<div class="mt-6">

**Report:**

```bash
web-codegen-scorer report
```

</div>

<div class="mt-6">

**Test manually:**

```bash
web-codegen-scorer run \
  --prompt=<generated-app> \
  --env=<path>
```

</div>

<div class="mt-6 text-sm opacity-70">

Playground: https://github.com/GregOnNet/angular-web-codegen-scorer-playground

</div>
