This experiment measures two things about a transformer model’s residual stream by restricting what a layer is allowed to read, and scoring the damage as KL against the full model:

- the reading pattern (does a layer read by distance or by absolute depth — for example, does it read a block of early layers regardless of how far away they are?)
- repair (when one layer’s write is hidden from one reader layer, how much of the loss do the later layers make good?).

Instruments (in tools/):

- run.py: the main testing instrument (window, pairs, storage, sinks, attention-on-BOS modes; 4-bit loading; profile-matched random controls)
- paper_tables.py: regenerates every table in the paper from them.

Models tested: Llama-2/3.1, CodeLlama, Mistral, Qwen2.5/3/3.5, OLMo-2, Gemma-2/3, GLM-4, Falcon, 1B–70B.

The tests were done on a single RTX 3090. All runs are in results/ as JSONL files.
