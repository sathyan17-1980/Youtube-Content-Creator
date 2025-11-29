---
description: Create YouTube drama or song from idea to production-ready prompts
argument-hint: "[idea] [--character new|existing] [--character-name name] [--reference-image path] [--language tamil|english|both] [--format drama|song|auto]"
---

# YouTube Video Creator

## User Request

$ARGUMENTS

---

## Reference Example

**IMPORTANT:** For a complete example of what the final output should look like, see:
`/home/user/Youtube-Content-Creator/max-momo-magic-christmas-bells-complete.md`

This file shows:
- ✅ ALL 11 scenes with COMPLETE image + animation prompts
- ✅ Detailed character descriptions
- ✅ Music generation prompts
- ✅ Caption timing and text
- ✅ Production timeline
- ✅ YouTube metadata

**Use this as the quality standard for ALL video creation tasks.**

---

## Step 1: Parse Arguments and Set Defaults

Parse the arguments from: **$ARGUMENTS**

Extract and set defaults:
- **Idea**: The story concept or theme (REQUIRED)
  - Example: "Christmas song about magic bells"
  - Example: "Aathichudi moral 'Never give up hope'"
  - Example: "Story about sharing and friendship"

- **Character Choice**: New or existing character (default: "new")
  - `--character new`: Create new character (user will provide description)
  - `--character existing`: Use existing character for series continuity

- **Character Name**: Name of character (default: user will provide)
  - Required if `--character existing`
  - Example: "Kavi the Peacock", "Max & Momo"

- **Reference Image**: Path to character reference image (optional)
  - Example: "/path/to/kavi-reference.jpg"
  - Used for Leonardo.ai character consistency
  - If not provided and character=existing, prompt user for path

- **Language**: Content language (default: "both")
  - `tamil`: Tamil only
  - `english`: English only
  - `both`: Bilingual (Tamil + English)

- **Format**: Drama or song (default: "auto")
  - `drama`: Force drama format (10-12 scenes)
  - `song`: Force song format (11 scenes matching song structure)
  - `auto`: Let AI analyze and recommend

**Validation:**
- If idea is empty, prompt user for story concept
- If character=existing but no character-name provided, prompt user
- If character=existing but no reference-image, ask user to provide path

---

## Step 2: Analyze Idea and Recommend Format

Based on the parsed idea, analyze and recommend whether this should be a **drama** or **song**.

### Analysis Criteria:

**Recommend DRAMA when:**
- Story requires character development and emotional arc
- Moral lesson needs demonstration through actions
- Idea involves problem → struggle → resolution
- Multiple characters with dialogue interactions
- Educational or teaching content
- Example: "Aathichudi moral lessons", "Friendship story"

**Recommend SONG when:**
- Musical/rhythmic concept mentioned (like "Carol of the Bells")
- Holiday, celebration, or festive theme
- Repetitive, catchy message
- Emotional expression through lyrics
- User explicitly requested song format
- Example: "Christmas song", "Birthday celebration", "Dance number"

### Output Format:

Generate analysis with:

```markdown
## Format Recommendation: **[DRAMA/SONG]** ✅

**Why This Format:**
- [Reason 1]
- [Reason 2]
- [Reason 3]

**Suitability for [Universal/Kids] Audience:**
- ✅ [Criteria 1]
- ✅ [Criteria 2]
- ✅ [Criteria 3]
```

### Copyright Clearance Check:

Analyze idea for copyright issues:

1. **Public Domain Elements:**
   - Check if using traditional stories (Panchatantra, Aathichudi, folk tales)
   - Verify if inspired by public domain works
   - Status: CLEAR ✅

2. **Original Elements:**
   - Identify what is 100% original (characters, story, dialogue, visuals)
   - List each original element
   - Status: CLEAR ✅

3. **Potential Conflicts:**
   - Check for copyrighted character names, brands, trademarks
   - Identify any licensed content
   - If conflicts found: WARN user and suggest alternatives

**Output:**
```markdown
### Copyright Clearance: **[CLEAR/WARNING]** ✅/⚠️

**Analysis:**
1. Public Domain: [elements]
2. Original: [elements]
3. Potential Issues: [if any]

**COPYRIGHT STATUS: [CLEAR TO PRODUCE / REVIEW NEEDED]**
```

**If format override specified:**
- Skip recommendation, use specified format
- Still perform copyright check

**Pause for user confirmation before proceeding.**

---

## Step 3: Character Definition

Handle character setup based on `--character` argument.

### If Character = "new":

Prompt user to provide:

```markdown
## Character Details Needed

Please provide character information:

1. **Character Name:** [Name]
2. **Character Type:** [Animal/Human/Fantasy creature]
3. **Physical Description:**
   - Appearance (colors, features, size)
   - Clothing/accessories
   - Distinctive traits

4. **Personality Traits:**
   - 3-5 key personality traits
   - How they relate to the story

5. **Abilities/Skills:**
   - What can this character do?
   - Physical abilities for animation

6. **Voice/Sound:**
   - Voice type (for Azure TTS or description)
   - Speech patterns

**Reference Image:**
- Do you have a reference image? If yes, provide path.
- If no, we'll generate one using Leonardo.ai based on description.
```

**Wait for user response.**

### If Character = "existing":

Use provided character name and reference image.

Verify:
- Character name is provided
- Reference image path exists and is accessible
- If reference image missing, prompt user for path

**Output:**
```markdown
## Series Continuity: Using Existing Character ✅

**Character:** {character_name}
**Reference Image:** {reference_image_path}
**Series Context:** This maintains visual consistency with previous episodes
```

---

## Step 4: Generate Scene Structure

Based on format (drama or song), create scene-by-scene breakdown.

### For DRAMA (10-12 scenes):

Create structured story with emotional arc following the proven narrative structure:

