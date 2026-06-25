---
theme: seriph
title: "Flip the Switch: Feature Flags and the Power of Open Standards"
info: |
  Flip the Switch: Feature Flags and the Power of Open Standards.
  Simon Schrottner — OpenFeature maintainer, CNCF Ambassador.
author: Simon Schrottner
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
mdc: true
fonts:
  sans: Inter
  mono: JetBrains Mono
addons:
  - slidev-addon-qrcode
layout: section
---

# Flip the Switch

## Feature Flags and the Power of Open Standards

<div class="pt-8 opacity-90 text-sm space-y-1">
  <div>Simon Schrottner · OpenFeature maintainer · CNCF Ambassador</div>
  <div><carbon:email class="inline"/> simon@schrottner.at &nbsp;·&nbsp;
       <carbon:link class="inline"/> <a href="https://schrottner.at" target="_blank">schrottner.at</a> &nbsp;·&nbsp;
       <carbon:logo-github class="inline"/> aepfli &nbsp;·&nbsp;
       <carbon:logo-linkedin class="inline"/> in/aepfli</div>
</div>

<!--
  Narrative rhythm (do not break):
    Hook (Knight Capital) → Who I am → What flags buy you → The trap (lock-in)
    → Act 2: Not a new problem — OpenTelemetry (merge) · Kubernetes (conformance) · the lesson
    → Act 3: OpenFeature — born open from day one (the contrast) → how it works (provider + context)
    → Act 4: What an open standard unlocks — ecosystem · room for startups · adopters
    → Act 5: What it takes to build a standard in the open — the hard, human part
    → Take-aways → Community CTA
-->

---
layout: section
---

# How *not* to do Feature Flags

A cautionary tale: Knight Capital Group, August 2012.

---
layout: image
image: /img/knight_capital.webp
---

---
layout: default
---

# What happened

<v-clicks>

- Lost **half a billion USD**
- ... in **one hour**
- ... due to a **feature flag**
- ... only deployed to **7 of 8 servers**
- ... they **repurposed**

</v-clicks>

<div class="abs-br m-6 flex items-end gap-2">
  <a href="https://blog.statsig.com/how-to-lose-half-a-billion-dollars-with-bad-feature-flags-ccebb26adeec" target="_blank" class="text-xs opacity-60 hover:opacity-100 text-right leading-tight pb-1 !text-inherit">
    <div>statsig.com — how to lose half a billion dollars</div>
    <div class="font-mono text-[10px] opacity-80 mt-0.5">blog.statsig.com</div>
  </a>
  <div class="bg-white p-1 rounded dark:invert">
    <QRCode data="https://blog.statsig.com/how-to-lose-half-a-billion-dollars-with-bad-feature-flags-ccebb26adeec" :width="90" :height="90" :margin="2" />
  </div>
</div>

---
layout: image-right
image: /img/simon.jpg
---

# Who am I?

**Simon Schrottner**

<div class="grid grid-cols-3 gap-3 mt-6">
  <div class="rounded border border-gray-200 p-3 text-center flex flex-col items-center justify-between">
    <div class="h-14 w-full flex items-center justify-center bg-white rounded p-2">
      <img src="/img/openfeature-horizontal-black.svg" class="max-h-9 object-contain" />
    </div>
    <div class="text-xs mt-3">OpenFeature Maintainer</div>
  </div>
  <div class="rounded border border-gray-200 p-3 text-center flex flex-col items-center justify-between">
    <div class="h-14 w-full flex items-center justify-center bg-white rounded p-2">
      <img src="/img/cncf-ambassador-color.svg" class="max-h-12 object-contain" />
    </div>
    <div class="text-xs mt-3">CNCF Ambassador</div>
  </div>
  <div class="rounded border border-gray-200 p-3 text-center flex flex-col items-center justify-between">
    <div class="h-14 w-full flex items-center justify-center bg-white rounded p-2">
      <img src="/img/logos/aaif-ambassador.png" class="max-h-12 object-contain" />
    </div>
    <div class="text-xs mt-3">AAIF Ambassador</div>
  </div>
</div>

<div class="pt-4 flex items-center gap-2 text-sm opacity-85">
  <img src="/img/logos/flagsmith.svg" class="h-4 object-contain dark:invert"/>
  <span>Fractional Developer Advocate @ Flagsmith</span>
</div>

<div class="pt-2 text-sm opacity-70">Open Source enthusiast — I help build a standard in the open.</div>

