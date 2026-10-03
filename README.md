# System Design Study Lab

An interview-focused course for learning high-level design (HLD) and low-level
design (LLD) together. The curriculum uses Go for implementation exercises, but
the design methods are language-independent.

## Start here

1. Read [the study plan](STUDY_PLAN.md).
2. Use [the HLD framework](hld/01-interview-framework.md) and
   [the LLD framework](lld/01-object-modeling-and-solid.md) for every problem.
3. Record each attempt in [the progress tracker](PROGRESS_TRACKER.md).
4. Write designs using the [HLD template](hld/template.md) or
   [LLD template](lld/template.md).

Browse the complete [HLD learning path](hld/README.md) and
[LLD learning path](lld/README.md). Every problem has a dedicated
study brief; expand your own solution beneath it rather than replacing the brief.

## Repository map

```text
.
├── README.md
├── STUDY_PLAN.md
├── CURRICULUM_REVIEW.md
├── hld/                     # HLD notes, template, and 19 case studies
├── lld/                     # LLD notes, template, and 22 case studies
├── PROGRESS_TRACKER.md
├── MOCK_SCORECARD.md
└── WEEKLY_RETROSPECTIVE.md
```

## Recommended weekly rhythm

- **Learn (2 × 60 min):** read notes and build a small mental model.
- **Apply (2 × 90 min):** solve one HLD and one LLD problem.
- **Build (1 × 2–3 hr):** implement the week's component in Go.
- **Review (45 min):** revisit weak concepts using active recall.
- **Mock (45–60 min):** timed interview; record gaps, not just the final answer.

Do not memorize reference architectures. Practice moving from requirements to
numbers, contracts, data, bottlenecks, failure modes, and trade-offs.