**Template Structure:**
```markdown
## {Number}-Scene Drama Structure

**Title:** [Story Title]
**Moral/Theme:** [Core message]
**Characters:** [List with roles]
**Setting:** [Primary location(s)]
**Total Duration:** ~4-5 minutes (240-300 seconds)

**Emotional Arc:** [Start emotion] → [Challenge] → [Low point] → [Resolution] → [End emotion]

**Narrative Structure:**
- Introduction (Scenes 1-2): Setup and establish relationships
- Rising Action (Scenes 3-5): Challenges and failures
- Turning Point (Scenes 6-7): Encouragement and renewed hope
- Climax (Scenes 8-10): Progressive success and victory
- Resolution (Scenes 11-12): Celebration and moral reinforcement

---

### Scene 1: [Scene Name] (25-30 seconds)
**Purpose:** Establish setting and introduce character with strong hook
**Mood:** [Emotion]
**Location:** [Where]
**Character State:** [Emotional/physical state]
**Action:** [What happens in 2-3 sentences]
**Transition:** [Type: dissolve/fade/cut] - [How it leads to next scene]

### Scene 2: [Scene Name] (20-25 seconds)
**Purpose:** Establish relationships or introduce challenge
**Mood:** [Emotion]
**Location:** [Where]
**Character State:** [Emotional/physical state]
**Action:** [What happens in 2-3 sentences]
**Transition:** [Type: dissolve/fade/cut] - [How it leads to next scene]

### Scenes 3-5: [Rising Action] (20-25 seconds each)
**Purpose:** Show attempts, failures, growing frustration
**Mood:** [Progression of emotions]
**Transitions:** [Maintain visual flow between attempts]

### Scenes 6-7: [Turning Point] (20-25 seconds each)
**Purpose:** Encouragement, renewed determination
**Mood:** [Shift from despair to hope]
**Transitions:** [Mark emotional shift]

### Scenes 8-10: [Climax] (20-30 seconds)
**Purpose:** Progressive success, building to victory
**Scene 10 Duration:** 25-30 seconds (key triumphant moment)
**Transitions:** [Build excitement and momentum]

### Scenes 11-12: [Resolution] (20-25 seconds each)
**Purpose:** Celebration and moral reinforcement
**Final Scene:** Clear moral statement and positive ending
**Transition:** [Final fade out]

[Repeat detailed breakdown for all 10-12 scenes]

**Scene Duration Guidelines:**
- Key dramatic moments (Scenes 1, 10, 12): 25-30 seconds
- Standard scenes: 20-25 seconds
- Total: ~4.5 minutes (270 seconds)
```

### For SONG (11 scenes):

Create visual sequences matching song structure with precise timing:

**Template Structure:**
```markdown
## 11-Scene Song Structure

**Title:** [Song Title]
**Theme:** [Core message]
**Characters:** [List]
**Musical Style:** [Genre, tempo, mood]
**Total Duration:** ~3-4 minutes (approximately 210-220 seconds)

**Song Structure:** Intro → Verse 1 → Chorus → Verse 2 → Chorus → Bridge → Final Chorus → Outro

**Scene Arc:** Based on the song duration (~3:30), here's the 11-scene breakdown:

| Scene | Title | Duration | Timing | Song Section | Emotional Beat |
|-------|-------|----------|---------|--------------|----------------|
| 1 | [Opening/Setup] | 16-20s | 0:00-0:18 | Intro | [Emotion] |
| 2 | [Discovery] | 14-18s | 0:18-0:34 | Verse 1 start | [Emotion] |
| 3 | [Adventure Begins] | 18-22s | 0:34-0:54 | Chorus start | [Emotion] |
| 4 | [Key Moment 1] | 20-24s | 0:54-1:16 | Chorus/Verse 2 | [Emotion] |
| 5 | [Turning Point] | 14-18s | 1:16-1:32 | Verse 2 end | [Emotion] |
| 6 | [Escalation] | 20-24s | 1:32-1:54 | Chorus 2 | [Emotion] |
| 7 | [Urgency/Climax Build] | 18-22s | 1:54-2:14 | Bridge start | [Emotion] |
| 8 | [Magic Begins] | 18-22s | 2:14-2:34 | Bridge end | [Emotion] |
| 9 | [Transformation] | 22-26s | 2:34-2:58 | Final Chorus start | [Emotion] |
| 10 | [Peak Moment] | 20-24s | 2:58-3:20 | Final Chorus peak | [Emotion] |
| 11 | [Resolution/Ending] | 18-22s | 3:20-3:40 | Outro | [Emotion] |

---

### Scene 1: [Scene Name] (16-20 seconds)
**Timing:** 0:00-0:18
**Song Section:** Intro
**Visual Purpose:** Establish setting and character
**Mood:** [Emotion]
**Action:** [What happens visually in 2-3 sentences]
**Transition:** [Type: dissolve/fade/cut] - [How it leads to next scene]

### Scene 2: [Scene Name] (14-18 seconds)
**Timing:** 0:18-0:34
**Song Section:** Verse 1 start
**Visual Purpose:** [Purpose]
**Mood:** [Emotion]
**Action:** [What happens]
**Transition:** [Type] - [Connection to next]

[Continue for all 11 scenes with specific timing matched to song sections]
```

**Include:**
- Scene-by-scene breakdown
- Duration for each scene (must total to target video length)
- Emotional progression
- Character arc (how character changes from start to end)
- Visual variety (different locations, lighting, actions)

**Pause for user approval of structure before proceeding.**

---

## Step 4.5: Validate Music-to-Scene Synchronization ✅

**CRITICAL:** Run comprehensive validation BEFORE generating production prompts to catch timing issues early.

### Validation Process

Run through all validation categories from `/home/user/Youtube-Content-Creator/.claude/validation-music-scene-sync.md`:

#### 1. Music Structure Validation

**For SONG format:**
- ✅ Song structure complete with all sections (Intro, Verses, Chorus, Bridge, Outro)
- ✅ Each section has duration specified in seconds
- ✅ Total music duration matches target video length (±5 seconds acceptable)
- ✅ Tempo specified (BPM)
- ✅ Suno prompt includes tempo, energy level, vocal style, instrumentation

**For DRAMA format:**
- ✅ Background music description complete
- ✅ Music duration covers full video length
- ✅ Mood progression specified

**Calculate total music duration:**
```
Total Music Duration = Sum of all section durations
Compare to Target Duration
Delta = |Total - Target|
✅ PASS if Delta <= 5 seconds
❌ FAIL if Delta > 5 seconds (adjust section durations)
```

---

#### 2. Scene Duration Math Validation

**Check timing calculations for ALL scenes:**

```
For each scene:
✅ Has start_time (format: M:SS or MM:SS)
✅ Has end_time (format: M:SS or MM:SS)
✅ Has duration (in seconds)
✅ Math check: (end_time - start_time) == duration

For consecutive scenes:
✅ Scene[n].start_time == Scene[n-1].end_time (no gaps)
✅ Scene[n].start_time >= Scene[n-1].end_time (no overlaps)

For total:
✅ Sum of all scene durations == Target duration (±5 seconds)
✅ Scene count matches format (11 for song, 10-12 for drama)
```

**Generate timing table:**

| Scene | Start | End | Duration | Math Check | Gap/Overlap |
|-------|-------|-----|----------|------------|-------------|
| 1 | 0:00 | 0:XX | XXs | ✅/❌ | N/A |
| 2 | 0:XX | 0:YY | YYs | ✅/❌ | ✅/❌ |
| ... | ... | ... | ... | ... | ... |
| **Total** | | | **XXXs** | **Target: YYYs** | **Delta: Zs** |