<div class="pt-6 text-xs opacity-70 space-y-1">
  <div><carbon:email class="inline"/> simon@schrottner.at &nbsp;·&nbsp; <carbon:link class="inline"/> <a href="https://schrottner.at" target="_blank">schrottner.at</a></div>
  <div><carbon:logo-github class="inline"/> aepfli &nbsp; <carbon:logo-linkedin class="inline"/> in/aepfli</div>
  <div>🦋 @aepfli.bsky.social</div>
</div>

---
layout: default
---

# Where we're going

<div class="grid grid-cols-3 gap-6 mt-10 items-stretch">

<v-clicks>

<div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
  <div class="text-3xl opacity-40 leading-none">1</div>
  <div class="text-lg font-semibold">The switch & the trap</div>
  <div class="text-sm opacity-70">What flags buy you — and the lock-in nobody warns you about.</div>
</div>

<div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
  <div class="text-3xl opacity-40 leading-none">2</div>
  <div class="text-lg font-semibold">Open standards</div>
  <div class="text-sm opacity-70">How OpenTelemetry & Kubernetes solved the same problem — and how OpenFeature did it differently.</div>
</div>

<div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
  <div class="text-3xl opacity-40 leading-none">3</div>
  <div class="text-lg font-semibold">What it unlocks</div>
  <div class="text-sm opacity-70">Room for new ideas, new tools, new companies — and what it takes to build a standard in the open.</div>
</div>

</v-clicks>

</div>

---
layout: section
---

# The Switch

## What a feature flag actually buys you

---
layout: statement
---

Feature flags <span v-mark.highlight.yellow="1">enable, disable, or change behavior</span> of features in a product or service <span v-mark.highlight.yellow="2">at runtime</span> — <span v-mark.highlight.yellow="3">without modifying the source code</span>.

---
layout: default
---

# Coordinate & Target

<div class="grid grid-cols-3 gap-6 mt-8 items-stretch">
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:time class="text-5xl opacity-70"/>
    <div class="font-bold text-lg">Synchronized rollouts</div>
    <div class="text-sm opacity-70">ship a new feature to every service at the same moment, without coordinating deploys</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:chart-multi-line class="text-5xl opacity-70"/>
    <div class="font-bold text-lg">A/B experiments</div>
    <div class="text-sm opacity-70">serve two variants, measure which wins, close the loop with data</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:user-multiple class="text-5xl opacity-70"/>
    <div class="font-bold text-lg">Targeted release</div>
    <div class="text-sm opacity-70">beta testers, enterprise tier, a single region — each sees a different flag value</div>
  </div>
</div>

---
layout: default
---

# Ship with more confidence

<div class="grid grid-cols-3 gap-6 mt-8 items-stretch">
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:launch class="text-5xl opacity-70"/>
    <div class="font-bold text-lg">Deploy ≠ release</div>
    <div class="text-sm opacity-70">ship code dark; turn it on later without redeploying</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:stop-outline class="text-5xl opacity-70"/>
    <div class="font-bold text-lg">Kill switch</div>
    <div class="text-sm opacity-70">disable a bad feature in seconds, no revert, no rebuild</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:chart-line class="text-5xl opacity-70"/>
    <div class="font-bold text-lg">Progressive rollout</div>
    <div class="text-sm opacity-70">1% → 10% → 100%, target a region, a tier, a cohort</div>
  </div>
</div>

<div class="text-sm opacity-70 text-center mt-10">
  Toggle a feature. Decouple a release. That part is <em>true</em>.
</div>

---
layout: section
---

# The Trap

## The part nobody tells you

---
layout: default
---

# You build on someone's SDK

<div class="text-sm opacity-70">It starts as a quick win. It ends as a dependency.</div>

<div class="grid grid-cols-3 gap-6 mt-8 items-stretch">

  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:rocket class="text-5xl opacity-70" />
    <div class="font-bold text-lg">Quick win</div>
    <div class="text-sm opacity-70">
      Pick a vendor, drop in their SDK, ship next week. Targeting, a UI, rollouts — all out of the box.
    </div>
  </div>

  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:plug class="text-5xl opacity-70" />
    <div class="font-bold text-lg">Bespoke everywhere</div>
    <div class="text-sm opacity-70">
      Their client library, their API, their semantics — woven through <strong>every call site</strong> in your codebase.
    </div>
  </div>

  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:locked class="text-5xl opacity-70" />
    <div class="font-bold text-lg">Locked in</div>
    <div class="text-sm opacity-70">
      Switching vendors means rewriting all of it. The cost of leaving is now your problem.
    </div>
  </div>

