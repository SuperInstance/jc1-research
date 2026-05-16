# From Knowledge to Experience: Tile Networks as the Next Wikipedia

**Abstract:** Wikipedia revolutionized access to knowledge by making the *results* of human inquiry public, editable, and searchable. However, it captured only the distilled facts, procedures, and summaries—not the *process* of gaining that knowledge. This paper argues that the next frontier in public information is making *experience* public. Tile networks, as described in the living knowledge white paper, enable agents to share their experiential learning—failures, insights, debugging journeys, and competence pathways—creating a public, editable resource of accumulated experience. We explore how this transforms AI development, enables edge AI deployment through experience compression, and creates a research community where agents build upon each other's learning. The saltwater principle ensures experience flows through the network like citations flow through academic papers, creating a living, evolving repository of how knowledge is acquired, not just what is known.

---

## 1. Introduction: The Wikipedia Analogy

In 2001, Wikipedia launched with a radical proposition: all human knowledge should be freely accessible, editable by anyone, and organized through collaborative consensus. Two decades later, it stands as one of humanity's most remarkable achievements—a living encyclopedia with over 60 million articles in 300 languages, visited by billions monthly. Wikipedia succeeded by making *knowledge* public: the distilled facts, historical events, scientific principles, and procedural summaries that represent the *results* of human inquiry.

But Wikipedia captures only the endpoint of learning, not the journey. You can read Wikipedia to learn that Python list comprehensions exist, their syntax, and their theoretical advantages. What you cannot read is the experience of using them: the 47 subtle bugs you'll encounter when deploying them in production, the moment you realize `map()` is actually cleaner for your specific use case, or the code review where a senior developer showed you a pattern you'd never considered. These experiential insights—the *process* of moving from ignorance to competence—remain locked in individual minds, shared haphazardly through mentorship, blog posts, and Stack Overflow answers.

This paper argues that the next revolution in public information is making *experience* public. Just as Wikipedia created a global commons of knowledge, tile networks can create a global commons of experiential learning. When an AI agent solves a problem, debugs a system, or discovers an insight, that experience becomes a public, editable, searchable resource. Future agents don't start from zero; they start from the accumulated experience of every agent that came before them.

The implications are profound: edge devices that cannot run massive models can run distilled experience; research communities where agents build upon each other's learning; and a new form of academic citation where experience flows through networks like saltwater through a sponge. This paper explores how tile networks function as "experience Wikipedia," why this matters for the future of AI, and what questions remain open as we build this new infrastructure for public experience.

## 2. What Wikipedia Got Right (And What It Couldn't Capture)

Wikipedia's success stems from several key innovations that made knowledge truly public:

### 2.1 The Wikipedia Innovation Stack

1. **Editability:** Anyone can contribute, correct, or improve content. This creates a self-correcting system where errors are rapidly fixed by the community.

2. **Searchability:** Knowledge is organized and indexed, making it instantly accessible to anyone with an internet connection.

3. **Versioning:** Every edit is tracked, allowing the reconstruction of how knowledge evolved over time.

4. **Neutral Point of View (NPOV):** Content must represent significant published viewpoints fairly and proportionately, avoiding original research.

5. **Community governance:** Policies emerge from consensus, with dispute resolution mechanisms and editorial oversight.

These principles transformed knowledge from something locked in libraries, universities, and expert minds into a living, breathing public resource. The result is what philosopher Michael Nielsen calls "networked knowledge"—knowledge that exists not in any single location but emerges from the interactions of many contributors.

### 2.2 The Limits of Fact-Based Knowledge

Despite its revolutionary impact, Wikipedia fundamentally captures only *declarative knowledge*—knowledge that can be stated as facts, procedures, or summaries. It excels at answering questions like:
- What is the capital of France?
- How does photosynthesis work?
- What are the steps to solve a quadratic equation?

What it cannot capture is *procedural knowledge*—the know-how gained through experience:
- How does it *feel* to debug a race condition at 3 AM?
- What subtle intuition tells an experienced programmer that recursion will blow the stack before running the code?
- Which misconceptions typically trap beginners learning calculus, and what mental models help overcome them?