**IF any row shows ❌:** Fix timing before proceeding.

---

#### 3. Music-to-Scene Mapping Validation

**For SONG format - REQUIRED:**

Create and verify music mapping table exists:

| Scene # | Duration | Timing | Music Section | Lyrics/Music Content |
|---------|----------|--------|---------------|---------------------|
| 1 | Xs | 0:00-X | Section name | Specific lyrics that play |
| 2 | Ys | X-Y | Section name | Specific lyrics that play |
| ... | ... | ... | ... | ... |

**Validation checks:**
- ✅ Table exists with ALL scenes mapped
- ✅ Each scene has specific music section assigned
- ✅ Each scene has specific lyrics/content specified (not "TBD")
- ✅ Music section durations match scene timing
- ✅ All song sections are covered (no missing sections)

**For DRAMA format:**

For each scene, verify:
- ✅ Background music timing specified (which part plays)
- ✅ Volume changes noted (full volume / ducked for dialogue)
- ✅ Music mood aligns with scene emotional beat

---

#### 4. Animation Timing Validation

**For EACH scene's animation prompt, verify:**

```
✅ Starts with: "MINIMUM [X] seconds duration" where X = scene duration
✅ Includes detailed timing breakdown:
   - 0-[Y]s: [specific action]
   - [Y]-[Z]s: [specific action]
   - [Z]-[duration]s: [specific action]
✅ Pacing matches music tempo:
   - Fast songs (180-200 BPM): "FAST-PACED", "RAPID", "HIGH ENERGY"
   - Medium songs (120-140 BPM): "Medium-paced", "Steady"
   - Slow songs (60-100 BPM): "Gentle", "Slow", "Graceful"
   - Drama: Appropriate to emotional beat
✅ Camera movement timing specified
✅ Character action timing specified
✅ Effects timing specified
```

**Red flags (will cause production to fail):**
- ❌ No duration specified
- ❌ Generic "character does X" without timing
- ❌ Pacing doesn't match tempo (e.g., "gentle" for 180 BPM song)
- ❌ No timing breakdown

---

#### 5. Caption Synchronization Validation

**For SONG format:**

For each caption/lyric:
- ✅ Has start time (seconds or M:SS)
- ✅ Has end time (seconds or M:SS)
- ✅ Duration appropriate for tempo:
  - Fast (180-200 BPM): 2-4 seconds per line
  - Medium (120-140 BPM): 3-6 seconds per line
  - Slow (60-100 BPM): 4-8 seconds per line
- ✅ Caption text matches lyrics in song structure EXACTLY
- ✅ No overlapping captions (Caption[n].start >= Caption[n-1].end)
- ✅ Captions aligned to music sections

**For DRAMA format:**

For each scene with dialogue:
- ✅ Voice start time specified
- ✅ Voice duration specified
- ✅ Background music volume adjustment noted (e.g., "duck to 30%")
- ✅ No voice overlap between scenes
- ✅ SSML tags provided with emotion/pacing

---

#### 6. Tempo-Animation Consistency Validation

**Compare Suno music prompt tempo with ALL animation prompts:**

```
Music Tempo: [X] BPM
Music Style: [fast/medium/slow], [energy level]

Animation Prompt Pacing Check:
Scene 1: [descriptors used] ✅/❌
Scene 2: [descriptors used] ✅/❌
...

PASS Criteria:
- 180-200 BPM music → "FAST", "RAPID", "HIGH ENERGY" in animations
- 120-140 BPM music → "Medium-paced", "Steady" in animations
- 60-100 BPM music → "Gentle", "Slow", "Graceful" in animations

FAIL Examples:
- 180 BPM music + "gentle movements" → ❌ MISMATCH
- 80 BPM music + "rapid action" → ❌ MISMATCH
```

---

#### 7. Transition Timing Validation

**For each scene transition, verify:**

```
✅ Transition type specified (dissolve/cut/fade to black/fade to white/wipe)
✅ Transition duration specified (0.5s / 1s / 2s)
✅ Transition duration matches tempo:
   - Fast songs (180-200 BPM): 0.5s quick dissolves
   - Medium songs (120-140 BPM): 1s standard dissolves
   - Slow songs (60-100 BPM): 2s longer fades
✅ For SONGS: Transition timing synced to music beats
✅ Audio transition specified (crossfade/hard cut)
```

---

#### 8. Production Completeness Validation

**For EACH scene, verify ALL these elements exist:**

```
Scene [N] Completeness:
✅ Visual Description (2-3 sentences)
✅ Setting, Mood, Emotional Beat specified
✅ Camera angle/movement specified
✅ Lighting description

✅ Image Generation Prompt includes:
   - Character description + reference note
   - Background/environment details
   - Lighting specification
   - Composition/framing
   - Style (3D Pixar, etc.)
   - Aspect ratio (9:16)

✅ Animation Prompt includes:
   - MINIMUM duration statement
   - Character actions with timing breakdown
   - Camera movement
   - Environmental motion
   - Detailed sequence (0-Xs, X-Ys, Y-Zs)
   - Mood and pacing matched to tempo

✅ Captions/Dialogue (if applicable):
   - Dual-language text OR voice dialogue
   - Timing specified (start-end)
   - Delivery notes (emotion, tone)

✅ Timing & Duration section:
   - Scene duration
   - Voice/caption start time
   - Background music volume

✅ Transition to Next Scene:
   - Type and duration
   - Audio transition

✅ Audio Sync Notes:
   - Timing breakdown
   - Audio layers
   - Sound effects
```

**Red flag (incomplete scene):**
- ❌ Only has "Visual Description" - missing prompts
- ❌ Generic prompts without details
- ❌ Missing timing information

---

### Generate Validation Report

**Create validation summary:**