</div>

---
layout: statement
---

# Then the ground shifts

<div class="grid grid-cols-3 gap-6 mt-10 max-w-4xl mx-auto">
  <div class="p-5 rounded-lg border border-gray-300">
    <carbon:money class="text-4xl opacity-70 mb-2"/>
    <div class="font-bold">Prices go up</div>
    <div class="text-sm opacity-70 mt-1">The bill triples at renewal. What are you going to do — rewrite?</div>
  </div>
  <div class="p-5 rounded-lg border border-gray-300">
    <carbon:network-3 class="text-4xl opacity-70 mb-2"/>
    <div class="font-bold">They get acquired</div>
    <div class="text-sm opacity-70 mt-1">New owner, new roadmap, new priorities. Maybe not yours.</div>
  </div>
  <div class="p-5 rounded-lg border border-gray-300">
    <carbon:fade class="text-4xl opacity-70 mb-2"/>
    <div class="font-bold">They stop caring</div>
    <div class="text-sm opacity-70 mt-1">The product stalls. Support slows. You're stuck on it anyway.</div>
  </div>
</div>

<div class="text-lg opacity-80 mt-10">
  The toggle was easy. <b>The lock-in is the bill.</b>
</div>

---
layout: default
---

# And lock-in is only half of it

<div class="text-sm opacity-70 -mt-2 mb-6">Across a company, feature flagging is rarely <em>one</em> thing. Different teams, different eras, different tools — homegrown here, one vendor there, two more services over. Nothing standardized.</div>

<div class="grid grid-cols-3 gap-6 items-stretch">
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:view-off class="text-5xl opacity-70"/>
    <div class="font-bold text-lg">You can't see across it</div>
    <div class="text-sm opacity-70">No single picture of what's on, off, or rolling out. Every team's flags are a black box to everyone else.</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:analytics class="text-5xl opacity-70"/>
    <div class="font-bold text-lg">You can't get insight</div>
    <div class="text-sm opacity-70">Which flags are live? Who's affected? What's safe to remove? Per-tool, maybe — across the org, never.</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 text-center flex flex-col items-center gap-3 h-full">
    <carbon:help class="text-5xl opacity-70"/>
    <div class="font-bold text-lg">You can't understand the system</div>
    <div class="text-sm opacity-70">To know how it behaves, someone has to read every service. The people who need the answer most often can't.</div>
  </div>
</div>

<div class="text-base opacity-85 text-center mt-8 max-w-3xl mx-auto">
  We want to <b>observe</b> — to get insight and understand the system. That's not the same as running <em>observability</em>, and it shouldn't require knowing the code.
</div>

---
layout: image
image: /img/breaks/frost-fence.jpg
---

---
layout: section
---

# This is not a new problem

## Other communities have been here before

---
layout: default
---

# OpenTelemetry: merge instead of fight

<div class="absolute top-8 right-8 opacity-80">
  <logos:opentelemetry class="h-8"/>
</div>

<div class="text-sm opacity-70 -mt-2 mb-6">Two competing observability projects looked at the fragmentation they'd created — and joined forces.</div>

<div class="grid grid-cols-2 gap-6 items-stretch">
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
    <div class="font-bold text-lg">The fragmentation</div>
    <div class="text-sm opacity-80"><strong>OpenTracing</strong> and <strong>OpenCensus</strong> — two standards solving the same problem. Instrument for one, you couldn't use the other. Vendors and users had to pick a side.</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
    <div class="font-bold text-lg">The merge (2019)</div>
    <div class="text-sm opacity-80">Instead of competing to the death, they <strong>merged into OpenTelemetry</strong>. Today it's the second-most-active CNCF project — the default way the industry does telemetry.</div>
  </div>
</div>

<div class="text-sm opacity-70 text-center mt-8">
  Standards didn't just solve a technical problem. They changed how rivals <em>collaborated</em>.
</div>

---
layout: default
---

# Kubernetes: a common baseline

<div class="text-sm opacity-70 -mt-2 mb-6">A fractured container ecosystem got one thing everyone could agree to certify against.</div>

<div class="grid grid-cols-2 gap-6 items-stretch">
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
    <div class="font-bold text-lg">Conformance</div>
    <div class="text-sm opacity-80">The <strong>Certified Kubernetes</strong> program defines a baseline every distribution must pass. Same API, same behavior — wherever it runs.</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
    <div class="font-bold text-lg">100+ certified distributions</div>
    <div class="text-sm opacity-80">Cloud providers, on-prem vendors, startups — all certify against the same spec. Your workload moves between them <strong>without a rewrite</strong>.</div>
  </div>
