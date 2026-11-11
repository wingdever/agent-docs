# ai knowledge spine index
20 phases 542 lessons 250 glossary terms
## 0. setup & tooling
## 1. math foundations
## 2. ML fundamentals
## 3. deep learning core
## 4. computer vision
## 5. NLP: foundations to advanced
## 6. speech & audio
## 7. transformers deep dive
## 8. generative AI
## 9. reinforcement learning
## 10. LLMs from scratch
## 11. LLM engineering
## 12. multimodal AI
## 13. tools & protocols
## 14. agent engineering
## 15. autonomous systems
## 16. multi-agent & swarms
## 17. infrastructure & production
## 18. ethics, safety & alignment
## 19. capstone projects

# 0. setup & tooling
00.01 dev environment
00.02 git & collaboration
00.03 GPU setup & cloud
00.04 APIs & Keys
00.05 jupyter Notebooks
00.06 python environment
00.07 docker for AI
00.08 editor setup
00.09 data management
00.10 terminal & shell
00.11 linux for AI
00.12 debugging & profiling
00.13 python for AI engineering
# 1. math foundations
01.01 linear algebra intuition
01.02 vectors, matrices & operations
01.03 matrix transformations & eigenvalues
01.04 calculus for ML: derivatives & gradients
01.05 chain rule & automatic differentiation
01.06 probability & distributions
01.07 bayes'theorem & statistical thinking
01.08 optimization: gradient descent family
01.09 information theory: entropy, KL divergence
01.10 dimensionality reduction: PCA, t-SNE, UMAP
01.11 singular value decomposition
01.12 tensor operations
01.13 numerical stability
01.14 norms & distances
01.15 statistics for ML
01.16 sampling methods
01.17 linear systems
01.18 convex optimization
01.19 complex numbers for AI
01.20 the fourier transform
01.21 graph theory for ML
01.22 stochastic processes
# 2. ML fundamentals
02.01 what is Machine Learning
02.02 linear regression from scratch
02.03 logistic regression & classification
02.04 decision trees & random forests
02.05 support vector machines
02.06 KNN & distance metrics
02.07 Unsupervised Learning: K-Means, DBSCAN
02.08 feature engineering & selection
02.09 model evaluation: metrics, cross-validation
02.10 bias, variance & the learning curve
02.11 ensemble methods: boosting, bagging, stacking
02.12 hyperameter tuning
02.13 ML pipelines & experiment tracking
02.14 naive bayes
02.15 time series fundamentals
02.16 anomaly detection
02.17 handling imbalanced data
02.18 feature selection
02.19 ML system design - from problem to deployed model
02.20 monitoring models in production - data drift and concept drift
02.21 feature stores and training-serving skew
# 3. deep learning core
03.01 the perceptron: where is all started
03.02 multi-layer networks & forward pass
03.03 backpropagation from scratch
03.04 activation functions: ReLU, sigmoid, GELU & why
03.05 loss functions: MSE, cross-entropy, contrastive
03.06 optimizers: SGD, momentum, adam, adamW
03.07 regularization: dropout, weight decay, batch-norm
03.08 weight initialization & training stability
03.09 learning rate schedules & warmup
03.10 build your own mini framework
03.11 introduction to pytorch
03.12 introduction to JAX
03.13 debugging neural networks
# 4. computer vision
04.01 image fundametals: pixels, channels, color spaces
04.02 convolutions from scratch
04.03 CNNs: LeNet to ResNet
04.04 image classification
04.05 transfer learning & fine-tuning
04.06 object detection - YOLO from scratch
04.07 semantic segmentation - U-Net
04.08 instance segmentation - mask R-CNN
04.09 image generation - GANs
04.10 image generation - diffusion models
04.11 stable diffusion - architecture & fine-tuning
04.12 video understanding - temporal modeling
04.13 3d vision: point clouds, NeRFs
04.14 vision transformers(ViT)
04.15 real-time vision: edge deployment
04.16 build a complete vision pipeline
04.17 self-supervised vision - SimCLR, DINO, MAE
04.18 open-vocabulary vision - CLIP
04.19 OCR & Document Understanding
04.20 image retrieval & metric learning
04.21 keypoint detection & pose estimation
04.22 3d gaussian splatting from scratch
04.23 diffusion transformers & rectified flow
04.24 SAM 3 & open-vacabulary segmentation
04.25 vision-language models (ViT-MLP-LLM)
04.26 monocular depth & geometry estimation
04.27 multi-object tracking & video memory
04.28 world models & video diffusion
# 5. NLP: foundations to advanced
05.01 text processing: tokenization, stemming, lemmatization
05.02 bag of words, TF-IDF & text representation
05.03 word embeddings: word2vec from scratch
05.04 GloVe, FastText & Subword embeddings
05.05 sentiment analysis
05.06 named entity recognition (NER)
05.07 POS tagging & syntactic parsing
05.08 text classification - CNNs & RNNs for text
05.09 sequence-sequence models
05.10 attention mechanism - the breakthrough
05.11 machine translation
05.12 text summarization
05.13 question answering systems
05.14 information retrieval & search
05.15 topic modeling: LDA, BERTopic
05.16 text generation
05.17 chatbots: rule-based to neural
05.18 multilingual NLP
05.19 subword tokenization: BPE, wordPiece, unigram, sentencePiece
05.20 structured outputs & constrained decoding
05.21 NLI & textual entailment
05.22 embedding models deep dive
05.23 chunking strategies for RAG
05.24 coreference resolution
05.25 entity linking & disambiguation
05.26 relation extraction & knowledge graph construction
05.27 LLM evaluation: RAGAS, DeepEval, G-Eval
05.28 Long-Context Evaluation: NIAH, RULER, longBench, MRCR
05.29 dialogue state tracking
# 6. speech & audio
06.01 audio fundamentals: waveforms, sampling, FFT
06.02 spectrograms, Mel Scale & audio features
06.03 audio classification
06.04 speech recognition (ASR)
06.05 Whisper: architecture & fine-tuning
06.06 speaker recognition & verification
06.07 text-to-speech (TTS)
06.08 voice cloning & voice conversion
06.09 music generation
06.10 audio-language models
06.11 real-time audio processing
06.12 build a voice assistant pipeline
06.13 neural audio codecs - EnCodec, SNAC, Mimi, DAC
06.14 voice activity detection & turn-taking
06.15 streaming speech-to-speech - Moshi, Hibiki
06.16 voice anti-spoofing & audio watermarking
06.17 audio evaluation - WER, MOS, MMAU, Leaderboards
# 7. transformers deep dive
07.01 why transformers: the problems with RNNs
07.02 self-attention from scratch
07.03 multi-head attention
07.04 positional encoding: sinusoidal, RoPE, ALiBi
07.05 the full transformer: encoder + decoder
07.06 BERT - masked language modeling
07.07 GPT - causal language modeling
07.08 T5, BART - encoder-decoder models
07.09 vision transformers (ViT)
07.10 audio transformers - whisper architecture
07.11 mixture of experts (MoE)
07.12 KV Cache, Flash Attention & Inference Optimization
07.13 Scaling Laws
07.14 build a transformer from scratch
07.15 attention variants - sliding window, sparse, differential
07.16 speculative decoding - draft, verify, repeat
# 8. generative AI
08.01 generative models: taxonomy & history
08.02 autoencoders & VAE
08.03 GANs: generator vs discriminator
08.04 conditional GANs & pix2pix
08.05 styleGAN
08.06 diffusion models - DDPM from scratch
08.07 latent diffusion & stable diffusion
08.08 controlNet, LoRA & conditioning
08.09 inpainting, outpainting & editing
08.10 video generation
08.11 audio generation
08.12 3d generation
08.13 flow matching & rectified flows
08.14 evaluation: FID, CLIP score
08.19 visual autoregressive modeling(VAR): next-scale prediction 
# 9. reinforcement learning
09.01 MDPs, states, actions & rewards
09.02 dynamic programming
09.03 monte carlo methods
09.04 Q-learning, SARSA
09.05 deep Q-networks (DQN)
09.06 policy gradients - REINFORCE
09.07 actor-critic - A2C, A3C
09.08 PPO
09.09 reward modeling & RLHF
09.10 multi-agent RL
09.11 Sim-to-Real transfer
09.12 RL for games
# 10. LLMs from scratch
10.01 tokenizers: BPE, wordPiece, sentencePiece
10.02 build a tokenizer from scratch
10.03 data pipielines for pre-training
10.04 pre-training a mini GPT(124M)
10.05 distributed training, FSDP, deepSpeed
10.06 instruction tuning - SFT
10.07 RLHF - reward model + PPO
10.08 DPO - direct preference optimization
10.09 constitutional AI & self-improvement
10.10 evaluation - benchmarks, evals
10.11 quantization: INT8, GPTQ, AWQ, GGUF
10.12 inference optimization
10.13 building a complete LLM pipeline
10.14 open models: architecture walkthroughs
10.15 speculative decoding and EAGLE-3
10.16 differential attention (V2)
10.17 native sparse attention (DeepSeek NSA)
10.18 multi-token prediction (MTP)
10.19 dualpipe parallelism
10.20 DeepSeek-V3 architecture walkthrough
10.21 Jamba - Hybrid SSM-transformer
10.22 Async and Hogwild Interface
10.25 speculative decoding and EAGLE
10.34 gradient checkpointing and activation recomputation
# 11. LLM engineering
11.01 prompt engineering: techniques & patterns
11.02 few-shot, CoT, Tree-of-Thought
11.03 structured outputs
11.04 embeddings & vector representation
11.05 context engineering
11.06 RAG: retrieval-augmented generation
11.07 advanced RAG: chunking, reranking
11.08 fine-tuning with LoRA & QLoRA
11.09 function calling & tool use
11.10 evaluation & testing
11.11 caching, rate limiting & cost
11.12 guardrails & safety
11.13 building a production LLM app
11.14 model context protocol (MCP)
11.15 prompt caching & context caching
11.16 agent state machines - graphs, nodes, checkpoints
11.17 agent framework tradeoffs
# 12. multimodal AI
12.01 vision transformers and the patch-token primitive
12.02 CLIP and contrastive vision-language pretraining
12.03 BLIP-2 Q-Former as modality bridge
12.04 flamingo and gated cross-attention
12.05 LLaVA and Visual Instruction Tuning
12.06 Any-Resolution vision - Patch-n'-Pack and NaFlex
12.07 open-weight VLM recipes: what actually matters
12.08 LLaVA-OneVision: Single, Multi, Video
12.09 Qwen-VL family and dynamic-FPS video
12.10 internVL3 native multimodal pretraining
12.11 chameleon early-fusion token-only
12.12 Emu3 next-token prediction for generation
12.13 transfusion autoregressive + diffusion
12.14 show-o discrete-diffusion unified
12.15 janus-pro decoupled encoders
12.16 MIO any-to-any streaming
12.17 video-language temporal grounding
12.18 long-video at million-token context
12.19 audio-language models: whisper to AF3
12.20 Omni models: thinker-talker streaming
12.21 embodied VLAs: RT-2, OpenVLA, pi0, GROOT
12.22 Document and diagram understanding
12.23 ColPali Vision-Native Document RAG
12.24 multimodal RAG and cross-modal retrieval
12.25 multimodal agents and computer-use (capstone)
# 13. tools & protocols
13.01 the tool interface
13.02 function calling deep dive
13.03 parallel and streaming tool calls
13.04 structured output
13.05 tool schema design
13.19 A2A protocol
13.20 openTelemetry GenAI
13.21 LLM routing layer
13.22 agent skills: portable contract and runtime boundary
13.23 capstone: stateless tool ecosystem
## skill
13.24 skill discovery and progressive disclosure
13.25 skill invocation and routing
13.26 skill evals, packaging, and portability
## mcp
13.06 fundamentals: stateless requests and json-rpc
13.07 server build: stateless python and typescript
13.08 client build: discovery, routing and dual-era fallback
13.09 transports: stdio and stateless streamable HTTP
13.10 resources and prompts: addressable context for stateless servers
13.11 model input: sampling migration and stateless MRTR state
13.12 explicit scope and stateless protocol
13.13 tasks extension: durable work on a stateless core
13.14 apps on the stateless protocol
13.15 security: poisoned metadata, routing, and MRTR state
13.16 authorization: CIMD, Issuer binding, and PKCE state
13.17 stateless gateways and registry admission
13.18 auth in production: Issuer-Bound enrollment and tokens
13.28 mcp tool contracts and content
13.29 mcp reliability, cancellation, and flow control
13.30 mcp registry supply chain: admission, drift, and rollback
13.31 mcp conformance engineering: versioning, evidence, operations
## reverse-engineer
13.32 program anatomy: an ELF reader from scratch
13.33 disassembly and control flow: from bytes to graph can check
13.34 lifting to pseudocode: IR, SSA, Structuring from scratch
13.35 evidence, confidence, and Unknowns in binary analysis
13.36 rebuild and prove equal:
      differential tests, byte comparison, evidence loop