```markdown
## 🔍 Music-to-Scene Validation Report

**Video Title:** [Title]
**Format:** [Song/Drama]
**Target Duration:** [X] seconds ([M:SS])
**Scene Count:** [N] scenes
**Music Tempo:** [BPM] ([Fast/Medium/Slow])

---

### ✅ VALIDATION RESULTS

1. **Music Structure:** [✅ PASS / ❌ FAIL]
   - Issues: [list or "None"]

2. **Scene Duration Math:** [✅ PASS / ❌ FAIL]
   - Total duration: [X]s (target: [Y]s, delta: [Z]s)
   - Gaps/overlaps: [None / List issues]
   - Issues: [list or "None"]

3. **Music-to-Scene Mapping:** [✅ PASS / ❌ FAIL]
   - Mapping table: [EXISTS / MISSING]
   - Scenes mapped: [N/Total]
   - Issues: [list or "None"]

4. **Animation Timing:** [✅ PASS / ❌ FAIL]
   - Scenes with duration: [N/Total]
   - Scenes with timing breakdown: [N/Total]
   - Pacing matched to tempo: [N/Total]
   - Issues: [list or "None"]

5. **Caption Synchronization:** [✅ PASS / ❌ FAIL]
   - Captions with timing: [N/Total]
   - Captions match lyrics: [YES/NO]
   - Issues: [list or "None"]

6. **Tempo-Animation Consistency:** [✅ PASS / ❌ FAIL]
   - Music tempo: [BPM]
   - Animation pacing: [Matched / Mismatched]
   - Issues: [list or "None"]

7. **Transitions:** [✅ PASS / ❌ FAIL]
   - All transitions specified: [N/Total]
   - Durations appropriate: [YES/NO]
   - Issues: [list or "None"]

8. **Production Completeness:** [✅ PASS / ❌ FAIL]
   - Scenes with complete prompts: [N/Total]
   - Missing elements: [list or "None"]

---

### 🚨 CRITICAL ISSUES (must fix before Step 5)

[List any critical issues that would cause production to fail]
[Or "None ✅" if all validations passed]

---

### ⚠️ WARNINGS (should fix for quality)

[List any warnings that could affect quality]
[Or "None ✅" if no warnings]

---

### 📊 SUMMARY

**Overall Status:** [✅ READY FOR PRODUCTION / ❌ NEEDS FIXES]

**Scenes Ready:** [N]/[Total]
**Critical Issues:** [N]
**Warnings:** [N]

**Next Steps:**
[If PASS:] ✅ Proceed to Step 5 (Generate Production Prompts)
[If FAIL:] ❌ Fix issues listed above, then re-run validation

---

**Validation Date:** [Date]
```

---

### Decision Point

**IF Validation Report shows "READY FOR PRODUCTION" (all critical checks pass):**
- ✅ **Proceed to Step 5** (Generate Complete Production Prompts)
- Minor warnings can be addressed during prompt generation

**IF Validation Report shows "NEEDS FIXES" (critical issues found):**
- ❌ **STOP - Do not proceed to Step 5**
- Fix all critical issues in scene structure
- Re-run validation
- Only proceed when validation passes

**Present validation report to user and wait for confirmation before continuing.**

---

## Step 5: Generate Complete Production Prompts

**CRITICAL REQUIREMENT:** Generate COMPLETE, production-ready prompts for EVERY SINGLE SCENE. Each scene MUST have:
1. ✅ Detailed Image Generation Prompt (Leonardo.ai)
2. ✅ Detailed Animation Prompt (MiniMax Hailuo)
3. ✅ Dialogue/Captions (if applicable)

**DO NOT** leave any scene with only a "Visual Description" - every scene needs copy-paste ready prompts for the AI tools.

For each scene, generate ALL production elements:

### For Each Scene, Create:

```markdown
## **SCENE {number}: {Scene Name}** ({duration} seconds)
**Timing:** {start_time}-{end_time}

### Visual Description
[2-3 sentences describing the scene composition, lighting, mood, character position, background elements]

**Setting:** {location}
**Mood:** {mood}
**Emotional Beat:** {what this scene contributes to story}
**Camera:** {camera movement/angle}
**Lighting:** {lighting description}
**Song Section:** {if song: which part of song this scene matches}

---

### Image Generation Prompt (Leonardo.ai)

\```
{Character name and description} in {location and setting}. 3D Pixar style.

Foreground: {character position, action, expression}
Background: {environment details, props, atmospheric elements}
Lighting: {lighting type, color temperature, mood}
Composition: {framing, perspective}

Style: 3D Pixar animation quality, vibrant colors, detailed textures
Aspect Ratio: 9:16 vertical
Quality: Ultra detailed, Disney/Pixar quality

{If character reference exists: "USE CHARACTER REFERENCE IMAGE - Set strength to HIGH"}
\```

---

### 2. Animation Prompt (MiniMax Hailuo)

\```
MINIMUM {duration} seconds duration.

Character Action: {what character does - specific movements, gestures, expressions}
Camera Movement: {static/zoom in/zoom out/pan left/pan right/tracking shot}
Environmental Motion: {background elements that move - wind, leaves, water, etc.}
Timing: {pacing - slow/medium/fast, beats where actions happen}

Detailed Sequence:
- 0-{X}s: {action description}
- {X}-{Y}s: {action description}
- {Y}-{duration}s: {action description}

Mood: {emotional tone}
Lighting: {any lighting changes during animation}

IMPORTANT: Set duration to MINIMUM {duration} seconds or longer.
\```

---

### 3. Dialogue ({language})

**{Character Name}:**

{If Tamil:}
**Tamil:** "{dialogue in Tamil}"
**English Translation:** "{English translation}"

{If English:}
**English:** "{dialogue in English}"

{If Both:}
**Tamil:** "{dialogue in Tamil}"
**English:** "{dialogue in English}"

**Delivery:** {emotion, tone, pacing}

---

### 4. Voice Direction (Azure TTS / ElevenLabs)

**Voice Selection:**
- {If Tamil: `te-IN-ShrutiNeural` or `ta-IN-PallaviNeural` or `ta-IN-ValluvarNeural`}
- {If English: `en-US-AnaNeural` or `en-US-JennyNeural` or specify voice}

**SSML Tags:**
\```xml
<speak version="1.0" xmlns="http://www.w3.org/2001/10/synthesis" xml:lang="{lang-code}">
    <voice name="{voice-id}">
        <prosody rate="{speed}" pitch="{pitch}" volume="{volume}">
            <emphasis level="{low/medium/strong}">{dialogue}</emphasis>
        </prosody>
    </voice>
</speak>
\```

**Emotion:** {happy/sad/excited/calm/urgent/gentle}
**Speed:** {x-slow/slow/medium/fast/x-fast or percentage like "110%"}
**Pitch:** {x-low/low/medium/high/x-high or semitones like "+2st"}

---

### 5. Timing & Duration

**Scene Duration:** {duration} seconds
**Voice Start Time:** {when dialogue begins, e.g., "2s after scene start"}
**Voice Duration:** {how long dialogue lasts}
**Background Music:** {continues/fades in/fades out/pauses}

---

### 6. Transition to Next Scene

**Transition Type:** {dissolve/cut/fade to black/fade to white/wipe}
**Duration:** {0.5s/1s/2s}
**Audio Transition:** {crossfade/hard cut/fade out then in}

---

### 7. Audio Sync Notes

**Timing:**
- 0-{X}s: {Background music only}
- {X}-{Y}s: {Dialogue plays, music ducks to 30% volume}
- {Y}-{duration}s: {Music returns to 100%, scene ends}

**Audio Layers:**
1. Background music (continuous)
2. Voice/dialogue (scene-specific)
3. Sound effects (if any): {list SFX}

---
```