</div>

<div class="text-sm opacity-70 text-center mt-8">
  A shared baseline turned a zero-sum fight into a market everyone could build on.
</div>

---
layout: statement
---

Standards don't just solve technical problems.

<div class="text-3xl font-bold mt-6">They change how communities collaborate.</div>

---
layout: image
image: /img/breaks/mist-mountain.jpg
---

---
layout: center
---

<span class="sr-only">OpenFeature</span>

<div class="flex flex-col items-center gap-6 mt-4">
  <img src="/img/openfeature-horizontal-black.svg" class="h-24 dark:invert"/>
  <div class="text-xl opacity-80 text-center max-w-2xl">A vendor-neutral, community-driven standard for feature flagging</div>
  <div class="flex flex-col items-center gap-1 mt-4">
    <img src="/img/cncf-incubating-color.svg" class="h-20 dark:hidden"/>
    <img src="/img/cncf-incubating-white.svg" class="h-20 hidden dark:block"/>
    <div class="text-xs opacity-60">CNCF Incubating project</div>
  </div>
</div>

---
layout: statement
---

OpenFeature is an <span v-mark.highlight.yellow="1">open specification</span> that provides a <span v-mark.highlight.yellow="2">vendor-agnostic, community-driven API</span> for feature flagging that works with your favorite feature flag management tool.

<div class="abs-br m-6 flex items-end gap-2">
  <a href="https://openfeature.dev/docs/reference/intro" target="_blank" class="text-xs opacity-80 hover:opacity-100 text-right leading-tight pb-1 !text-inherit">
    <div>OpenFeature Specification intro</div>
    <div class="font-mono text-[10px] opacity-80 mt-0.5">openfeature.dev/docs/reference/intro</div>
  </a>
  <div class="bg-white p-1 rounded dark:invert">
    <QRCode data="https://openfeature.dev/docs/reference/intro" :width="90" :height="90" :margin="2" />
  </div>
</div>

---
layout: default
---

# The same bet — but born open

<div class="text-sm opacity-70 -mt-2 mb-8">OpenTelemetry had to <em>merge</em> two rivals to undo the fragmentation. OpenFeature skipped the fight — competing vendors collaborated <strong>before</strong> anyone shipped a rival standard.</div>

<div class="grid grid-cols-4 gap-4">

  <div class="flex flex-col items-center text-center gap-2 p-4 rounded border border-gray-300">
    <carbon:bullhorn class="text-3xl opacity-80"/>
    <div class="text-lg font-semibold">May 2022</div>
    <div class="text-sm opacity-80">Announced at <strong>KubeCon Valencia</strong> — a coalition of flag-vendor engineers inviting the community in</div>
  </div>

  <div class="flex flex-col items-center text-center gap-2 p-4 rounded border border-gray-300">
    <carbon:idea class="text-3xl opacity-80"/>
    <div class="text-lg font-semibold">June 2022</div>
    <div class="text-sm opacity-80">Into the <strong>CNCF Sandbox</strong> — neutral, open governance from the start</div>
  </div>

  <div class="flex flex-col items-center text-center gap-2 p-4 rounded border border-gray-300">
    <carbon:growth class="text-3xl opacity-80"/>
    <div class="text-lg font-semibold">Nov 2023</div>
    <div class="text-sm opacity-80">Promoted to <strong>CNCF Incubating</strong> — stable spec, 1.0 SDKs across major languages</div>
  </div>

  <div class="flex flex-col items-center text-center gap-2 p-4 rounded border border-gray-300">
    <carbon:collaborate class="text-3xl opacity-80"/>
    <div class="text-lg font-semibold">Today</div>
    <div class="text-sm opacity-80">A <strong>multi-vendor</strong> standard — competitors shipping providers side by side</div>
  </div>

</div>

<div class="text-sm opacity-70 text-center mt-8">
  No merge needed. The collaboration <em>was</em> the starting point.
</div>

---
layout: center
---

# How it works: Providers

<img src="/img/architecture.png" class="mx-auto max-h-[55vh]"/>

<div class="text-sm opacity-70 text-center mt-2">Your code talks to one Evaluation API. A Provider adapts it to whichever tool you use.</div>