13.37 the reverse engineering landscape:
      history, tool families, how decompiler is built
13.38 calling conventions and stack frames:
      system V, windows x64, AArch64
13.39 compiler idioms:
      what optimization does to your code and how to read it back
13.40 linking, loading, and stripped binaries:
      PLT, GOT, imports, fixups, and function identification
13.41 recovering data and types:
      structs, arrays, C++ objects, and DWARF
13.42 dynamic analysis of your own program:
      debuggers, traces, and confirming static claims
13.43 beyond native code:
      python, JVM, .net, and webAssembly bytecode
13.44 binary diffing and symbolic execution:
      matching functions and solving for inputs
13.45 ai-assisted reverse engineering:
      LLM decompilers, analysis agents, and ground truth
# 14. agent engineering
14.01 the agent loop
14.02 ReWOO and plan-and-execute
14.03 reflexion and verbal reinforcement learning
14.04 tree of thoughts and LATS
14.05 self-refine and CRITIC
14.06 tool use and function calling
14.07 agent memory - virtual context and memory paging
14.08 memory blocks and sleep-time compute
14.09 hybrid memory - vector + graph + KV
14.10 skill libraries and lifelong learning (Voyager)
14.11 planning with HTN and evolutionary search
14.12 anthropic's workflow patterns
14.13 stateful graph orchestrate - durable execution and checkpoints
14.14 the actor model for agents
14.15 role-based agent teams - roles, tasks, processes
14.16 openAI agents SDK - handoffs, guardrails, tracing
14.17 the harness as a library - subagents and session store
14.18 production agent runtimes
14.19 benchmarks - SWE-bench, GAIA, agentBench
14.20 benchmarks - webArena and OSWorld
14.21 computer use - claude, openAI CUA, Gemini
14.22 voice agents - pipecat and liveKit
14.23 openTelemetry GenAI semantic conventions
14.24 agent observability - langfuse, phoenix, Opik
14.25 multi-agent debate and collaboration
14.26 failure models - why agents break
14.27 prompt injection and the PVE Defense
14.28 orchestration patterns - supervisor, swarm, hierarchical
14.29 production runtimes - queue, event, cron
14.30 eval-driven agent development
14.31 agent workbench: why capable models still fail
14.32 the minimal agent workbench
14.33 agent instructions as execuable constraints
14.34 repo memory and durable state
14.35 initialization scripts for agents
14.36 scope contracts and task boundaries
14.37 runtime feedback loops
14.38 verification gates
14.39 reviewer agent: separate builder from marker
14.40 multi-session handoff
14.41 the workbench on a real repo
14.42 capstone: ship a reused agent workbench pack
14.43 frame the task before the agent writes code
14.44 build an evidence-backed execution plan
14.45 delegate agent work with isolation and merge contracts
14.46 turn every agent correction into a system improvement
14.47 define the outcome before you choose the output
14.48 discover the workflow people actually perform
14.49 map assumptions and resolve the riskiest one first
14.50 choose the smallest slice that can change the decision
14.51 write specifications that preserve judgment
14.52 design success metrics before the result exists
14.53 choose prototype, Pilot, or production deliberately
14.54 build a feedback ratchet with ownership and retirement
# 15. autonomous systems
15.01 from chatbots to long-horizon agents (METR)
15.02 STaR, V-STaR, Quiet-STaR: self-taught reasoning
15.03 alphaEvolve: Evolutionary coding agents
15.04 Darwin Godel Machine: self-modifying agents
15.05 AI scientist v2: workshop-level research
15.06 automated alignment research (anthropic AAR)
15.07 recursive self-improvement: capability vs alignment
15.08 bounded self-improvement designs
15.09 autonomous coding agent landscape (SWE-bench, CodeAct)
15.10 permission models for autonomous agents
15.11 browser agents and indirect prompt injection
15.12 durable execution for long-running agents
15.13 action budgets, iteration caps, cost governors
15.14 kill switches, circuit breakers, canary tokens
15.15 HITL: propose-then-commit
15.16 checkpoints and rollback
15.17 constitutional AI and rule overrides
15.18 llama guard and input/output classification
15.19 anthropic responsible scaling policy v3.0
15.20 openAI preparedness framework and deepmind FSF
15.21 METR time horizons and external evaluation
15.22 CAIS, CAISI, and Societal-Scale Risk
# 16. multi-agent & swarms
16.01 why multi-agent
16.02 FIPA-ACL heritage and speech acts
16.03 communication protocols
16.04 the multi-agent primitive model
16.05 supervisor / orchestrator-worker pattern
16.06 hierarchical architecture and decomposition drift
16.07 society of mind and multi-agent debate
16.08 role specialization - planner / critic / executor / verifier
16.09 parallel swarm and networked architectures
16.10 group chat and speaker selection
16.11 handoffs and routines (stateless orchestration)
16.12 a2a - the agent-to-agent protocol
16.13 shared memory and blackboard patterns
16.14 consensus and byzantine fault tolerance
16.15 voting, self-consistency, and debate topology
16.16 negotiation and bargaining
16.17 generative agents and emergent simulation
16.18 theory of mind and emergent coordination
16.19 swarm optimization (PSO, ACO)
16.20 MARL - MADDPG, QMIX, MAPPO
16.21 agent economies, token incentives, reputation
16.22 production scaling - queues, checkpoints, durability
16.23 failure modes - MAST, groupthink, monoculture
16.24 evaluation and coordination benchmarks
16.25 case studies and 2026 state of the art
# 17. infrastructure & production
17.01 managed LLM platforms - bedrock, azure openAI, vertex AI
17.02 inference platform economics
       - fireworks, together, baseten, modal