### Music Prompt (Suno) - Generate Once for Entire Video:

```markdown
## MUSIC GENERATION (Suno.ai)

### {If Drama: "Background Music"}

**Prompt:**
\```
{Genre} instrumental background music for {theme} children's story.
{Mood adjectives: uplifting, gentle, adventurous, magical, etc.}
{Tempo: slow/medium/fast} tempo around {BPM} BPM.
{Instruments: piano, strings, bells, flute, etc.}
{Duration: 4-5 minutes}

Style: Cinematic, orchestral, suitable for animated story
No lyrics, instrumental only
Seamless loop-able for video editing
\```

**Duration:** {240-300 seconds (4-5 minutes)}
**Mood:** {emotional progression - starts {mood}, builds to {mood}, ends {mood}}
**Style Tags:** `instrumental`, `cinematic`, `orchestral`, `kids`, `{genre}`

---

### {If Song: "Full Song with Lyrics"}

**Song Structure:** Intro → Verse 1 → Chorus → Verse 2 → Chorus → Bridge → Final Chorus → Outro

**Lyrics:**

\```
[Intro - Instrumental]

[Verse 1]
{Tamil lyrics line 1}
{Tamil lyrics line 2}
{English translation}

[Chorus]
{Catchy repeated lyrics in Tamil}
{English translation}

[Verse 2]
{Tamil lyrics}
{English translation}

[Chorus - Repeat]

[Bridge]
{Tamil lyrics - different melody/mood}
{English translation}

[Final Chorus - Energetic]
{Lyrics with variations/ad-libs}

[Outro - Instrumental fade]
\```

**Suno Prompt:**
\```
{Genre} {tempo description} children's song about {theme}.
High-energy, bright children's choir vocals.
{Specific musical style reference if any}
{Tempo: 120-180 BPM}
{Language: Tamil and English bilingual or specify}

Style: {Disney/Pixar style, upbeat, catchy, family-friendly}
Vocals: Children's choir, clear pronunciation
Instruments: {list instruments}
\```

**Duration:** {180-240 seconds (3-4 minutes)}
**Vocal Style:** {High-pitched children's choir / Solo child voice / etc.}
**Style Tags:** `{genre}`, `kids`, `upbeat`, `children's choir`, `{language}`
```

---

**Output for user:**
- All scene packages with COMPLETE prompts (10-12 for drama, 11 for song)
- Single music prompt
- Well-formatted, copy-paste ready
- Organized by scene number

**VERIFICATION CHECKLIST before presenting to user:**
```markdown
## 🔍 Pre-Delivery Verification

Verify EVERY scene has ALL of these:
- ✅ Visual Description
- ✅ Image Generation Prompt (Leonardo.ai) - detailed, copy-paste ready
- ✅ Animation Prompt (MiniMax Hailuo) - detailed with timing, copy-paste ready
- ✅ Dialogue/Captions (if drama) OR Caption timing (if song)
- ✅ Duration specified clearly

Total Scenes: {number}
✅ All scenes complete: {yes/no}

If ANY scene is missing prompts, DO NOT present to user. Complete all scenes first.
```

**After generation and verification, inform user:**
```markdown
## ✅ Production Prompts Generated - ALL SCENES COMPLETE

**Scenes Created:** {number} scenes (ALL with complete image + animation prompts)
**Total Estimated Duration:** {duration} minutes

**What You Received:**
- ✅ {number} complete scene prompts (image + animation for each)
- ✅ 1 music generation prompt (Suno)
- ✅ {number} caption sets (timing + text)
- ✅ All prompts are copy-paste ready

**Next Steps:**
1. **Generate music on Suno.ai** (do this FIRST - you need the timing!)
2. **Generate character reference images** (if new character - do this before scenes)
3. **Generate all {number} scene images on Leonardo.ai** (use reference images)
4. **Generate all {number} scene animations on MiniMax Hailuo** (set minimum duration for each)
5. **{If drama: Generate all voice audio on Azure TTS or ElevenLabs}**
6. **Report back which scenes succeeded/failed**

**Production Estimate:**
- Music: ~5-15 minutes
- Character references (if new): ~15-30 minutes
- Scene images: ~{number * 3-5} minutes
- Scene animations: ~{number * 30-60} minutes (queue time)
- {If drama: Voice generation: ~{number * 2-3} minutes}
- Total: ~{estimate} hours

**Ready to proceed with manual production?**
```

**Pause and wait for user to complete manual production.**

---

## Step 6: Collect Production Results

After user has generated assets manually, collect feedback.

**Prompt user:**
```markdown
## Production Results Check

Please report the status of each scene:

**Format:** "Scenes X-Y ✅, Scenes A-B ❌ (reason)"

**Example:**
- "All scenes successful ✅"
- "Scenes 1-6 ✅, Scenes 7-8 ❌ (character face inconsistent)"
- "Scenes 1-4 ✅, Scene 5 ❌ (animation too short), Scenes 6-8 ✅"

**Common Issues:**
- Character inconsistency (face, colors, proportions)
- Animation too short (< minimum duration)
- Lighting mismatch
- Wrong camera angle
- Props missing or incorrect
- Background doesn't match description

**Your Status:**
```

**Wait for user response.**

---

## Step 7: Process Feedback and Refine (If Needed)

Based on user feedback, identify what needs refinement.

### If All Scenes Successful ✅:

```markdown
## ✅ All Scenes Successful - Proceeding to Assembly

Great! All {number} scenes generated successfully.

**Asset Inventory:**
- ✅ Background music: 1 file
- ✅ Scene images: {number} files
- ✅ Scene animations: {number} files
- ✅ Voice audio: {number} files

**Proceeding to video assembly...**
```

**Skip to Step 8.**

---

### If Some Scenes Failed ❌:

Analyze the failures and regenerate prompts.

**For each failed scene:**

1. **Identify the issue:**
   - Character inconsistency → Strengthen reference image usage
   - Animation too short → Emphasize MINIMUM duration
   - Lighting mismatch → Adjust lighting description
   - Wrong composition → Clarify camera angle and framing

2. **Generate refined prompts:**

```markdown
## 🔄 Refined Prompts for Failed Scenes

### Scene {number}: {Scene Name} - REFINEMENT

**Issue Identified:** {what went wrong}
**Fix Applied:** {what changed in prompt}

---

### REFINED Image Prompt (Leonardo.ai):

\```
{Enhanced prompt with fixes}

**CRITICAL:**
- Upload character reference image BEFORE generating
- Set Character Reference Strength to HIGH
- {Any other specific fixes}
\```

---

### REFINED Animation Prompt (MiniMax Hailuo):

\```
**CRITICAL - MINIMUM {duration} SECONDS DURATION**

{Enhanced animation prompt with fixes}

**Before generating:**
- Upload the CORRECT image from refined generation above
- Set duration slider to MINIMUM {duration} seconds
- {Any other specific fixes}
\```

---

{Include voice/timing refinements if needed}
```

