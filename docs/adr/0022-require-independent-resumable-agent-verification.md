# Require independent resumable agent verification

An implementation agent cannot certify its own task: an independent verification agent evaluates the code, tests, and acceptance evidence, and the final test agent re-executes the development baseline's complete workflows. Each agent run retains resumable checkpoints, inputs, model and platform identity, tool activity, changes, tests, costs, and failures so execution can survive process restarts and an FDE can pause, reassign, or take over work without losing its audit trail.