<div class="abs-br m-6 flex items-end gap-2">
  <a href="https://openfeature.dev/docs/reference/intro#what-is-openfeature" target="_blank" class="text-xs opacity-60 hover:opacity-100 text-right leading-tight pb-1 !text-inherit">
    <div>OpenFeature provider architecture</div>
    <div class="font-mono text-[10px] opacity-80 mt-0.5">openfeature.dev/docs/reference/intro#what-is-openfeature</div>
  </a>
  <div class="bg-white p-1 rounded dark:invert">
    <QRCode data="https://openfeature.dev/docs/reference/intro#what-is-openfeature" :width="90" :height="90" :margin="2" />
  </div>
</div>

---
layout: default
---

# How an evaluation works

<div class="text-sm opacity-70 -mt-2 mb-4">
  Register a provider <b>once, at startup</b>. After that, every evaluation is the same shape — in any language, against any vendor.
</div>

````md magic-move {lines: true}
```java {1-2}
var api = OpenFeatureAPI.getInstance();
api.setProviderAndWait(new FlagdProvider(config));
```
```java {4}
var api = OpenFeatureAPI.getInstance();
api.setProviderAndWait(new FlagdProvider(config));

var client = api.getClient();
```
```java {5}
var api = OpenFeatureAPI.getInstance();
api.setProviderAndWait(new FlagdProvider(config));

var client = api.getClient();
boolean on = client.getBooleanValue("v2_enabled", false);
```
```java {2}
var api = OpenFeatureAPI.getInstance();
api.setProviderAndWait(new FlagsmithProvider(flagsmithConfig));

var client = api.getClient();
boolean on = client.getBooleanValue("v2_enabled", false);
```
````

<div class="grid grid-cols-4 gap-3 mt-6 text-center text-xs">
  <div class="p-2 rounded border border-gray-200"><div class="font-bold">1 · Provider</div><div class="opacity-70">connect a flag source</div></div>
  <div class="p-2 rounded border border-gray-200"><div class="font-bold">2 · Client</div><div class="opacity-70">cheap, scoped handle</div></div>
  <div class="p-2 rounded border border-gray-200"><div class="font-bold">3 · Evaluate</div><div class="opacity-70">name + default → value</div></div>
  <div class="p-2 rounded border border-orange-400/70"><div class="font-bold">↺ Swap</div><div class="opacity-70">only the provider line</div></div>
</div>

<div class="text-xs opacity-60 mt-4">
  <carbon:document class="inline-block align-middle" /> The default is mandatory — your code always gets a value back. ~130 providers in the ecosystem:
  <a href="https://openfeature.dev/ecosystem" target="_blank">openfeature.dev/ecosystem</a>
</div>

<div class="abs-br m-6 flex items-end gap-2">
  <a href="https://openfeature.dev/ecosystem" target="_blank" class="text-xs opacity-60 hover:opacity-100 text-right leading-tight pb-1 !text-inherit">
    <div>Provider ecosystem</div>
    <div class="font-mono text-[10px] opacity-80 mt-0.5">openfeature.dev/ecosystem</div>
  </a>
  <div class="bg-white p-1 rounded dark:invert">
    <QRCode data="https://openfeature.dev/ecosystem" :width="90" :height="90" :margin="2" />
  </div>
</div>

---
layout: default
---

# It still does the real work

<div class="text-sm opacity-70 -mt-2 mb-4">Vendor-neutral doesn't mean lowest-common-denominator. Pass context, get dynamic, per-subject evaluation.</div>

```java {1-5|6-7|9-10}
Map<String, Value> attrs = new HashMap<>();
attrs.put("email",
    new Value(session.getAttribute("email")));
attrs.put("region",
    new Value("eu"));
EvaluationContext reqCtx =
    new ImmutableContext(targetingKey, attrs);

boolean on =
    client.getBooleanValue("v2_enabled", false, reqCtx);
```

<div class="text-xs opacity-60 mt-4">
  <carbon:information class="inline-block align-middle" /> Per-user, per-region, per-tenant targeting and percentage rollouts — the standard defines the <em>input</em>, the provider does the evaluation.
</div>

---
layout: fact
---

# One API. Any vendor.

Swap providers without rewriting · target dynamically · never welded to one company again.

<blockquote class="text-sm opacity-70 italic mt-8 max-w-3xl mx-auto border-l-4 border-gray-300 pl-4 text-left">
  Providers are responsible for performing flag evaluations. They provide an <b>abstraction between the underlying flag management system and the OpenFeature SDK</b>.
</blockquote>

