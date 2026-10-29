# Notes

## Paper in one line
Planning: goal → actions. Inverse planning (Bayesian ToM): actions → goal. Inverse inverse planning: choose actions so that an observer's inverse planner reaches a target belief, over time.

## Core ideas
- Acting *in* a situation vs. acting *out* a situation. A storyteller optimizes the audience's belief, not the character's reward.
- Inspired by Kukkonen (2014): a story is a "probability design" — a journey of the reader's changing beliefs.
- Audience model: Ullman et al. (2009) inverse planner. Grid world, robot + "cheese" agent, MDP, softmax-rational policies, two levels of recursion.
- Hypothesis H = ⟨G_cheese, G_robot, ρ_robot⟩. Posterior P(H | s → a) ∝ P(s → a | H) P(H).
- Script σ = initial state + sequence of transitions. Objective example: f_help(σ) = Σ_t P(ρ_robot > 0 | σ_1:t). Optimized with beam search.

## Results
- Exp. 1 (N = 98, 120 animations): "helping" recognized 73% vs. 6% (naïve planning). "Hindering" 63% vs. 29%. "Indifferent" equal (73% vs. 75%).
- Physics mime: differentiable simulator, SHAC actor-critic. Exp. 2 (N = 35): mime judged heavier than real light box 95.7%, heavier than real heavy box 68.6%.
- Storytelling elements as objectives: plot twist, irony, flashback, narrative arc (Vonnegut shapes) with deus ex machina, stumbling.

## Limits (from the paper)
- Scales poorly: state, hypothesis and script spaces grow fast.
- Too slow for real-time improvisation.
- Future work: emotion in the audience model.

## Borges link
Page numbers refer to `papers/Borges1941_The_Garden_of_Forking_Paths.pdf`.

### Plot in brief
Yu Tsun, a German spy in England, knows the name of the town with the new British artillery park. Madden is about to catch him. Yu Tsun cannot send a message to Berlin. He finds the name "Stephen Albert" in the phone book, travels to Albert's house, and talks with Albert about Ts'ui Pen's labyrinth-novel. Then he shoots Albert. The newspapers report the murder. The Chief in Berlin reads the report, understands the message, and the town of Albert is bombed (p. 8).

### Main point: the murder is inverse inverse planning inside the story
- Yu Tsun does not act *in* the situation. He acts *out* a message for one observer, the Chief. This is the paper's "acting in vs. acting out" distinction in its strongest form.
- Mapping:
  - Storyteller = Yu Tsun.
  - Audience = the Chief, who sees only newspaper reports (the observation channel, p. 1–2).
  - Target belief = "the target is the town called Albert".
  - Script σ = take the train, find the man, kill him, get arrested.
- The action is very bad in the world (he kills a friend and is sentenced to hang). It is the best action for the belief it creates. This is the paper's claim that a storyteller "might choose a sub-optimal action" for a stronger effect on the audience.
- The Chief "already solved" the puzzle (p. 8). That is a successful inverse planner: P(target = Albert | the reported murder) is high.
- It is also the miming result in an extreme form: the act depicts something (a place name) that it is not.

### Second level: Borges as inverse inverse planner of the reader
The reader's belief about Yu Tsun's goal changes over the story. Each step maps to one storytelling device in the paper.

| Story step | Reader's belief about Yu Tsun's goal | Device in paper |
|---|---|---|
| Frame: the Liddell Hart offensive is delayed, "unsuspected light" (p. 1) | The deposition explains a historical event | Flashback: c(σ) recontextualizes a known fact |
| Phone book, "the one person capable of passing on the information" (p. 2) | Albert is an informant or contact | Ambiguous goal, posterior spread |
| Long talk on the labyrinth (p. 5–7) | Yu Tsun waits for Madden, or the visit is about family history | Belief drifts away from the true goal |
| Yu Tsun says he is Albert's friend, then shoots (p. 8) | Helper, then sudden "hinderer" | Plot twist, close to f_twist: ρ > 0 for t ≤ T/2, ρ < 0 after |
| Last paragraph: the town is called Albert (p. 8) | The whole visit was a message | Flashback-style reinterpretation of all earlier actions |

- Dramatic irony: Albert says that in some futures he is Yu Tsun's enemy (p. 8). The reader then knows more than Albert. This matches f_irony: the audience is certain about something that a character does not know.
- Narrative arc: terror → hope after he escapes on the train (p. 2–3) → calm in the garden → murder → triumph and remorse. Compare with f_arc (rise-fall-rise).

### Third level: the garden itself as the space of scripts
- Ts'ui Pen's novel takes *all* branches at each choice point (p. 6). The paper's optimizer searches the same tree of scripts and keeps *one*. Storytelling = choose a path through the garden for its effect on beliefs.
- The two battle chapters (p. 6–7) reach the same outcome (victory) by different paths. Compare: f_help does not fix the goals or the start state. Many scripts satisfy the same belief objective.
- The chess riddle (p. 7): the book is about time but never uses the word. This is "show, don't tell" as a design rule. The audience infers the concept from what is shown. Yu Tsun's message works the same way: he never says the word "Albert" to the Chief.
- Editor's footnote (p. 1) contradicts the narrator. The reader must model an unreliable narrator. The paper's audience model assumes that all observations are true.

### Critique points from this text
- **Shared hypothesis space.** The message works only because the Chief's hypothesis space contains "a killing can encode a place name". The paper uses a small, fixed space H = ⟨G_cheese, G_robot, ρ⟩. How can a storyteller rely on hypotheses that the audience builds only when it sees the act?
- **One-shot, noisy channel.** Yu Tsun has one action, seen only through newspapers. The paper's audience sees the full trajectory with no noise.
- **Emotion.** Yu Tsun's "infinite penitence" (p. 8) is outside any belief objective. The paper names emotion as future work.
- **Ethics.** Inverse inverse planning is also deception: a "helpful" act is in fact hostile. Compare the paper's references on legibility vs. deceptive motion (Dragan; Pattanayak).

### Discussion questions (draft)
1. Write an objective f(σ) for Yu Tsun. Which term makes the murder better than any other action?
2. Is the Chief a Bayesian inverse planner? What prior does he need?
3. Can a branching story like Ts'ui Pen's novel be optimized at all, or is it the absence of a choice of σ?
4. Plot twists need a wrong belief first. Is a good twist a script that *maximizes* the KL-divergence at one time step?

## Talk outline (draft)
1. Hook: Heider & Simmel video.
2. Recap: Bayesian inverse planning (link to 03.12 session).
3. Inverse inverse planning: idea and objective.
4. Grid-world results + Exp. 1.
5. Mime + Exp. 2.
6. Storytelling devices as objectives.
7. Borges: Yu Tsun's murder as inverse inverse planning, then the reader's belief path, then the garden as script space.
8. Critique + discussion questions.

## Open tasks
- [ ] Ask organizer for talk length and format.
- [ ] Watch videos at the OSF / project link.
- [x] Re-read Borges and map it to the paper.
- [ ] Pick 2–3 short passages for slides.
- [ ] Refine the discussion questions.