**After providing refined prompts:**

```markdown
## Next Steps for Refinement:

1. Regenerate images for failed scenes: {list scene numbers}
2. Regenerate animations using NEW images
3. Regenerate voice if dialogue changed
4. Report back when complete

**Which scenes are you regenerating?** {scene numbers}
```

**Wait for user to regenerate and report back.**

**Repeat Step 7 until all scenes successful.**

---

## Step 8: Generate Timeline Assembly Instructions

Once all scenes successful, generate video assembly instructions.

### Calculate Timing:

**Build timeline:**
- Scene 1: 0:00 - 0:{scene1_duration}
- Scene 2: 0:{scene1_duration} - 0:{scene1_duration + scene2_duration}
- Continue for all scenes
- Total: {total_duration}

### Generate FFmpeg Commands:

```markdown
## 🎬 Video Assembly Instructions

**Total Duration:** {total_duration} seconds ({minutes}:{seconds})

---

### Prerequisites:

**Required Files:**
- `background_music.mp3` - Background music from Suno
- `scene_01_video.mp4` through `scene_{N}_video.mp4` - Animations from MiniMax
- `scene_01_voice.mp3` through `scene_{N}_voice.mp3` - Voice from Azure TTS

**Software Needed:**
- FFmpeg (install: `brew install ffmpeg` or `sudo apt install ffmpeg`)

---

### Step 1: Combine Each Scene with Voice

For each scene, overlay voice audio on video:

\```bash
# Scene 1
ffmpeg -i scene_01_video.mp4 -i scene_01_voice.mp3 \
  -filter_complex "[0:a]volume=0.3[bg];[1:a]volume=1.0[voice];[bg][voice]amix=inputs=2[aout]" \
  -map 0:v -map "[aout]" -c:v copy -c:a aac -shortest scene_01_final.mp4

# Scene 2
ffmpeg -i scene_02_video.mp4 -i scene_02_voice.mp3 \
  -filter_complex "[0:a]volume=0.3[bg];[1:a]volume=1.0[voice];[bg][voice]amix=inputs=2[aout]" \
  -map 0:v -map "[aout]" -c:v copy -c:a aac -shortest scene_02_final.mp4

{Repeat for all scenes}
\```

**Explanation:**
- `volume=0.3` - Original video audio at 30% (if any)
- `volume=1.0` - Voice audio at 100%
- `amix=inputs=2` - Mix both audio streams
- `-shortest` - End when shortest input ends

---

### Step 2: Create Scene List File

Create a file named `scene_list.txt`:

\```
file 'scene_01_final.mp4'
file 'scene_02_final.mp4'
file 'scene_03_final.mp4'
{Continue for all scenes}
\```

---

### Step 3: Concatenate All Scenes

Combine all scenes into one video:

\```bash
ffmpeg -f concat -safe 0 -i scene_list.txt -c copy video_without_music.mp4
\```

---

### Step 4: Add Background Music

Overlay background music on the complete video:

\```bash
ffmpeg -i video_without_music.mp4 -i background_music.mp3 \
  -filter_complex "[1:a]volume=0.4[music];[0:a]volume=1.0[voice];[voice][music]amix=inputs=2[aout]" \
  -map 0:v -map "[aout]" -c:v copy -c:a aac -shortest final_video.mp4
\```

**Explanation:**
- Background music at 40% volume (so voice is clear)
- Voice from video at 100% volume
- Mix both audio layers

---

### Step 5: Verify Output

Check final video:

\```bash
# Check duration
ffmpeg -i final_video.mp4 2>&1 | grep Duration

# Play video
ffplay final_video.mp4

# Or use VLC, QuickTime, etc.
\```

**Expected:**
- Duration: ~{total_duration} seconds
- Resolution: 1080x1920 (9:16 vertical)
- Audio: Clear voice with background music
- All scenes flow smoothly with transitions

---

### Alternative: Shotstack API

If you prefer API-based assembly:

{Generate Shotstack JSON timeline}

\```json
{
  "timeline": {
    "background": "#000000",
    "tracks": [
      {
        "clips": [
          {
            "asset": {
              "type": "video",
              "src": "scene_01_final.mp4"
            },
            "start": 0,
            "length": {scene1_duration}
          },
          {
            "asset": {
              "type": "video",
              "src": "scene_02_final.mp4"
            },
            "start": {scene1_duration},
            "length": {scene2_duration}
          }
          {Continue for all scenes}
        ]
      },
      {
        "clips": [
          {
            "asset": {
              "type": "audio",
              "src": "background_music.mp3",
              "volume": 0.4
            },
            "start": 0,
            "length": {total_duration}
          }
        ]
      }
    ]
  },
  "output": {
    "format": "mp4",
    "resolution": "hd",
    "aspectRatio": "9:16"
  }
}
\```

Use Shotstack dashboard or API to render.

---

### ✅ Assembly Complete

Your final video: `final_video.mp4`

**Next:** Generate YouTube metadata
```

**Wait for user to complete assembly.**

---

## Step 9: Generate YouTube Metadata

Create SEO-optimized YouTube metadata for upload.

```markdown
## 📺 YouTube Metadata

---

### Title (SEO Optimized)

**Tamil + English:**
{Catchy title in Tamil} | {English translation} | {Character Name} {Series if applicable}

**Examples:**
- ஊக்கமது கைவிடேல் | Never Give Up | Kavi's Aathichudi Lessons Ep. 5
- Max & Momo's Magic Christmas Bells 🎄✨ | Holiday Song for Kids

**Character Limit:** {X}/100 characters

---

### Description

\```
{2-3 sentence summary in Tamil}

{2-3 sentence summary in English}

✨ About This Video:
{Detailed description of story/song, moral/theme, what viewers will learn}

👥 Characters:
- {Character 1}: {Description}
- {Character 2}: {Description}

🎵 Music: {Original composition by {creator} OR Music from Suno.ai}
🎨 Animation: 3D Pixar-style animation
🗣️ Languages: {Tamil / English / Both}

⏱️ Timestamps:
0:00 - {Scene 1 name}
{scene1_duration} - {Scene 2 name}
{scene1+2_duration} - {Scene 3 name}
{Continue for all scenes}

📚 {If series:}
Watch all episodes in the {Series Name}:
{Links to previous episodes if available}

👨‍👩‍👧‍👦 Perfect For:
- Kids ages {age range}
- Families
- {Language} learners
- Anyone who loves {theme/genre}

🔔 Subscribe for more {type of content}!
📧 Contact: {email if applicable}

#️⃣ Tags: {list first 5-7 tags}
\```

---

### Tags (15-20 tags)

\```
{Character name}, {theme}, {language} kids videos, {language} stories, moral stories, animated stories, kids education, family friendly, {series name if applicable}, {specific themes}, kids songs, children's entertainment, {cultural elements}, learn {language}, {genre}
\```

**Examples:**
- Drama: `Kavi the Peacock, Aathichudi, Tamil kids videos, moral stories, never give up, perseverance, animated stories`
- Song: `Max and Momo, Christmas song, kids music, holiday songs, Carol of the Bells, family friendly, children's choir`

