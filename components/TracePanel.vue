<script setup>
// The hero's visual: one command as the platform records it. Illustrative
// content, deliberately in the shape of a real execution record.
const command = { name: "FinaliseAppraisal" };

const fields = [
  ["actor", "j.mwangi · officer"],
  ["object", "case/AK-2291 · facility"],
  ["policy", "approver signature required"],
];

const events = [
  { time: "09:14:02", name: "DocumentsVerified", detail: "12 checks", state: "ok" },
  { time: "09:14:02", name: "FindingRaised", detail: "registry mismatch", state: "flag" },
  { time: "09:26:40", name: "FindingResolved", detail: "evidence attached", state: "ok" },
  { time: "09:31:18", name: "CaptureAccepted", detail: "34 fields · 3 corrected", state: "ok" },
  { time: "09:33:07", name: "AppraisalGenerated", detail: "deterministic", state: "ok" },
  { time: "09:41:55", name: "AppraisalFinalised", detail: "signed · pdf", state: "ok" },
];
</script>

<template>
  <div class="relative isolate">
    <!-- glow behind the panel -->
    <div
      class="absolute -inset-x-10 -inset-y-8 -z-10 opacity-60 blur-3xl"
      style="background: radial-gradient(45% 45% at 60% 35%, rgba(211,173,98,0.16), transparent 70%)"
      aria-hidden="true"
    />

    <div class="overflow-hidden border rounded-xl border-white/10 bg-ink-900/90 shadow-2xl shadow-black/60">
      <!-- header -->
      <div class="flex items-center justify-between px-5 py-3 border-b border-white/6 bg-ink-850/80">
        <div class="flex items-center gap-2">
          <span class="w-2 h-2 rounded-full bg-white/12" />
          <span class="w-2 h-2 rounded-full bg-white/12" />
          <span class="w-2 h-2 rounded-full bg-white/12" />
          <span class="ml-3 font-mono text-2xs tracking-wider text-mist-500">audit/execution-record</span>
        </div>
        <span class="inline-flex items-center gap-1.5 font-mono text-2xs tracking-wider uppercase text-brass-400">
          <span class="w-1.5 h-1.5 rounded-full bg-brass-400" />
          append-only
        </span>
      </div>

      <!-- command block -->
      <div class="px-5 py-5 border-b border-white/6">
        <p class="eyebrow text-mist-500">command</p>
        <p class="mt-2 font-mono text-base text-mist-100">{{ command.name }}</p>
        <dl class="grid mt-4 gap-y-2 gap-x-4 text-xs sm:grid-cols-[5.5rem_1fr]">
          <template v-for="[key, value] of fields" :key="key">
            <dt class="font-mono text-mist-500">{{ key }}</dt>
            <dd class="font-mono text-mist-300">{{ value }}</dd>
          </template>
        </dl>
      </div>

      <!-- event stream -->
      <div class="px-5 py-4">
        <p class="eyebrow text-mist-500">events</p>
        <ul class="mt-3 divide-y divide-white/5">
          <li
            v-for="event of events"
            :key="event.time + event.name"
            class="flex items-center gap-3 py-2 font-mono text-xs"
          >
            <span class="text-mist-500 tabular-nums shrink-0">{{ event.time }}</span>
            <span class="truncate text-mist-200">{{ event.name }}</span>
            <span class="flex-1 h-px bg-white/6" aria-hidden="true" />
            <span class="hidden text-mist-500 sm:inline shrink-0">{{ event.detail }}</span>
            <span
              class="w-1.5 h-1.5 rounded-full shrink-0"
              :class="event.state === 'flag' ? 'bg-brass-400' : 'bg-emerald-400/70'"
            />
          </li>
        </ul>
      </div>

      <!-- footer -->
      <div class="flex items-center justify-between px-5 py-3 border-t border-white/6 bg-ink-850/60">
        <span class="font-mono text-2xs text-mist-500">sha256 9f2c·41ab·d0e7</span>
        <span class="font-mono text-2xs text-mist-500">6 events · 0 mutations outside a command</span>
      </div>
    </div>
  </div>
</template>