17.03 gpu autoscaling on kubernetes - karpenter, KAI scheduler
17.04 serving engine internals
       - pagedAttention, Continous Batching, chunked prefill
17.05 EAGLE-3 speculative decoding in production
17.06 prefix-cache serving - radixAttention and KV reuse
17.07 hardware-specialized inference compilation
       - FP8 and NVFP4 on blackwell
17.08 inference metrics - TTFT, TPOT, ITL, Goodput, P99
17.09 production quantization - AWQ, GPTQ, GGUF, FP8, NVFP4
17.10 cold start mitigation for serverless LLMs
17.11 multi-region LLM serving and KV cache locality
17.12 edge inference - ANE, Hexagon, webGPU, Jetson
17.13 LLM observability stack selection
17.14 prompt caching and semantic caching economics
17.15 batch APIs - the 50% discount as industry standard
17.16 model routing as a cost-reduction primitive
17.17 disaggregated prefill/decode - NVIDIA dynamo and llm-d
17.18 production serving stack - KV offloading and cache-aware routing
17.19 AI gateways - LiteLLM, portkey, Kong, Bifrost
17.20 shadow, canary, and progressive deployment
17.21 A/B testing LLM features - growthbook and statsig
17.22 load testing LLM APIs - k6, LLMPerf, GenAI-Perf
17.23 SRE for AI - multi-agent incident response
17.24 chaos engineering for LLM production
17.25 security - secrets, PII scrubbing, audit logs
17.26 compliance - SOC 2, HIPAA, GDPR, EU AI Act, ISO 42001
17.27 FinOps for LLMs - unit economics and multi-tenant attribution
17.28 self-hosted serving selection
       - matching engine to hardware and scale