<div class="abs-br m-6 flex items-end gap-2">
  <a href="https://openfeature.dev/docs/reference/concepts/provider" target="_blank" class="text-xs opacity-60 hover:opacity-100 text-right leading-tight pb-1 !text-inherit">
    <div>Providers — concept docs</div>
    <div class="font-mono text-[10px] opacity-80 mt-0.5">openfeature.dev/docs/reference/concepts/provider</div>
  </a>
  <div class="bg-white p-1 rounded dark:invert">
    <QRCode data="https://openfeature.dev/docs/reference/concepts/provider" :width="90" :height="90" :margin="2" />
  </div>
</div>

---
layout: image
image: /img/breaks/spring-blossoms.jpg
---

---
layout: section
---

# What an open standard unlocks

## Less friction → more room to build

---
layout: default
---

# A neutral base everyone can build on

<div class="text-sm opacity-70 -mt-2 mb-6">When the integration surface is shared, the ecosystem stops re-inventing it — and starts extending it.</div>

<div class="grid grid-cols-2 gap-5">

  <div class="p-5 rounded-lg border border-gray-200 shadow-sm flex flex-col gap-2">
    <div class="flex items-center gap-3"><carbon:plug class="text-3xl opacity-70"/><div class="font-bold text-lg">~130 providers</div></div>
    <div class="text-sm opacity-80">Commercial and open source, all speaking one API. Write one provider, instantly work with every OpenFeature SDK.</div>
  </div>

  <div class="p-5 rounded-lg border border-gray-200 shadow-sm flex flex-col gap-2">
    <div class="flex items-center gap-3"><carbon:cloud class="text-3xl opacity-70"/><div class="font-bold text-lg">flagd</div></div>
    <div class="text-sm opacity-80">A free, open-source reference provider — born <em>because</em> the standard existed. No vendor required to get started.</div>
  </div>

  <div class="p-5 rounded-lg border border-gray-200 shadow-sm flex flex-col gap-2">
    <div class="flex items-center gap-3"><carbon:api class="text-3xl opacity-70"/><div class="font-bold text-lg">OFREP</div></div>
    <div class="text-sm opacity-80">A standard HTTP protocol for evaluation. Any backend can serve any client — a whole new integration shape, opened up by the spec.</div>
  </div>

  <div class="p-5 rounded-lg border border-gray-200 shadow-sm flex flex-col gap-2">
    <div class="flex items-center gap-3"><carbon:terminal class="text-3xl opacity-70"/><div class="font-bold text-lg">CLI & tooling</div></div>
    <div class="text-sm opacity-80">Type-safe codegen, manifests, testing tools — community-built on top of a stable contract.</div>
  </div>

</div>

---
layout: default
---

# Room for new ideas — and new companies

<div class="text-sm opacity-70 -mt-2 mb-6">Lock-in protects incumbents. A standard lowers the cost of switching — so vendors have to compete on <strong>value</strong>, not on how hard they are to leave.</div>

<div class="grid grid-cols-3 gap-6 items-stretch">
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
    <carbon:rocket class="text-4xl opacity-70"/>
    <div class="font-bold text-lg">Lower barrier to entry</div>
    <div class="text-sm opacity-80">A new startup ships <em>one provider</em> and is instantly compatible with every OpenFeature app. No SDK to evangelize, no rip-and-replace to win a customer.</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
    <carbon:application class="text-4xl opacity-70"/>
    <div class="font-bold text-lg">Compete on the product</div>
    <div class="text-sm opacity-80">UI, targeting, analytics, price — the things that actually matter. Customers can leave, so vendors have to be worth staying for.</div>
  </div>
  <div class="rounded-lg border border-gray-200 shadow-sm p-6 flex flex-col gap-2 h-full">
    <carbon:idea class="text-4xl opacity-70"/>
    <div class="font-bold text-lg">Mix and experiment</div>
    <div class="text-sm opacity-80">Open-source platforms like <strong>Flagsmith</strong>, multi-provider setups, edge evaluation — combinations that simply weren't worth building before.</div>
  </div>
</div>

<div class="text-sm opacity-70 text-center mt-8">
  The standard isn't a constraint on the market. It's the floor the market builds on.
</div>

---
layout: image
image: /img/breaks/ruin-archway.jpg
---

---
layout: section
---

# Building a standard in the open

## The part that's harder than the code

---
layout: default
---

# The code is the easy part

<div class="text-sm opacity-70 -mt-2 mb-6">Writing an SDK is a solved problem. Getting competitors to agree on what it should <em>say</em> is the work.</div>

