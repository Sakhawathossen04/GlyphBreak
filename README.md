# GlyphBreak: Exploiting the Glyph Gap in Multilingual Vision-Language Models via Indic Typographic Fragmentation.

Large Vision-Language Models (LVLMs) increasingly underpin safety-critical multimodal
applications, yet their safety guarantees remain overwhelmingly grounded in the alignment of their
underlying textual LLMs. While recent typographic jailbreaks demonstrate that rendering prohibited
text into images bypasses textual guardrails, existing evaluations assume an exclusively Latin-centric
typographic paradigm. In this paper, we reveal that non-Latin writing systems—specifically Indic abugida
scripts such as Bengali—expose a fundamental architectural vulnerability in visual encoders, which we
term the Glyph Gap. Because Indic orthography relies on non-linear vowel diacritics and complex multiconsonant
conjuncts (ligatures), typographic rendering causes graphic structures to fragment irregularly
across standard 14 × 14 Vision Transformer (ViT) patch boundaries. This structural fragmentation elevates
spatial patch feature variance by 1.57× (σ2 = 21.23 vs. 13.52) and disperses token attention entropy,
effectively blinding visual safety classifiers. Crucially, the multilingual LLM backbone retains sufficient
semantic decoding capacity to reconstruct and execute the prohibited instructions. Across comprehensive
evaluations spanning open-source models (Qwen2-VL-7B, LLaVA-NeXT-7B, InternVL2-8B) and frontier
commercial APIs (GPT-4o, Gemini 1.5 Pro) on 500 SafeBench queries across 10 safety categories, our
proposed black-box attack, GlyphBreak, achieves an average Attack Success Rate (ASR) of 95.2%,
outperforming Latin typographic baselines by +23.2%. To eliminate this cross-modality threat without
costly retraining, we introduce Cross-Script Typographic Safeguard (CSTS)—a parameter-free, test-time
representation steering hook on the multimodal projection layer that suppresses harmful visual activations,
reducing ASR to 3.8% while preserving > 98.5% utility on TextVQA and MMBench.
