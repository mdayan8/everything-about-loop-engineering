# Loop Engineering Illustrations

This directory contains illustrations for the "Everything About Loop Engineering" repository, designed in the Ian Xiaohei style (小黑怪诞正文配图).

## Directory Structure

```
assets/illustrations/
├── README.md                    # This file
├── ILLUSTRATION-GUIDE.md        # Detailed prompts and generation guidelines
├── generate-illustrations.sh    # Script with all illustration prompts
├── readme/                      # Illustrations for the main README
│   ├── 01-big-idea-transformation.svg
│   ├── 02-maturity-model.svg
│   ├── 03-six-building-blocks.svg
│   └── 04-six-production-patterns.svg
├── modules/                     # Illustrations for individual modules
│   ├── 02-loop-engineering-concept.svg
│   ├── 02-timeline-evolution.svg
│   ├── 03-six-building-blocks.svg
│   ├── 05-maturity-model.svg
│   └── 06-six-patterns.svg
└── examples/                    # Illustrations for examples
    └── 01-examples-overview.svg
```

## Style Guidelines

All illustrations follow the Ian Xiaohei style:

- **16:9 horizontal format** with pure white background
- **Black hand-drawn line art** with slight wobble
- **小黑 (Xiaohei)** as the core character: solid black creature with white dot eyes, thin legs, blank serious expression
- **Sparse red/orange/blue Chinese annotations** (5-8 labels, 2-8 characters each)
- **Lots of empty white space** (40-60% main subject, 35%+ blank)

## Color Usage

- **Black**: Main line art, 小黑, frames, structures, primary text
- **Orange**: Main flow/path/arrows, automation direction
- **Red**: Key warnings, problems, results, critical reminders
- **Blue**: Supplementary notes, system state, AI/assistant hints

## How to Generate Illustrations

### Option 1: Use the Generation Script

```bash
cd everything-about-loop-engineering
./assets/illustrations/generate-illustrations.sh
```

This script contains all prompts for generating the illustrations. Use these prompts with an image generation tool that supports the Ian Xiaohei style.

### Option 2: Use the Illustration Guide

For detailed prompts and generation guidelines, see [ILLUSTRATION-GUIDE.md](ILLUSTRATION-GUIDE.md).

### Option 3: Reference Existing Examples

For style reference images, see the examples in the ian-xiaohei-illustrations repository:
```
/tmp/ian-xiaohei-illustrations/ian-xiaohei-illustrations/assets/examples/
```

## Illustrations in Documentation

The following files have been updated to reference illustrations:

### README.md
- After "The Big Idea" section: `01-big-idea-transformation.svg`
- After "The Maturity Model" section: `02-maturity-model.svg`
- After "The Six Building Blocks" section: `03-six-building-blocks.svg`
- After "The Six Production Patterns" section: `04-six-production-patterns.svg`

### Module READMEs
- Module 02: After "The Short Version" and "The Timeline" sections
- Module 03: After "The Short Version" section
- Module 05: After "The Short Version" section
- Module 06: After "The Six Patterns" section

### Examples README
- At the top, after the title

## QA Checklist

Before finalizing illustrations, verify:

- [ ] 16:9 horizontal format
- [ ] Pure white background
- [ ] 小黑 present and performing core action
- [ ] Not copying previous examples
- [ ] Creative and interesting
- [ ] Clean and simple (40-60% main subject)
- [ ] One core concept per image
- [ ] Chinese labels short and readable
- [ ] Orange for main flow/arrows
- [ ] Red for warnings/problems/results
- [ ] Blue for supplementary notes

## Style Reference

For style reference, see the example images in the ian-xiaohei-illustrations repository. These images are for style calibration only - do not copy their compositions.

## Implementation Notes

1. **Generate one illustration at a time** using the prompts in the generation script
2. **Save illustrations** in the appropriate directory (readme/, modules/, examples/)
3. **Name files** descriptively: `01-topic-name.svg`
4. **Update documentation** to reference illustrations
5. **Check quality** against QA checklist before finalizing

## Contributing

If you generate new illustrations or improve existing ones, please:

1. Follow the style guidelines
2. Update the generation script with new prompts
3. Update this README with new file references
4. Ensure all illustrations pass the QA checklist