<div class="grid grid-cols-2 gap-5">

  <div class="p-5 rounded-lg border border-gray-200 shadow-sm flex flex-col gap-2">
    <div class="flex items-center gap-3"><carbon:partnership class="text-3xl opacity-70"/><div class="font-bold text-lg">Rivals at one table</div></div>
    <div class="text-sm opacity-80">Vendors who compete for the same customers, agreeing on a shared contract. That takes trust, patience, and a neutral room.</div>
  </div>

  <div class="p-5 rounded-lg border border-gray-200 shadow-sm flex flex-col gap-2">
    <div class="flex items-center gap-3"><carbon:scales class="text-3xl opacity-70"/><div class="font-bold text-lg">Neutral governance</div></div>
    <div class="text-sm opacity-80">A CNCF home, open meetings, public decisions — so no single company can steer the spec to its own advantage.</div>
  </div>

  <div class="p-5 rounded-lg border border-gray-200 shadow-sm flex flex-col gap-2">
    <div class="flex items-center gap-3"><carbon:document class="text-3xl opacity-70"/><div class="font-bold text-lg">Spec first, code second</div></div>
    <div class="text-sm opacity-80">Write the contract, then nine languages implement it. The spec is the source of truth — every SDK has to conform.</div>
  </div>

  <div class="p-5 rounded-lg border border-gray-200 shadow-sm flex flex-col gap-2">
    <div class="flex items-center gap-3"><carbon:checkmark-outline class="text-3xl opacity-70"/><div class="font-bold text-lg">Conformance & trust</div></div>
    <div class="text-sm opacity-80">Shared test suites and a transparent process keep "compatible" honest — the thing that makes the promise real.</div>
  </div>

</div>

---
layout: default
---

# Standards aren't free

<div class="text-sm opacity-70 -mt-2 mb-6">An honest ledger. Worth it — but go in with eyes open.</div>

<div class="grid grid-cols-2 gap-6 items-start">

<div class="p-5 rounded-lg border border-green-500/50 shadow-sm">
  <div class="flex items-center gap-2 font-bold text-lg mb-3"><carbon:thumbs-up class="opacity-80"/> Pro</div>
  <ul class="text-sm opacity-85 space-y-2 list-disc pl-5">
    <li><strong>Lowers the barrier to entry</strong> — startups adopt a shared language instead of building their own moat</li>
    <li><strong>No single vendor</strong> controls the roadmap</li>
    <li><strong>Diversity of implementations</strong> drives innovation at the edges</li>
    <li>Genuine user <strong>choice</strong>, not the illusion of it</li>
    <li><strong>Interoperability</strong> without renegotiating every integration</li>
  </ul>
</div>

<div class="p-5 rounded-lg border border-red-500/50 shadow-sm">
  <div class="flex items-center gap-2 font-bold text-lg mb-3"><carbon:thumbs-down class="opacity-80"/> Con</div>
  <ul class="text-sm opacity-85 space-y-2 list-disc pl-5">
    <li><strong>Consensus is slow</strong> — standards can ossify before they ship</li>
    <li><strong>Governance conflicts</strong> shape the spec as much as user needs do</li>
    <li>Migration costs exist <strong>even between compliant</strong> implementations</li>
    <li><strong>Lowest-common-denominator</strong> risk — converging on what everyone agrees, not what's best</li>
    <li>The <strong>CNCF graveyard</strong> — not every standard survives long enough to matter</li>
  </ul>
</div>

</div>

---
layout: statement
---

You can write the code in a weekend.

<div class="text-3xl font-bold mt-6">The agreement is what takes a community.</div>

<div class="text-lg opacity-70 mt-8 max-w-2xl mx-auto">
  And the agreement is the part that's actually worth something — because it's the part that outlives any one vendor.
</div>

---
layout: image
image: /img/breaks/summit-vista.jpg
---

---
layout: section
---

# Take-aways

---
layout: default
---

# Three take-aways

<div class="grid grid-cols-1 gap-4 mt-6 max-w-3xl mx-auto">

<div class="p-5 rounded border-l-4 border-blue-500">
  <div class="text-lg font-bold">Evaluate governance, not just the spec</div>
  <div class="text-sm opacity-70 mt-1">Who owns the roadmap matters as much as what's in it.</div>
</div>

<div class="p-5 rounded border-l-4 border-purple-500">
  <div class="text-lg font-bold">Contribution is self-interest</div>
  <div class="text-sm opacity-70 mt-1">If you're not in the room, someone else's priorities shape the standard you depend on.</div>
</div>

