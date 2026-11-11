# Choose Your Own Adventure: The Saga of Serving LLM Inference

Slides for Whitney Lee and Viktor Farcic's talk at KubeCon + CloudNativeCon North America 2026. The audience votes on three inference-serving choices, then the talk explains what each choice means. The demo that runs the votes is [vfarcic/inference-vote](https://github.com/vfarcic/inference-vote).

The deck is built with [Slidev](https://sli.dev), a tool that turns a Markdown file (`slides.md`) into a slide deck that runs in the browser.

**View the slides online:** https://wiggitywhitney.github.io/cyoa-kubecon-na-2026/

## Present from your own laptop

You need Node.js 22.12 or newer and pnpm.

```bash
git clone https://github.com/wiggitywhitney/cyoa-kubecon-na-2026.git
cd cyoa-kubecon-na-2026
pnpm install --frozen-lockfile
npx slidev --port 3030
```

Slidev prints the addresses it serves:

```text
  public slide show   > http://localhost:3030/
  presenter mode      > http://localhost:3030/presenter/
  slides overview     > http://localhost:3030/overview/
```

Open the **presenter mode** address on the laptop screen to see the speaker notes, the next slide, and a timer. Open the **public slide show** address in a second window on the projector. The two windows stay in sync as you click through.

The deck runs entirely on your laptop, so it keeps working if the Wi-Fi drops.

To get the latest changes before presenting:

```bash
git pull
```

The running deck picks up the changes automatically.
