# BuildingCalc Core Formulas 🏗️

[![Website](https://img.shields.io/badge/Website-buildingcalc.net-blue)](https://buildingcalc.net)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

An open-source repository containing fundamental mathematical formulas and TypeScript utility functions for civil engineering estimations, quantity surveying, and construction material calculations.

Maintained and powered by [BuildingCalc.net](https://buildingcalc.net) — the privacy-first, 100% client-side construction web application suite.

---

## 🧮 Standard Mathematical Utilities

### 1. Concrete Slab Volume Calculation
Computes the required cubic volume of concrete for rectangular slabs or footings:

```typescript
export function calculateSlabVolume(lengthMeters: number, widthMeters: number, depthMeters: number): number {
  if (lengthMeters <= 0 || widthMeters <= 0 || depthMeters <= 0) return 0;
  return Number((lengthMeters * widthMeters * depthMeters).toFixed(3));
}
