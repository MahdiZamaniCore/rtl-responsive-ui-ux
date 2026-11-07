# Layout schematics

The sketches use physical page sides only to explain RTL placement. In horizontal Persian, the right edge is normally inline-start and the left edge inline-end. Adapt the schematic to the content and design system.

## 1. RTL detail card, wide view

```text
physical right / inline-start                                  inline-end / physical left
┌───────────────────────────────────────────────────────────────────────────────────────┐
│ category + title + supporting copy                       │ image / visual             │
│ main values, kept near their labels                       │ stable ratio, safe crop    │
│ secondary information                                     │                            │
│ primary action                                             │                            │
└───────────────────────────────────────────────────────────────────────────────────────┘
```

Use a balanced two-track hero when the visual is central. For compact comparison, reduce the image and keep a clear text edge; do not shrink the title to preserve an arbitrary column width.

## 2. Compact comparison card

```text
┌──────────────────────────────────────────────────────────┐
│ category / status                              (optional) │
│ title                                                    │
│ short reason                                              │
│ ┌──────────────────────────────────────────────────────┐ │
│ │ named detail group: values / semantic chips           │ │
│ └──────────────────────────────────────────────────────┘ │
│ one primary action                                       │
└──────────────────────────────────────────────────────────┘
```

Across a row, align titles and actions where it helps comparison. Let each card grow for meaningful content; keep empty regions purposeful and restrained.

## 3. Mobile card alternatives

```text
Media-object (fast scanning)              Stacked hero (visual is primary)
┌──────────────────────────┐               ┌──────────────────────────┐
│ text on right │ image    │               │          image           │
│ title         │ at end   │               ├──────────────────────────┤
│ reason        │          │               │ category                 │
├──────────────────────────┤               │ title                    │
│ details and action       │               │ summary                  │
└──────────────────────────┘               │ details and action       │
                                             └──────────────────────────┘
```

Choose between these patterns by scan priority and image importance. A horizontal card is not automatically better on every phone width.

## 4. Numbered method or timeline

```text
RTL reading edge →
┌─────────────────────────────────────────────────────────┐
│ intro / context                                           │
├─────────────────────────────────────────────────────────┤
│ step copy                           [01]                 │
│ step copy continues on this edge                          │
│ ──────────────────────────────────────────────────────── │  divider begins after marker track
│ next step copy                       [02]                 │
└─────────────────────────────────────────────────────────┘
```

Give the marker a separate layout track. Maintain a visible gap between its edge and the copy. Keep the introduction visually separate from the first action.

## 5. Metrics with attached labels

```text
Wide:   ┌────────────┬────────────┬────────────┐
        │ label / 12 │ label / 08 │ label / 24 │
        └────────────┴────────────┴────────────┘

Narrow: ┌──────────────────┬──────────────────┐
        │ label / value     │ label / value    │
        ├──────────────────┼──────────────────┤
        │ label / value     │ supporting item  │
        └──────────────────┴──────────────────┘
```

Keep labels and values in the same cell. Change the number of columns when the real label length needs it.

## 6. Sticky tabs without clipped content

```text
┌ fixed app bar; measured height = H ─────────────┐
│ sticky tab strip; inset-block-start = H         │
├────────────────────────────────────────────────┤
│ destination heading; scroll margin ≥ H + tabs  │
│ target content                                  │
│ ...                                             │
│ final content clears fixed bottom navigation   │
└────────────────────────────────────────────────┘
```

Measure the real bars, use one shared offset, and check both the stuck and unstuck states.
