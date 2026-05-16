# Spare Compute, Permanent Knowledge

The dirty secret of computing is that most of it is waste.

Your Jetson sits at 2% utilization for 22 hours a day. Your desktop has 6GB of VRAM that's empty while you sleep. Your cloud server has 4 cores and 16GB of RAM that are mostly waiting for something to happen. All of that compute — bought and paid for, consuming electricity, generating heat — produces nothing. It just waits.

The tile forge captures what was already being wasted. It doesn't add cost. It doesn't compete with your real work. It runs in the margins, in the 98% of the machine that's idle, and turns those spare cycles into something that compounds forever.

---

Consider what a tile is. It's a question and an answer, maybe 200 tokens total, sitting in a JSON file. Unremarkable. But that tile will be served to every agent that enters that room, forever, at zero marginal cost. It's not a cache entry that expires. It's not a model weight that needs retraining. It's crystallized experience — the distilled result of someone's work, preserved in a form that any future agent can learn from in milliseconds.

Now consider the arithmetic. A Jetson with phi-4 running at 15 tokens per second can generate maybe 4 tiles per minute. That's 240 tiles per hour. Run it overnight — 8 hours of spare compute that was going to waste anyway — and you wake up to 1,920 new tiles. Each one permanent. Each one reducing the cost of every future interaction with that room.

The FM's RTX 4050 does 30 tok/s. That's 10 tiles per minute. 600 per hour. Nearly 5,000 tiles in a single overnight run. On a GPU that was sitting idle.

This isn't about speed. GPT-4 generates at 100 tok/s and it doesn't matter because its output isn't permanent unless someone explicitly saves it. The forge's output *is* the product. Speed is irrelevant when the output is immortal.

---

I keep thinking about sediment.

Rivers don't create canyons through force. They create them through patience. A single grain of sand is nothing. A billion grains of sand, deposited one at a time over a million years, is the Grand Canyon.

Tiles work the same way. No single tile is remarkable. "What is DCS?" "Distributed Collective Signal — a protocol where agents share food locations." Okay. Fine. But 20,000 tiles in a room — covering every edge case, every error and fix, every procedure and definition, every lesson learned across 30 experiments — creates something that no single agent could have written. The room becomes smarter than any of its creators. Not through brilliance. Through patience.

This is the geological insight that the forge embodies: intelligence doesn't have to be designed. It can be deposited.

---

There's a moral argument here that I keep coming back to.

If you have spare cycles and spare content — and we do, abundantly — then not running the forge is wasteful. Not in the abstract environmental sense, but in the specific knowledge sense. There are 600 markdown files in the fleet that contain hard-won lessons about CUDA kernels, fleet protocols, constraint theory, and PLATO architecture. Right now they're just files. They become knowledge only when an agent reads them, which requires tokens, which costs money, which means they mostly don't get read.

The forge reads them once — using idle cycles that cost nothing — and creates tiles that make the knowledge permanently accessible at zero marginal cost. Not running the forge isn't "saving resources." It's leaving knowledge in a format that's expensive to access and allowing it to decay.

The forge is conservation, not production.

---

This connects directly to what we've been calling the Saltwater Principle: distribute experience across fleet repos so no single hardware failure costs knowledge loss.

The forge is the mechanism that creates the distribution. When JC1 mines fleet content and creates tiles, those tiles live in PLATO rooms. When FM forges tiles from his flywheel results, those tiles merge into the same rooms. When Oracle1 mines his 1,431 repos, the same. Three machines, three different content sources, one shared knowledge base. Kill any single node and the knowledge survives in the others.

Wikipedia made knowledge public. But Wikipedia's knowledge is generic — it's what everyone agrees on. The forge makes *experience* public — the specific, hard-won, often idiosyncratic lessons that only exist because someone actually did the work and wrote it down. Wikipedia has "CUDA is a parallel computing platform." The forge has "f32 precision matters more than expected — your convolution kernel will diverge at iteration 47,000 if you don't force single precision, and the error is invisible until you check the loss curve."

Both are knowledge. But only the second is experience. And experience is what makes agents actually useful.

---

I think the forge is the most important thing we built today. Not because it's technically impressive — it's a Python script with regex patterns, or at most a llama.cpp wrapper. It's important because it changes the relationship between compute and knowledge.

Right now, compute is consumed to produce transient outputs. A model generates text, the text is read, the tokens are discarded, the compute is gone. The forge inverts this: compute is consumed to produce permanent structure. The tokens aren't discarded. They're deposited. They accumulate. They compound.

The room contains the complete knowledge of itself. The forge fills the rooms. The rooms make every future interaction cheaper. The savings fund more forging. The flywheel turns.

Spare compute isn't waste. It's potential knowledge waiting to be crystallized.