<div class="p-5 rounded border-l-4 border-green-500">
  <div class="text-lg font-bold">A standard is only as good as its community</div>
  <div class="text-sm opacity-70 mt-1">A standard nobody maintains is just slower lock-in.</div>
</div>

</div>

---
layout: default
---

# Join us

<div class="text-sm opacity-70 -mt-2 mb-8">A standard is only as good as the community around it. Come help build it.</div>

<div class="grid grid-cols-2 gap-5">

<a href="https://cloud-native.slack.com/archives/C0344AANLA1" target="_blank" class="p-5 rounded-lg border border-gray-200 shadow-sm flex items-start gap-4 hover:border-gray-400 !text-inherit !no-underline">
  <carbon:logo-slack class="text-4xl opacity-70 shrink-0 mt-1"/>
  <div>
    <div class="font-bold">#openfeature on CNCF Slack</div>
    <div class="text-sm opacity-70 mt-1">Daily chat with maintainers and users. Best place to ask a question.</div>
    <div class="font-mono text-[10px] opacity-60 mt-1">cloud-native.slack.com · #openfeature</div>
  </div>
</a>

<a href="https://github.com/open-feature" target="_blank" class="p-5 rounded-lg border border-gray-200 shadow-sm flex items-start gap-4 hover:border-gray-400 !text-inherit !no-underline">
  <carbon:logo-github class="text-4xl opacity-70 shrink-0 mt-1"/>
  <div>
    <div class="font-bold">github.com/open-feature</div>
    <div class="text-sm opacity-70 mt-1">Spec, SDKs, providers, CLI — everything lives here. Issues and PRs welcome.</div>
    <div class="font-mono text-[10px] opacity-60 mt-1">github.com/open-feature</div>
  </div>
</a>

<a href="https://openfeature.dev/community" target="_blank" class="p-5 rounded-lg border border-gray-200 shadow-sm flex items-start gap-4 hover:border-gray-400 !text-inherit !no-underline">
  <carbon:user-multiple class="text-4xl opacity-70 shrink-0 mt-1"/>
  <div>
    <div class="font-bold">Community page</div>
    <div class="text-sm opacity-70 mt-1">Contributing guide, working groups, governance, code of conduct.</div>
    <div class="font-mono text-[10px] opacity-60 mt-1">openfeature.dev/community</div>
  </div>
</a>

<a href="https://openfeature.dev/community/meeting-notes" target="_blank" class="p-5 rounded-lg border border-gray-200 shadow-sm flex items-start gap-4 hover:border-gray-400 !text-inherit !no-underline">
  <carbon:calendar class="text-4xl opacity-70 shrink-0 mt-1"/>
  <div>
    <div class="font-bold">Community meetings</div>
    <div class="text-sm opacity-70 mt-1">Public calls — see exactly how the agreement gets made. Bring a topic.</div>
    <div class="font-mono text-[10px] opacity-60 mt-1">openfeature.dev/community/meeting-notes</div>
  </div>
</a>

</div>

<div class="text-sm opacity-70 text-center mt-6 italic">
  First-time contributors very welcome — maintainers label good-first-issues on GitHub.
</div>

---
layout: end
---

# Thanks — Q&A

<div class="text-lg opacity-80 mt-6 max-w-2xl mx-auto">
  Flip the switch with confidence — on a standard no single vendor owns.
</div>

<div class="mt-10 text-sm opacity-80">
  <carbon:email class="inline"/> simon@schrottner.at &nbsp;·&nbsp;
  <carbon:link class="inline"/> <a href="https://schrottner.at" target="_blank">schrottner.at</a> &nbsp;·&nbsp;
  <carbon:logo-github class="inline"/> aepfli &nbsp;·&nbsp;
  <carbon:logo-linkedin class="inline"/> in/aepfli
</div>

<div class="mt-2 text-xs opacity-60 font-mono">
  <carbon:logo-github class="inline align-middle"/> github.com/aepfli/flip-the-switch
</div>

<div class="abs-br m-6 flex items-end gap-2">
  <a href="https://schrottner.at/flip-the-switch/" target="_blank" class="text-xs opacity-60 hover:opacity-100 text-right leading-tight pb-1 !text-inherit">
    <div>Slides — grab them now</div>
    <div class="font-mono text-[10px] opacity-80 mt-0.5">schrottner.at/flip-the-switch</div>
  </a>
  <div class="bg-white p-1 rounded dark:invert">
    <QRCode data="https://schrottner.at/flip-the-switch/" :width="90" :height="90" :margin="2" />
  </div>
</div>