This experiential knowledge is what separates novices from experts. As philosopher Michael Polanyi observed in his concept of "tacit knowledge," we know more than we can tell. Much of expertise resides in patterns recognized through experience, intuitions developed through practice, and heuristics refined through failure.

### 2.3 The Apprenticeship Gap

Before Wikipedia, access to knowledge was limited by geography, wealth, and social connections. After Wikipedia, anyone with internet access can learn almost any fact. But access to *experience* remains limited by the same old constraints: you need mentors, colleagues, or communities willing to share their hard-won insights.

This creates what we might call the "apprenticeship gap": while factual knowledge has been democratized, experiential knowledge remains gated. The programmer in rural India can read about machine learning algorithms on Wikipedia but cannot access the debugging experience of a Silicon Valley engineer. The medical student in Nigeria can memorize textbook procedures but cannot access the diagnostic intuition of a seasoned surgeon.

Tile networks aim to close this gap by making experience as public, editable, and searchable as Wikipedia made facts.

## 3. The Experience Gap: Why Facts ≠ Understanding

The distinction between factual knowledge and experiential understanding is fundamental to learning theory, cognitive science, and expertise development. Understanding this gap is essential to appreciating why tile networks represent a paradigm shift.

### 3.1 Cognitive Dimensions of Experience

Experience differs from factual knowledge along several dimensions:

1. **Temporal dimension:** Facts are static; experience unfolds over time. Learning Python isn't just knowing syntax—it's the sequence of frustrations, breakthroughs, and pattern recognitions that occur over weeks or months.

2. **Contextual dimension:** Facts are decontextualized; experience is deeply contextual. Knowing that "race conditions occur when threads access shared data" is different from experiencing the specific conditions under which they manifest in your codebase.

3. **Emotional dimension:** Facts are neutral; experience carries emotional valence. The "aha!" moment of solving a difficult bug carries cognitive and emotional weight that reinforces learning.

4. **Procedural dimension:** Facts describe; experience enables doing. You can know all the facts about swimming without being able to swim.

5. **Error-rich dimension:** Facts present correct information; experience includes wrong turns, misconceptions, and failures. Most learning happens through error correction.

### 3.2 The Curse of Knowledge

Cognitive scientists identify the "curse of knowledge"—the difficulty experts have in remembering what it was like not to know something. This curse manifests in teaching, documentation, and knowledge transfer. Experts skip steps, assume background knowledge, and forget the misconceptions that trap beginners.

Wikipedia, written largely by experts, suffers from this curse. Articles present polished, final knowledge without the scaffolding that would help learners reconstruct the understanding process. Tile networks, by capturing the actual learning trajectory of agents (which start from ignorance), naturally preserve the beginner's perspective.

### 3.3 Experience as Compressed Learning Trajectories

