# BuildingCalc Core Formulas

**Open-source mathematical utilities for construction quantity estimation.**

[![Website](https://img.shields.io/badge/Website-BuildingCalc.net-2563eb)](https://buildingcalc.net/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

BuildingCalc Core Formulas is an open-source project for documenting and implementing mathematical utilities used in construction quantity estimation and building-material calculations.

The project is maintained alongside [BuildingCalc.net](https://buildingcalc.net/), a browser-based platform of construction calculators for builders, contractors, homeowners, and DIY users.

The goal is to make calculation logic easier to inspect, understand, test, and improve.

## Project goals

- Document the mathematical assumptions behind construction estimates.
- Keep calculation functions readable and maintainable.
- Validate inputs and define expected behaviour for invalid values.
- Encourage transparent examples and reproducible tests.
- Help developers understand common construction quantity calculations.

## Current scope

The repository currently includes a concrete slab volume calculation example and a masonry brickwork-count resource. Check the source files before relying on any calculation in a project.

Additional calculation modules should be added only when their implementation, units, assumptions, and tests are documented.

## Example: rectangular concrete slab volume

For a rectangular slab, the basic geometric volume is:

\[
V = L \times W \times D
\]

Where:

- \(V\) is volume in cubic metres.
- \(L\) is length in metres.
- \(W\) is width in metres.
- \(D\) is depth in metres.

Example:

A slab measuring 5 m × 4 m × 0.15 m has a geometric volume of:

\[
5 \times 4 \times 0.15 = 3.0 \text{ m}^3
\]

This is the geometric volume only. It does not automatically account for wastage, uneven excavation, reinforcement displacement, or supplier ordering requirements.

### Illustrative TypeScript implementation

```typescript
export function calculateSlabVolume(
  lengthMeters: number,
  widthMeters: number,
  depthMeters: number
): number {
  if (
    !Number.isFinite(lengthMeters) ||
    !Number.isFinite(widthMeters) ||
    !Number.isFinite(depthMeters) ||
    lengthMeters <= 0 ||
    widthMeters <= 0 ||
    depthMeters <= 0
  ) {
    return 0;
  }

  return Number(
    (lengthMeters * widthMeters * depthMeters).toFixed(3)
  );
}
```

**Implementation note:** Use this example only if it matches the committed source code. If the existing function differs, update the example to match the tested implementation rather than documenting code that is not present.

## Design principles

### Clear units

Functions should document the units expected for every input and returned value.

### Predictable validation

Invalid, non-finite, or out-of-range inputs should have documented behaviour. A return value of zero is one possible API choice, but it must not be mistaken for a valid estimate.

### Explicit assumptions

Geometric quantities should be distinguished from purchasing quantities and engineering design calculations.

### Testable calculations

Each supported function should have examples and automated tests covering ordinary values, boundaries, and invalid inputs.

## Repository structure

As the project grows, a possible structure is:

```text
buildingcalc-core-formulas/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── SECURITY.md
├── CHANGELOG.md
├── src/
│   ├── concrete/
│   └── masonry/
└── tests/
```

Adapt this structure to the actual codebase. Do not create empty folders merely to make the repository look larger.

## Testing

Tests should verify the expected output for documented examples, input validation, unit assumptions, rounding, and edge cases.

If automated tests are available, follow the repository's documented test instructions. If no test suite exists yet, contributions should include tests alongside new calculation functions.

## Safety and limitations

This project provides mathematical utilities for estimation and educational purposes. It is not a substitute for site inspection, engineering judgement, local building codes, or professional review.

Structural design, electrical sizing, reinforced-concrete design, and other safety-critical work require appropriate methods, assumptions, standards, and qualified professional verification.

A mathematically correct calculation does not by itself establish that a real-world design is safe or code-compliant.

## Contributing

Contributions are welcome when they improve calculation correctness, clarity, documentation, or test coverage.

Before submitting a change:

1. Explain the calculation and its units.
2. Document assumptions and limitations.
3. Include a worked example.
4. Add tests for normal and invalid inputs.
5. Keep changes focused and reviewable.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the contribution process.

## Licence

This repository is distributed under the licence specified in [LICENSE](LICENSE). Check that file for the applicable permissions and conditions.

## Project website

Explore the calculators and guides at [BuildingCalc.net](https://buildingcalc.net/).

The website and this repository have related goals, but the presence of a calculator on the website does not imply that its underlying implementation is included in this repository.