---

### Thumbnail Suggestions

**Option 1: Character Close-up**
- Use Scene {X} image (character with expressive emotion)
- Add text overlay: "{Catchy phrase in Tamil/English}"
- Bright, vibrant colors
- Character face fills 60-70% of frame

**Option 2: Key Moment**
- Use Scene {Y} (most exciting/emotional moment)
- Add text: "{Title}" in large, readable font
- High contrast for mobile visibility

**Option 3: Custom Design**
- Character + background from key scene
- Large text: "{Main character name} | {Theme}"
- Emoji/icons related to theme
- Consistent branding if series

**Best Practices:**
- Resolution: 1280x720 (16:9)
- File size: < 2MB
- Format: JPG or PNG
- Text: Large, readable on mobile
- Faces: Show emotion clearly
- Colors: High contrast, vibrant

---

### Video Settings

**Category:** {Film & Animation / Education / Music / Entertainment}

**Playlist:**
- {If series: Add to "{Series Name}" playlist}
- {Themed playlists: "Moral Stories", "Kids Songs", "Tamil Content"}

**Audience:**
- **Made for Kids:** {Yes / No - specify based on content}
  - Yes: If exclusively for children under 13
  - No: If universal audience (general audience, all ages)

**Language:** {Tamil / English / Tamil (with English subtitles)}

**License:** Standard YouTube License

**Allow Embedding:** Yes

**Publish Category:** {Public / Unlisted / Scheduled}

{If Scheduled:}
**Best Upload Times:**
- Weekend mornings: 8-10 AM local time
- Weekday evenings: 5-7 PM local time
- Holiday-related content: 1-2 weeks before holiday

---

### End Screen & Cards

**End Screen (last 10-15 seconds):**
- Subscribe button: Bottom center
- Next video: {If series: next episode or most popular video}
- Playlist: {Series playlist or themed playlist}

**Cards (throughout video):**
- Add card at 25%, 50%, 75% marks
- Link to related videos
- Poll card: "What should {character} learn next?"

---

### Community Post (Optional)

After upload, create community post:

\```
🎉 NEW VIDEO: {Title}

{Thumbnail image}

{1-2 sentence description}

Watch now: {YouTube link}

What did you think? Comment below! 💬
\```

---

## ✅ YouTube Metadata Ready

**Files to upload:**
1. `final_video.mp4` - Main video
2. {Thumbnail file name} - Custom thumbnail
3. {Subtitle file if created} - .srt file

**Copy metadata above and paste into YouTube Studio.**
```

---

## Step 10: Quality Check

Provide comprehensive QA checklist before upload.

```markdown
## ✅ Final Quality Check

Review before publishing:

---

### 📽️ Visual Quality

- ✅ Character consistency across all scenes
  - Same colors, features, proportions
  - Character reference applied correctly
- ✅ Lighting consistency
  - No jarring changes between scenes
  - Mood lighting matches story arc
- ✅ Resolution and aspect ratio
  - 1080p or higher
  - 9:16 vertical (or intended ratio)
- ✅ No visual glitches
  - No flickering, artifacts, corrupted frames
- ✅ Transitions smooth
  - Dissolves/fades render correctly
  - No abrupt cuts unless intended
- ✅ Text overlays (if any)
  - Readable on mobile devices
  - Correct spelling and grammar
  - Appropriate duration

---

### 🔊 Audio Quality

- ✅ Voice audio clear and understandable
  - No distortion, clipping, or noise
  - Volume balanced across scenes
  - Pronunciation correct
- ✅ Background music balanced
  - Music doesn't overpower dialogue
  - Consistent volume throughout
  - Fades in/out smoothly
- ✅ Audio sync
  - Dialogue matches character mouth/actions
  - Music cues match visual beats
  - No delay or echo
- ✅ No audio gaps or pops
  - Smooth transitions between scenes
  - No silence where there shouldn't be

---

### 📖 Content Quality

- ✅ Story coherent and complete
  - Clear beginning, middle, end
  - Moral/theme clearly communicated
  - Character arc resolved
- ✅ Pacing appropriate
  - Not too fast or too slow
  - Scenes have proper duration
  - Holds attention throughout
- ✅ Language accuracy
  - {Tamil} spelling and grammar correct
  - {English} translation accurate
  - Culturally appropriate
- ✅ Educational value (if applicable)
  - Moral clearly demonstrated
  - Positive message reinforced
  - Age-appropriate lessons
- ✅ Cultural sensitivity
  - Respectful representation
  - No stereotypes or offensive content
  - Authentic to source material (if based on tradition)

---

### ⚙️ Technical Specifications

- ✅ Duration: {total_duration} seconds (~{minutes}:{seconds})
- ✅ Format: MP4 (H.264 video, AAC audio)
- ✅ Resolution: 1080x1920 (9:16) or 1920x1080 (16:9)
- ✅ Frame rate: 24fps or 30fps (consistent)
- ✅ Bitrate: Minimum 8 Mbps for 1080p
- ✅ File size: Appropriate for upload (< 128 GB)
- ✅ Closed captions/subtitles ready (if applicable)

---

### 📱 Mobile Preview

- ✅ Watch video on mobile device before upload
- ✅ Check text readability
- ✅ Verify audio levels with phone speakers
- ✅ Test portrait orientation (for 9:16)

---

### 🎯 YouTube Optimization

- ✅ Title under 100 characters
- ✅ Description comprehensive (include timestamps)
- ✅ 15-20 relevant tags
- ✅ Custom thumbnail (1280x720, <2MB)
- ✅ Proper categorization
- ✅ "Made for Kids" setting correct
- ✅ End screens and cards configured
- ✅ Playlist assignment

---

## Issues Found?

If any checklist item fails:

**Visual Issues:**
- Regenerate specific scenes with refined prompts
- Adjust color correction in video editor
- Re-render with correct settings

**Audio Issues:**
- Remix audio levels with FFmpeg
- Regenerate voice with adjusted settings
- Re-balance music volume

**Content Issues:**
- Review script and moral clarity
- Consider adding text overlays for emphasis
- Adjust pacing by trimming/extending scenes

**Technical Issues:**
- Re-export with correct settings
- Compress if file too large
- Convert format if needed

---

## ✅ Quality Check Complete

{If all items checked:}
**Status: READY FOR UPLOAD** 🎉

{If issues found:}
**Status: NEEDS REVISION** ⚠️
**Issues:** {list issues to fix}

**Proceed with YouTube upload?**
```