17.29 model demo interfaces - from a function to a shareable app
# 18. ethics, safety & alignment
18.01 instruction-following as alignment signal
18.02 reward hacking & goodhart's law
18.03 direct preference optimization family
18.04 sycophancy as RLHF amplification
18.05 constitutional AI & RLAIF
18.06 mesa-optimization & deceptive alignment
18.07 sleeper agents - persistent deception
18.08 in-context scheming in frontier models
18.09 alignment faking
18.10 AI control - safety despite subversion
18.11 scalable oversight & weak-to-strong
18.12 red-teaming: PAIR & automated attacks
18.13 many-shot jailbreaking
18.14 ASCII art & visual jailbreaks
18.15 indirect prompt injection
18.16 red-team tooling: garak, llama guard, pyRIT
18.17 WMDP & dual-use capability evaluation
18.18 frontier safety frameworks - RSP, PF, FSF
18.19 model welfare research
18.20 bias & representational harm
18.21 fairness criteria: group, individual, counterfactual
18.22 differential privacy for LLMs
18.23 watermarking: synthID, stable signature, C2PA
18.24 regulatory frameworks: EU, US, UK, Korea
18.25 EchoLeak & CVEs for AI
18.26 model, system & dataset cards
18.27 data provenance & training-data governance
18.28 alignment research ecosystem: MATS, Redwood, Apollo, METR
18.29 moderation systems: openAI, perspective, llama guard
18.30 dual-use risk: cyber, bio, chem, nuclear
# 19. capstone projects
19.01 terminal-native coding agent
19.02 RAG over codebase (cross-repo semantic search)
19.03 real-time voice assistant (ASR->LLM->TTS)
19.04 multimodal document QA (vision-first)
19.05 autonomous research agent (ai-scientist class)
19.06 DevOps troubleshooting agent for Kubernetes
19.07 end-to-end fine-tuning pipeline
19.08 production RAG chatbot (regulated vertical)
19.09 code migration agent (repo-level upgrade)
19.10 multi-agent software engineering team
19.11 LLM obervability & Eval dashboard
19.12 video understanding pipeline (Scene -> QA)
19.13 stateless MCP server with registry and governance
19.14 speculative-decoding inference server
19.15 cpnstitutional safety harness + red-team range
19.16 github issue-to-pr autonomous agent
19.17 personal AI tutor (adaptive, multimodal)
19.20 agent harness loop contract
19.21 tool registry with schema validation
19.22 json-rpc 2.0 over newline-delimited stdio
19.23 function call dispatcher
19.24 plan-execute control flow
19.25 verification gates and observation budget
19.26 sandbox runner with denylist and path jail
19.27 eval harness with fixture tasks
19.28 observability with OTel GenAI Spans and prometheus metrics
19.29 end-to-end coding agent on the harness
19.30 BPE tokenizer from scratch
19.31 tokenized dataset with sliding window
19.32 token and positional embeddings
19.33 multi-head self-attention
19.34 transformer block from scratch
19.35 GPT model assembly
19.36 training loop and evaluation
19.37 loading pretrained weights
19.38 classifier fine-tuning by head swap
19.39 instruction tuning by supervised fine-tuning
19.40 direct preference optimization from scratch
19.41 full evaluation pipeline
19.42 large-corpus downloader
19.43 HDF5 tokenized corpus
19.44 cosine LR with linear warmup
19.45 gradient clipping and mixed precision
19.46 gradient accumulation
19.47 checkpoint save and resume
19.48 distributed data parallel and FSDP from scratch
19.49 language model evaluation harness
19.50 hypothesis generator
19.51 literature retrieval
19.52 experiment runner
19.53 result evaluator
19.54 paper writer
19.55 critic loop
19.56 iteration scheduler
19.57 end-to-end research demo
19.58 vision encoder patches
19.59 vision transformer encoder
19.60 projection layer for modality alignment
19.61 cross-attention fusion
19.62 vision-language pretraining
19.63 multimodal evaluation
19.64 chunking strategies, compared
19.65 hybrid retrieval with BM25 and Dense embinddings
19.66 cross-encoder reranker
19.67 query rewriting: HyDE, multi-query, and decomposition
19.68 RAG eval: precision,recall,MRR,nDCG,faithfull,relevant
19.69 end-to-end RAG system
19.70 task spec format
19.71 classical metrics
19.72 code exec metric
19.73 perplexity and calibration
19.74 leaderboard aggregation
19.75 end-to-end eval runner
19.76 collective ops from scratch
19.77 data parallel DDP from scratch
19.78 ZeRO optimizer state sharding
19.79 pipeline parallel and bubble analysis
19.80 sharded checkpoint and atomic resume
19.81 end-to-end distributed training
19.82 jailbreak taxonomy
19.83 prompt injection detector
19.84 refusal evaluation
19.85 content classifier integrarion
19.86 constitutional rules engine
19.87 end-to-end safety gate