# Worked sample (historical)

Upstream designRun shipped a fictional `projects/relay-sample/` product to show how sources work together. This fork has removed that sample. Keep this note as the historical removal how-to; do not recreate the sample unless you intentionally want teaching material.

## Remove the sample (if reintroduced)

Delete `projects/relay-sample/`, then remove any `sample-relay-*` objects from the JSON array in `knowledge/todos.md`. Run `npm run validate && npm run index`. The control center will return to a clean first-project state.

