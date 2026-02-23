---
Health: 4
Wealth: 5
Relationship: 3
Sprituality: 6
list: []
---
## {{date:[Week] ww}} [[{{date:YYYY-MM}}|🪴]] {{date:MMM gggg}}


🌲 [[<% moment(tp.file.title, "YYYY-ww").subtract(1, "weeks").format("YYYY-ww") %>]] | [[<% moment(tp.file.title, "YYYY-[W]ww").add(1, "weeks").format("YYYY-ww") %>]] 🌲


S [[{{sunday:YYYY-MM-DD}}|{{sunday:DD}}]] · M [[{{monday:YYYY-MM-DD}}|{{monday:DD}}]] · T [[{{tuesday:YYYY-MM-DD}}|{{tuesday:DD}}]] · W [[{{wednesday:YYYY-MM-DD}}|{{wednesday:DD}}]] · T [[{{thursday:YYYY-MM-DD}}|{{thursday:DD}}]] · F [[{{friday:YYYY-MM-DD}}|{{friday:DD}}]] · S [[{{saturday:YYYY-MM-DD}}|{{saturday:DD}}]] ^{{date:ww}}

### Life Balance

```meta-bind
INPUT[progressBar(title(Health), minValue(0), maxValue(10)):Health]
```
```meta-bind
INPUT[progressBar(title(Wealth), minValue(0), maxValue(10)):Wealth]
```
```meta-bind
INPUT[progressBar(title(Relationship), minValue(0), maxValue(10)):Relationship]
```
```meta-bind
INPUT[progressBar(title(Sprituality), minValue(0), maxValue(10)):Sprituality]
```

### What has been Accomplished?

```meta-bind
INPUT[list(title(Wins This Week)):list]
```

---
### What Next?
