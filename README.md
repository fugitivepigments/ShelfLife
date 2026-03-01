# Shelf-Life Preservation Survey Sampler

A lightweight, browser-based tool for planning statistically grounded preservation condition surveys in libraries, archives, and special collections.

This project recreates a core planning function of the historic CALIPR preservation assessment workflow: estimating a statistically valid sample and generating randomized physical stack locations for survey work.

## Features

- Calculates a target sample size using:
  - collection size
  - selectable confidence level
  - user-defined margin of error
  - finite population correction
- Adjusts planned draws based on estimated occupancy
- Generates:
  - random-order CSV
  - walking-order CSV
  - top-up batch CSV
  - methods note
- Supports:
  - repeating bay-per-side patterns
  - range-specific bay overrides
- Runs entirely in the browser
- Requires no installation or server

## Intended Use

This tool is intended for planning collection condition surveys where:

- the collection is too large for item-by-item review
- staff need a statistically informed sample
- physical stack locations must be generated transparently and reproducibly
- the workflow must remain practical to execute in real space

## How It Works

The tool models shelving locations using:

- Range
- Side
- Bay
- Shelf
- Item

It estimates a statistically valid sample using a conservative proportion (`p = 0.5`) and finite population correction, then inflates the number of generated rows based on occupancy to account for likely misses.

## Basic Workflow

1. Open `index.html` in a modern browser.
2. Enter collection size, confidence level, margin of error, occupancy, and stack layout.
3. Click **Generate sample**.
4. Download the random-order and/or walking-order CSV files.
5. Attempt every row in the generated batch.
6. If too many rows are unusable, generate a **top-up batch** with a new seed.

## Sampling Guidance

- The tool uses a conservative variability assumption (`p = 0.5`).
- Lower margins of error require larger samples.
- Lower occupancy results in more planned draws.
- To avoid bias, do **not** stop partway through a generated list.
- If additional rows are needed, use a separate top-up batch.

## Limitations

This tool does not currently:

- track misses during fieldwork
- dynamically replace unusable rows
- support variable shelf counts within the same bay
- model drawers, map cases, or boxed storage without adapting the stack logic

## Development Notes

The app is a single-file HTML tool with embedded CSS and JavaScript for easy deployment via GitHub Pages.

Built-in browser console self-tests check:

- pattern parsing
- range override parsing
- sample size calculation
- stack map generation
- location mapping

## Acknowledgment

This tool is inspired by the preservation survey-planning logic documented in the original CALIPR project developed through the University of California in the 1980s-1990s.
## License

See `LICENSE`.