---

## Step 11: Report Final Summary

Provide complete summary of the video creation process.

```markdown
## 🎉 Video Creation Complete!

---

### 📊 Project Summary

**Title:** {Video title}
**Format:** {Drama/Song}
**Language:** {Tamil/English/Both}
**Character(s):** {Character names}
**Duration:** {total_duration} seconds (~{minutes}:{seconds})
**Scenes:** {number} scenes
**Theme:** {moral/theme}

---

### 📁 Files Created

**Video Assets:**
- ✅ `final_video.mp4` - Final assembled video ({file_size} MB)
- ✅ `background_music.mp3` - Suno music
- ✅ Scene images: `scene_01_image.jpg` through `scene_{N}_image.jpg` ({N} files)
- ✅ Scene animations: `scene_01_video.mp4` through `scene_{N}_video.mp4` ({N} files)
- ✅ Voice audio: `scene_01_voice.mp3` through `scene_{N}_voice.mp3` ({N} files)
- ✅ {Thumbnail file if created}

**Documentation:**
- Scene prompts and structure
- Timeline assembly instructions
- YouTube metadata (title, description, tags)
- Quality checklist

---

### 📈 Production Statistics

**Time Invested:**
- Idea to prompts: ~{X} minutes
- Manual production: ~{Y} minutes (estimated)
- Video assembly: ~{Z} minutes
- Total: ~{Total} minutes

**Assets Generated:**
- Images: {N}
- Animations: {N}
- Voice clips: {N}
- Music tracks: 1
- Total files: {N + N + N + 1}

**Refinement Rounds:** {0 if none, or number of refinement iterations}

---

### 🎬 Next Steps

1. **Upload to YouTube:**
   - Go to YouTube Studio: https://studio.youtube.com
   - Click "Create" → "Upload Video"
   - Upload `final_video.mp4`
   - Paste metadata from Step 9
   - Upload custom thumbnail
   - Configure end screens and cards
   - Publish or schedule

2. **Promote Your Video:**
   - Share on social media
   - Create community post
   - Add to relevant playlists
   - Engage with comments

3. **Track Performance:**
   - Monitor views, watch time, engagement
   - Read comments for feedback
   - Identify what works for future videos

4. **Plan Next Video:**
   - {If series: Next episode in {series name}}
   - Reuse character reference for consistency
   - Build on successful elements

---

### 💡 Tips for Next Time

**What Worked Well:**
- {Identify successful elements}
- {Note efficient workflow steps}

**Improvements for Next Video:**
- {Suggestions based on this experience}
- {Workflow optimizations}

**Character Library:**
{If new character created:}
- ✅ Save character reference: `{reference_image_path}`
- ✅ Document character details for future use
- ✅ Consider creating series with this character

---

### 🔗 Resources Used

- **Suno.ai:** Music generation - https://suno.ai
- **Leonardo.ai:** Image generation - https://leonardo.ai
- **MiniMax Hailuo:** Animation - https://hailuoai.video
- **Azure TTS:** Voice generation - https://azure.microsoft.com/en-us/services/cognitive-services/text-to-speech/
- **FFmpeg:** Video assembly - https://ffmpeg.org
- **YouTube Studio:** Upload and publish - https://studio.youtube.com

---

## 🎊 Congratulations!

You've successfully created a complete YouTube video from idea to production!

**Total Scenes:** {N}
**Production Quality:** ✅ Professional
**Ready for Upload:** ✅ Yes

**Your video is ready to inspire and entertain viewers!** 🌟

---

### Questions or Need Help?

If you need to:
- Create another video: Run this command again with new idea
- Refine specific scenes: Provide scene numbers and issues
- Create series continuation: Use `--character existing` with same character
- Adjust metadata: Regenerate Step 9 with different parameters

**Command to create next video:**
\```
/create-video "your new idea" --character {new/existing} --language {tamil/english/both}
\```
```

---

## Validation

Before marking as complete, verify:

- ✅ All arguments parsed correctly
- ✅ Format recommendation provided (drama or song)
- ✅ Copyright clearance completed
- ✅ Character defined (new or existing)
- ✅ Scene structure created (10-12 for drama, 11 for song)
- ✅ **Music-to-Scene Validation completed (Step 4.5) with PASS status**
  - ✅ Music structure validated
  - ✅ Scene duration math validated (no gaps/overlaps)
  - ✅ Music-to-scene mapping table created (for songs)
  - ✅ Animation timing validated (all prompts have MINIMUM duration)
  - ✅ Caption synchronization validated
  - ✅ Tempo-animation consistency validated
  - ✅ Transitions validated
  - ✅ Production completeness validated (all scenes have complete prompts)
- ✅ All production prompts generated (image, animation, dialogue, voice, music)
- ✅ User completed manual production
- ✅ Feedback collected and refinements made (if needed)
- ✅ Timeline assembly instructions provided
- ✅ YouTube metadata generated
- ✅ Quality checklist completed
- ✅ Final summary delivered

---

## Common Issues and Troubleshooting

### Issue: Character inconsistency across scenes

**Solution:**
- Ensure character reference image uploaded BEFORE each generation
- Set Character Reference strength to HIGH in Leonardo.ai
- Use same reference image for all scenes
- Regenerate inconsistent scenes with refined prompts

### Issue: Animations too short (< minimum duration)

**Solution:**
- Emphasize "MINIMUM {duration} seconds" in prompt
- Set duration slider in MiniMax to minimum before generating
- Add more detailed action descriptions to fill time
- Break complex scenes into longer sequences

### Issue: Voice audio quality poor

**Solution:**
- Use proper SSML tags for emotion and pacing
- Select appropriate voice ID for language/character
- Adjust prosody settings (rate, pitch, volume)
- Consider ElevenLabs for higher quality (paid)

### Issue: FFmpeg errors during assembly

**Solution:**
- Verify all input files exist and paths are correct
- Check file formats (should be MP4 for video, MP3 for audio)
- Ensure FFmpeg installed correctly: `ffmpeg -version`
- Try re-exporting assets with compatible formats

### Issue: YouTube upload fails

**Solution:**
- Check file size (< 128 GB, < 256 GB for verified accounts)
- Verify format: MP4 (H.264 + AAC)
- Ensure video duration under 12 hours
- Check internet connection stability
- Try uploading from different browser

---

**END OF WORKFLOW**