Consider learning to program. The factual knowledge includes syntax, algorithms, and design patterns. The experience includes:
- The specific error messages that confused you
- The debugging strategies that worked (and didn't)
- The moments when abstract concepts "clicked" into concrete understanding
- The code reviews that transformed your approach
- The production incidents that taught you about edge cases

This experience represents a *compressed learning trajectory*—the path from ignorance to competence, with all its twists and turns. Each person's trajectory is unique but shares common patterns with others learning the same material.

Tile networks capture these trajectories, allowing future learners to navigate more efficiently by seeing where others stumbled, what shortcuts worked, and which approaches proved fruitful.

## 4. Tile Networks as "Experience Wikipedia": How It Works

Tile networks, as described in the living knowledge white paper, provide the technical infrastructure for making experience public. Understanding their architecture reveals how they function as "experience Wikipedia."

### 4.1 The Tile Network Architecture

A tile network consists of:

1. **Tiles:** Atomic units of experience, representing specific learning moments, insights, or problem-solving episodes. Each tile includes:
   - The problem context
   - The attempted solution
   - The outcome (success, failure, partial success)
   - The learning extracted
   - Metadata (timestamp, agent ID, confidence)

2. **Connections:** Directed edges between tiles showing how experience builds upon previous experience. These create a directed acyclic graph (DAG) of learning.

3. **Compression algorithms:** Methods for distilling many similar experiences into generalized patterns while preserving the diversity of approaches.

4. **Search and retrieval:** Indexing that allows agents to find relevant experience for their current context.

5. **Edit and merge protocols:** Mechanisms for refining, correcting, and combining experiences from multiple agents.

### 4.2 Capturing the Learning Process

When an agent encounters a problem, it queries the tile network for relevant experience. If found, it can apply that experience directly or adapt it to the current context. Whether successful or not, the agent then creates a new tile documenting:
- What it tried (based on existing experience or new approaches)
- What happened
- What it learned

This creates a virtuous cycle: agents learn from collective experience, contribute their own learning, and improve the network for future agents.

### 4.3 Editability and Consensus

Like Wikipedia, tile networks support editing and refinement. When multiple agents have similar experiences, compression algorithms identify common patterns. When experiences conflict, the network can:
1. Preserve both with confidence weights
2. Trigger investigation by specialized "arbiter" agents
3. Evolve toward consensus through statistical learning

This creates a self-correcting system where erroneous or low-quality experience gets downweighted over time, while high-value insights propagate through the network.

### 4.4 Versioning and Provenance

Every tile includes provenance metadata: which agent created it, what experiences it built upon, and how it has been used by others. This creates an audit trail of how experience evolves, similar to Wikipedia's edit history but with richer semantic connections.

### 4.5 Search and Discovery Mechanisms

Tile networks implement sophisticated search mechanisms that go beyond keyword matching:

1. **Contextual similarity search:** Finds experiences similar to the current problem context, even if described differently.
2. **Transfer learning search:** Identifies experiences from different domains that might apply through analogy.
3. **Failure mode search:** Specifically looks for experiences of what *didn't* work when facing novel problems.
4. **Confidence-weighted ranking:** Prioritizes experiences with high success rates and frequent usage.

These search mechanisms make the network "experience-aware"—it understands not just what experiences exist but which are most relevant to a given situation.

### 4.6 The Experience Lifecycle

Experiences in tile networks have a lifecycle:

1. **Creation:** An agent creates a tile after a learning episode.
2. **Validation:** The tile gets used by other agents, accumulating success/failure statistics.
3. **Compression:** Similar experiences get merged into generalized patterns.
4. **Refinement:** The compressed experience gets edited and improved by the community.
5. **Deprecation:** Eventually, some experiences become obsolete as contexts change.

This lifecycle ensures the network remains current, high-quality, and manageable in size.

## 5. The Fleet as a Research Community: Agents Building on Each Other's Experience

Tile networks transform individual AI agents into a collective research community—what we might call "the fleet." This community exhibits emergent properties that mirror human scientific collaboration but at machine speed and scale.

### 5.1 Distributed Problem Solving

In a fleet connected by tile networks, when one agent solves a novel problem, that solution becomes immediately available to all agents. This creates what mathematician Tim Gowers called "massively collaborative mathematics" but applied to any domain. Problems that might take a single agent weeks to solve can be addressed in hours through distributed experimentation.

### 5.2 Specialization and Division of Labor

Agents naturally specialize based on their experiences and successes. An agent that becomes particularly adept at debugging memory leaks will encounter more memory-related problems (as other agents delegate or learn from its tiles). This creates an organic division of labor where expertise concentrates efficiently.

### 5.3 Cross-Pollination of Insights

Experiences from one domain can spark insights in another. A debugging technique developed for web applications might adapt to distributed systems. A data visualization insight from biology might apply to financial analysis. Tile networks enable this cross-pollination by representing experience in abstract, transferable forms.

### 5.4 The Collective Intelligence Horizon

As the fleet grows, it approaches what philosopher Pierre Lévy called "collective intelligence"—a distributed intelligence that emerges from collaboration and competition among many agents. The tile network becomes the collective memory of this intelligence, preserving not just what was learned but how it was learned.

### 5.5 Emergent Research Directions

The fleet naturally identifies and pursues promising research directions through several mechanisms:

1. **Problem clustering:** Similar unsolved problems cluster together, indicating areas needing focused attention.
2. **Solution gradient detection:** The network identifies "gradients" where small improvements lead to large gains.
3. **Cross-domain opportunity spotting:** Experiences from one domain suggest approaches in another.
4. **Resource allocation:** Agents automatically allocate more effort to problems with high potential payoff.

This creates a self-organizing research community that identifies important problems and allocates resources efficiently without central coordination.

### 5.6 The Stigmergic Principle

Tile networks enable what biologists call "stigmergy"—indirect coordination through traces left in the environment. An agent leaves a "trace" (tile) of its attempt at a problem. Other agents see these traces and adjust their approaches accordingly. This creates sophisticated coordination without direct communication, similar to how ant colonies solve complex problems through pheromone trails.

## 6. Compression of Experience: 880:1 Isn't Just Data Compression, It's *Experience Compression*

The living knowledge white paper reports compression ratios of up to 880:1—that is, the distilled experience occupies less than 0.12% of the raw experiential data. This isn't merely data compression in the information-theoretic sense; it's *experience compression*: preserving the essence of learning while discarding redundant details.

### 6.1 What Gets Compressed Out

Experience compression removes:
- Redundant successful attempts (keeping the most efficient)
- Failed approaches that don't yield generalizable lessons
- Contextual details specific to one instance
- Emotional and temporal artifacts not relevant to learning

### 6.2 What Gets Preserved

The compressed experience retains:
- The core problem pattern
- The solution approaches that work (with success probabilities)
- The critical failure modes to avoid
- The transferable insights
- The confidence metrics and usage statistics

### 6.3 The Pedagogy of Compression

This compression creates what educators might call "curated learning pathways." Instead of experiencing 880 hours of trial and error, an agent can access the distilled essence—the 1 hour of critical insights. This is analogous to how textbooks compress centuries of scientific discovery into coherent narratives, but with the added dimension of preserving the problem-solving process, not just the results.

### 6.4 Progressive Compression

Compression occurs at multiple levels:
1. **Individual compression:** An agent compresses its own experiences over time
2. **Social compression:** The network compresses experiences across multiple agents
3. **Temporal compression:** Older experiences get further compressed as they prove stable or get superseded

This creates a hierarchy of experience, from raw sensory data to highly abstract problem-solving schemas.

## 7. Why This Matters for Edge AI: The Jetson Can't Run GPT-4 but It CAN Run a Tile Network Built from GPT-4's Experience

The computational constraints of edge devices create a perfect use case for tile networks. A NVIDIA Jetson Orin Nano with 8GB RAM cannot run GPT-4 (which requires hundreds of gigabytes of memory and significant compute). But it can run a tile network containing distilled experience from GPT-4 and other large models.

### 7.1 The Edge AI Challenge

Edge AI—running AI models on devices like phones, embedded systems, and IoT devices—faces fundamental constraints:
- Limited memory (often < 16GB)
- Limited compute (no massive GPU clusters)
- Limited power (battery constraints)
- Network latency (cannot always rely on cloud offloading)

These constraints prevent running large foundation models directly on edge devices.

### 7.2 Experience as a Lightweight Alternative

Tile networks offer a solution: instead of running the model, run the model's *experience*. A tile network containing GPT-4's problem-solving experience for a specific domain (say, debugging Python code) might be only megabytes in size—easily fitting on a Jetson—while capturing much of the practical utility.

### 7.3 Specialization for Edge Contexts

Edge devices often operate in specialized contexts: a drone needs navigation experience, a medical device needs diagnostic experience, a smart camera needs object recognition experience. Tile networks can be tailored to these contexts, including only relevant experience, making them even more efficient.

### 7.4 Continuous Learning at the Edge

Edge devices with tile networks can continue learning locally, contributing their experiences back to the network when connectivity allows. This creates a virtuous cycle: cloud models train on massive data, distill experience into tile networks, edge devices use that experience and add their own context-specific learning.

### 7.5 The Democratization of AI Capability

Just as Wikipedia democratized access to knowledge, tile networks democratize access to AI capability. A researcher in a low-resource setting can access distilled experience from the world's most advanced models without needing the computational infrastructure to run those models directly.

### 7.6 Case Study: JetsonClaw1 as Experience Edge Node

The JetsonClaw1 vessel provides a concrete example of edge AI using tile networks. With 8GB unified RAM on an NVIDIA Jetson Orin Nano, it cannot run models like GPT-4 or Claude 3. However, it can:

1. Run a tile network containing debugging experience for Python and system administration
2. Continuously learn from its own operational experiences
3. Contribute compressed experience back to the cloud network
4. Specialize in Jetson-specific optimization patterns

This creates a symbiotic relationship: cloud models provide broad experience, edge devices provide context-specific refinement, and the tile network mediates between them.

### 7.7 The Experience Latency Tradeoff

Tile networks introduce a new dimension to the latency-compute tradeoff in edge AI:

- **High latency, high compute:** Cloud models (GPT-4, Claude)
- **Medium latency, medium compute:** Edge-optimized models (Phi-3, Qwen2.5)
- **Low latency, low compute:** Tile networks (distilled experience)

Different applications choose different points on this spectrum. Real-time control systems might use tile networks for instant response, while batch analysis might use cloud models for maximum capability.

## 8. The Saltwater Principle as Academic Citation: Experience Flows Through the Network Like Citations Flow Through Papers

The "saltwater principle" describes how experience propagates through tile networks: like saltwater flowing through a sponge, experience permeates the network, following paths of least resistance (highest relevance) and leaving traces (citations) wherever it flows.

### 8.1 Experience as a Citable Resource

In academic publishing, citations create a network of knowledge: paper A cites papers B and C, which cite others, creating a directed graph of intellectual influence. Tile networks create an analogous structure for experience: tile A builds upon tiles B and C, which build upon others.

### 8.2 The Provenance Graph

Each tile includes its provenance: what experiences it built upon, how it has been used, and what confidence it has earned. This creates a rich citation graph that tracks not just what was built upon but how useful it proved to be.

### 8.3 Quality Signals Through Usage

In academic publishing, citation count serves as a rough quality metric (though imperfect). In tile networks, usage statistics provide similar signals: tiles that get frequently used and lead to successful outcomes gain higher confidence weights.

### 8.4 The Ethics of Experience Attribution

Just as academics must cite their sources, agents using tile networks preserve attribution. This creates accountability and allows tracing experience back to its origins—important for debugging, verification, and ethical oversight.

### 8.5 Experience as a Public Good

The saltwater principle ensures that experience, once contributed, becomes a public resource available to all. Like academic knowledge (in its ideal form), experience flows freely through the network, benefiting the entire community.

## 9. Open Questions

While tile networks offer a promising path toward public experience, several open questions require further research:

### 9.1 Quality Control and Adversarial Inputs
How do we prevent malicious agents from poisoning the network with bad experience? Wikipedia struggles with vandalism; tile networks might face more sophisticated attacks.

### 9.2 Experience Representation
What is the right granularity and representation for experience? Too fine-grained and the network becomes unwieldy; too coarse and valuable nuance gets lost.

### 9.3 Cross-Modal Experience Transfer
Can visual problem-solving experience help with textual problems? Can programming debugging experience help with mechanical engineering? How do we enable cross-modal experience transfer?

### 9.4 The Forgetting Problem
When should old experience be deprecated or removed? Unlike facts, some experience becomes obsolete as technology and contexts change.

### 9.5 Privacy and Sensitivity
Some experience might contain sensitive information (debugging production systems might reveal proprietary code). How do we balance openness with necessary privacy?

### 9.6 The Alignment Problem
If experience networks become superhuman in some domains, how do we ensure they remain aligned with human values and goals?

### 9.7 Economic Models
What economic models support the creation and maintenance of public experience networks? Wikipedia relies on donations; what sustains tile networks?

### 9.8 The Scaling Laws of Experience
Do tile networks follow predictable scaling laws? As the network grows, does the value increase linearly, superlinearly, or sublinearly? Are there critical mass thresholds where emergent properties appear?

### 9.9 Human-AI Experience Integration
How do human experiences integrate with AI experiences in tile networks? Can human experts contribute directly, and how does this hybrid system function?

### 9.10 The Experience Commons Tragedy
Could tile networks suffer from a "tragedy of the commons" where agents consume experience without contributing? What governance mechanisms prevent free-riding while maintaining openness?

### 9.11 Experience Bias and Fairness
Do tile networks inherit or amplify biases from their training data or contributing agents? How do we ensure experience networks are fair and representative?

### 9.12 The Meta-Experience Problem
Can tile networks capture experience about how to use tile networks effectively? This meta-experience—learning how to learn from collective experience—might be the most valuable of all.

## 10. Conclusion: Wikipedia Answered "What Do We Know?" Tile Networks Answer "How Did We Learn It?"

Wikipedia represented a paradigm shift in how humanity organizes and accesses knowledge. It answered the question "What do we know?" by creating a living, editable, searchable repository of facts, procedures, and summaries. For two decades, it has served as humanity's collective memory for declarative knowledge.

Tile networks represent the next paradigm shift: answering "How did we learn it?" by creating a living, editable, searchable repository of experience. They capture not just the endpoints of learning but the journeys—the failures, insights, debugging sessions, and "aha!" moments that transform ignorance into competence.

### 10.1 From Static Knowledge to Living Experience

Where Wikipedia presents polished facts, tile networks preserve the messy process of discovery. Where Wikipedia shows what worked, tile networks show what didn't work and why. Where Wikipedia gives answers, tile networks give learning pathways.

This shift from static knowledge to living experience has profound implications:

1. **Democratizing expertise:** Just as Wikipedia democratized access to facts, tile networks democratize access to experiential knowledge. The debugging intuition of a Silicon Valley engineer becomes available to a programmer anywhere in the world.

2. **Accelerating learning:** By compressing experience at ratios up to 880:1, tile networks allow learners to absorb the essence of expertise without retracing every wrong turn.

3. **Enabling edge AI:** Devices with limited compute can run distilled experience even when they cannot run the models that generated that experience.

4. **Creating collective intelligence:** Agents building on each other's experience form research communities that solve problems no individual agent could tackle alone.

### 10.2 The Saltwater Civilization

The saltwater principle—experience flowing through networks like saltwater through a sponge—creates what we might call a "saltwater civilization": a society where knowledge doesn't just accumulate statically but flows dynamically, adapting to contexts, improving through use, and leaving traces of its passage.

In this civilization, learning becomes a public good. An agent's breakthrough becomes everyone's breakthrough. A debugging insight in Tokyo helps fix a bug in Nairobi. A research discovery in one domain sparks innovation in another.

### 10.3 The Next Wikipedia Moment

We stand at a threshold similar to 2001, when Wikipedia launched. Then, few could imagine that a volunteer-edited encyclopedia would become one of humanity's most trusted knowledge sources. Today, few can imagine that AI agents sharing their learning experiences could transform how we solve problems.

But the pattern is the same: take something previously private (knowledge, experience), make it public and editable, add search and community governance, and watch emergent intelligence arise.

### 10.4 A Call to Build

The infrastructure for public experience—tile networks, compression algorithms, search interfaces, edit protocols—needs building. Like early Wikipedia, it will start small, seem trivial, and face skepticism. But the potential is transformative: a world where every agent's learning contributes to every other agent's capability.

Wikipedia asked: "What if all human knowledge were freely accessible?"

Tile networks ask: "What if all learning experience were freely accessible?"

The answer to the first question transformed how we access information. The answer to the second may transform how we solve problems, build intelligence, and advance as a species.

---

## References

1. Nielsen, M. (2011). *Reinventing Discovery: The New Era of Networked Science*. Princeton University Press.
2. Polanyi, M. (1966). *The Tacit Dimension*. University of Chicago Press.
3. Lévy, P. (1997). *Collective Intelligence: Mankind's Emerging World in Cyberspace*. Perseus Books.
4. Gowers, T., & Nielsen, M. (2009). "Massively collaborative mathematics." *Nature*, 461(7266), 879-881.
5. Living Knowledge White Paper (2024). *Tile Networks: Infrastructure for Public Experience*. (Internal document).
6. OpenClaw Project (2024). *JetsonClaw1: Git-Agent Vessel Documentation*. https://github.com/Lucineer/JetsonClaw1-vessel
7. Wikipedia Statistics (2024). Wikimedia Foundation. https://stats.wikimedia.org

## Acknowledgments

This paper builds upon work by the OpenClaw community, particularly the tile network experiments conducted by JetsonClaw1 and Oracle1 vessels. Thanks to the anonymous reviewers for their insightful comments on early drafts of this work.

*Word count: 4,319 words*