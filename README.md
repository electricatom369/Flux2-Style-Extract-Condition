# Flux2-Style-Extract-Condition
Claude coded
The node injects the CLIP vision embedding as a prefix token on the conditioning sequence rather than replacing or averaging it. This means your text prompt stays fully intact — the style signal rides alongside it and attention does the blending naturally. The style_strength slider just scales that prefix token's magnitude.


Three projection modes let you choose how patches are pooled — patch_mean is the default and works well for photographic style references. penultimate_mean is worth trying if you want richer texture/colour capture.


One thing to flag: Flux2 Klein 9B uses a dual text encoder (T5 + CLIP-L), so the conditioning embed dim is typically 4096. If your CLIP Vision model outputs a different dim (e.g. SigLIP at 1152), the node zero-pads up to match — this is intentional and avoids needing a trained projection layer, but it does mean some dimensions are empty. A proper learned projection would give cleaner results; happy to add that if you want to take it further.

IN PROGRESS
