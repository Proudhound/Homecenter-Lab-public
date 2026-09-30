# Architecture overview

```text
Family
  │
  ├── Family dashboard
  └── optional local voice clients
          │
          ▼
    Home Assistant
          │
  ┌───────┼─────────────────────┐
  │       │                     │
Calendar  Home / IoT systems   House services
Shopping  Energy / climate     Search / AI
Weather   Security / network   Documentation
  │       │                     │
  └───────┴──────► HomeCenter ◄─┘
```

## Architectural rule
Home control and experimental development workloads are operated separately. Experimental AI or development services must not become a single point of failure for basic home functions.
