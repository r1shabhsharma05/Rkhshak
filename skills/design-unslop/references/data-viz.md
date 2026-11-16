# Data Visualization — which chart, and how to draw it

Charts are content, not decoration. A chart that doesn't answer a question is a picture. Pick the chart by the question, not by what looks impressive.

## Which chart for which question
| Question | Chart | Notes |
|---|---|---|
| How does one number change over time? | Line chart | One line per series, max 3–4 series. Direct labels, not a legend the eye has to travel to. |
| How do categories compare? | Bar chart | Horizontal bars for long labels, vertical for time. Sorted (biggest first) unless time order matters. |
| What share is each part? | Donut (not pie) | Max 5 slices. Label each slice directly with its value. Never a 3D pie. |
| How are two numbers related? | Scatter plot | One dot per item, axes labeled with units. Trend line only if it means something. |
| How is a value distributed? | Histogram / bar | Bins are equal width, labeled with their range. |
| One number that matters? | A big number | Not a chart. Set the number huge (it is the answer) with a comparison (`+12% vs last month`). Stat cards are numbers — no sparklines or icons to fill them. |

## Rules
- **One main chart per screen, one accent per chart.** A dashboard with five charts is five questions the user didn't ask. Pick the one that matters.
- **Color means something.** Each series has a distinct hue AND a distinct marker/pattern (not hue alone — color-blind safety). The accent color is reserved for the series that matters most.
- **Label directly.** Values on the bars/points, not in a legend far away. Axes have units (`₹`, `%`, `days`). No chart without a title that says what it shows.
- **No decoration.** No gridlines that don't help read a value (light hairlines only, or none). No 3D, no shadows, no gradients on bars. No chartjunk.
- **Empty / loading / error states.** A chart with no data shows a real empty state (see `content-states.md`), not an empty grid. A loading chart shows a skeleton that matches the chart's shape.
- **Numbers are honest.** Axes start at zero for bars (never truncate a bar axis to exaggerate). If the axis doesn't start at zero, say so on the chart. Never cherry-pick the range to make a change look bigger.
- **Accessibility:** each series is distinguishable without color (marker/pattern/label). The chart has a text alternative (a table or a one-line summary) for screen readers.
- **Responsive:** the chart reflows at mobile (fewer ticks, rotated labels, or a simplified view) — never a tiny unreadable chart squeezed into 360px.
