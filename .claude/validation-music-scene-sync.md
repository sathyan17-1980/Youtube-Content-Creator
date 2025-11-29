# Music-to-Scene Validation Framework

## Purpose
Validate that music timing, scene durations, animations, and captions are perfectly synchronized before production begins. Catch timing issues early to avoid expensive re-generation.

---

## Validation Categories

### 1. Music Structure Validation

**Check that music structure matches format type:**

**For SONG format (11 scenes):**
- ✅ Song has clear structure: Intro → Verse 1 → Chorus → Verse 2 → Chorus → Bridge → Final Chorus → Outro
- ✅ Each music section has defined duration (in seconds)
- ✅ Music sections total to target video length (±5 seconds acceptable)
- ✅ Tempo specified (BPM) for songs
- ✅ Suno prompt includes tempo, energy level, and style requirements

**For DRAMA format (10-12 scenes):**
- ✅ Background music is continuous, not sectioned
- ✅ Music duration covers full video length
- ✅ Mood progression specified (starts X, builds to Y, ends Z)

---

### 2. Scene Duration Validation

**Check that scene timings are mathematically correct:**

```
VALIDATION FORMULA:

Total Scene Duration = Sum of all individual scene durations
Gap Check = Scene[n].start_time == Scene[n-1].end_time (no gaps)
Overlap Check = Scene[n].start_time >= Scene[n-1].end_time (no overlaps)
Target Match = |Total Scene Duration - Target Duration| <= 5 seconds

Example:
Scene 1: 0:00-0:18 (18s) ✅
Scene 2: 0:18-0:34 (16s) ✅ (starts exactly when Scene 1 ends)
Scene 3: 0:34-0:54 (20s) ✅ (starts exactly when Scene 2 ends)
...
Total: 220 seconds, Target: 220 seconds ✅
```

**Validation Steps:**
1. ✅ Each scene has explicit start time, end time, and duration
2. ✅ Scene durations add up correctly (end_time - start_time = duration)
3. ✅ No timing gaps between scenes (Scene[n].start == Scene[n-1].end)
4. ✅ No timing overlaps (Scene[n].start >= Scene[n-1].end)
5. ✅ Total duration matches target video length (±5 seconds)
6. ✅ Scene count matches format (11 for song, 10-12 for drama)

---

### 3. Music-to-Scene Mapping Validation

**Check that each scene is mapped to specific music section:**

**For SONG format:**
```
REQUIRED MAPPING TABLE:

| Scene # | Duration | Timing | Music Section | Lyrics/Music Content |
|---------|----------|--------|---------------|---------------------|
| 1       | Xs       | 0:00-X | Section Name  | Specific lyrics     |
| 2       | Ys       | X-Y    | Section Name  | Specific lyrics     |
...

VALIDATION:
✅ Table exists with all 11 scenes
✅ Each scene row has: Scene #, Duration, Timing, Music Section, Lyrics
✅ Music sections align with song structure
✅ Lyrics are specific (not "TBD" or generic)
✅ Timing column matches scene timing exactly
```

**For DRAMA format:**
```
REQUIRED MAPPING:

Each scene should specify:
✅ Which part of background music plays (time range)
✅ Whether music is at full volume or ducked for dialogue
✅ Any music mood shifts that align with scene emotion
```

---

### 4. Animation Timing Validation

**Check that animation prompts specify correct durations:**

**Animation Prompt Requirements:**
```
Each scene's animation prompt MUST include:

✅ "MINIMUM [X] seconds duration" (where X = scene duration)
✅ Detailed timing breakdown within animation:
   - 0-[Y]s: [action]
   - [Y]-[Z]s: [action]
   - [Z]-[duration]s: [action]

✅ Pacing specification matching music tempo:
   - For fast songs (180-200 BPM): "FAST", "RAPID", "HIGH ENERGY"
   - For medium songs (120-140 BPM): "Medium paced", "Steady"
   - For drama: "Appropriate to emotional beat"

✅ Camera movement timing specified
✅ Character action timing specified

EXAMPLE (CORRECT):
"MINIMUM 27 seconds duration. FAST-PACED animation matching 180-200 BPM.
- 0-6s: Max enters clearing
- 6-14s: Bells transform to gold
- 14-22s: Massive sparkle explosion
- 22-27s: Max and Momo awed faces"

EXAMPLE (INCORRECT - will fail):
"Max enters and rings bells. Magic happens."
❌ No duration specified
❌ No timing breakdown
❌ No pacing specified
```

---

### 5. Caption Synchronization Validation

**Check that captions are timed to music/dialogue:**

**For SONG format:**
```
Caption Requirements:

✅ Each lyric line has specific timing (start-end)
✅ Caption timing matches music section timing
✅ Caption duration is appropriate for reading at tempo:
   - Fast songs (180-200 BPM): 2-4 seconds per line
   - Medium songs (120-140 BPM): 3-6 seconds per line
✅ Dual-language captions don't overlap (Tamil above, English below)
✅ Caption text matches lyrics in song prompt exactly

Example Caption Timing:
Music Section: Intro (0:00-0:18)
Caption 1 (0:02-0:06): "டிங் டாங், டிங் டாங், டிங் டாங் டிங்!"
Caption 2 (0:08-0:16): "மேக்ஸ் மற்றும் மோமோ மணிகள் கண்டார்!"

✅ Captions start 2s after scene (give viewer time to see visual)
✅ Captions end before next caption starts (no overlap)
✅ Caption text matches lyrics from song structure
```

**For DRAMA format:**
```
Voice/Dialogue Requirements:

✅ Voice start time specified for each scene
✅ Voice duration specified
✅ Background music volume adjustment specified (duck to 30%)
✅ Timing ensures voice doesn't overlap between scenes
✅ SSML tags provided for emotion/pacing
```

---

### 6. Tempo-to-Animation Consistency Validation

**Check that animation speed matches music tempo:**

```
TEMPO MATCHING RULES:

Music Tempo: 180-200 BPM (FAST - like Carol of the Bells)
Required Animation Descriptors:
✅ "FAST-PACED", "RAPID", "HIGH ENERGY", "QUICK"
✅ "Rapid movements", "Quick cuts", "Energetic"
✅ "No slow moments", "Continuous action"
✅ Character movements: "runs quickly", "swings rapidly", "bounces energetically"
❌ AVOID: "gentle", "slow", "gradual", "peaceful" (except final scene)

Music Tempo: 120-140 BPM (MEDIUM)
Required Animation Descriptors:
✅ "Medium-paced", "Steady", "Flowing"
✅ "Smooth movements", "Natural pace"

Music Tempo: 60-100 BPM (SLOW - ballads)
Required Animation Descriptors:
✅ "Gentle", "Slow", "Peaceful", "Graceful"
✅ "Smooth camera movements", "Lingering shots"

VALIDATION CHECK:
Compare Suno prompt tempo specification with animation prompt pacing descriptors.
If mismatch found, flag for correction.
```

---

### 7. Transition Timing Validation

**Check that transitions are synced to music beats:**

```
Transition Requirements:

✅ Each scene specifies transition type (dissolve/cut/fade)
✅ Transition duration specified (0.5s / 1s / 2s)
✅ For SONG format: Transitions sync to music beats
   - Fast songs: Quick dissolves (0.5s) on strong beats
   - Medium songs: Standard dissolves (1s)
   - Slow songs: Longer fades (2s)

✅ For DRAMA format: Transitions match emotional flow
   - Intense moments: Cuts or quick dissolves
   - Emotional shifts: Longer fades (1-2s)

EXAMPLE (SONG at 180 BPM):
Scene 3 → Scene 4 transition:
✅ Type: Dissolve
✅ Duration: 0.5s (fast to match tempo)
✅ Timing: Synced to beat at 0:54 mark
✅ Note: "Quick dissolve on strong beat"
```

---

### 8. Production Completeness Validation

**Check that ALL production elements are specified:**

```
SCENE COMPLETENESS CHECKLIST:

For EACH scene, verify:

✅ Visual Description (2-3 sentences)
✅ Setting, Mood, Emotional Beat specified
✅ Camera movement/angle specified
✅ Lighting description provided

✅ Image Generation Prompt:
   - Character description with reference
   - Background/environment details
   - Lighting specification
   - Composition/framing
   - Style requirements (3D Pixar, etc.)
   - Aspect ratio (9:16)
   - Quality notes

✅ Animation Prompt:
   - MINIMUM duration specified (= scene duration)
   - Character actions with timing
   - Camera movement
   - Environmental motion
   - Detailed sequence breakdown
   - Mood and lighting
   - Pacing matched to music tempo

✅ Dialogue/Captions (if applicable):
   - Dual-language text (Tamil + English for bilingual)
   - Delivery notes (emotion, tone, pacing)
   - Timing specified (when captions appear)

✅ Voice Direction (if drama):
   - Voice selection (Azure TTS voice ID)
   - SSML tags with prosody
   - Emotion, speed, pitch specified

✅ Timing & Duration:
   - Scene duration
   - Voice/caption start time
   - Background music volume
   - Audio transition notes

✅ Transition to Next Scene:
   - Transition type
   - Duration
   - Audio transition

✅ Audio Sync Notes:
   - Timing breakdown
   - Audio layers specified
   - Sound effects listed

RED FLAGS (incomplete scene):
❌ "Visual Description" only - missing prompts
❌ Generic image prompt without details
❌ Animation prompt without duration or timing
❌ Missing caption timing
❌ No transition specified
```

---

## Validation Workflow

### When to Validate

**Step 1-3 (Planning Phase):**
- ✅ Run validation AFTER scene structure is created
- ✅ Run validation BEFORE generating production prompts
- ✅ Fix timing issues at planning stage (cheap to fix)

**Step 5 (Production Prompts Generated):**
- ✅ Run validation on ALL prompts before user starts generation
- ✅ Ensure completeness before manual production begins
- ✅ Catch missing elements before expensive AI generation

---

### How to Validate

**Automated Validation Script** (conceptual - manual checklist in practice):

```python
def validate_music_scene_sync(scenes, music_structure, format_type):
    """
    Validate music-to-scene synchronization

    Args:
        scenes: List of scene objects with timing, prompts, etc.
        music_structure: Song structure or drama music info
        format_type: "song" or "drama"

    Returns:
        validation_report: Dict with pass/fail for each category
    """

    report = {
        "music_structure": validate_music_structure(music_structure, format_type),
        "scene_durations": validate_scene_durations(scenes),
        "music_mapping": validate_music_mapping(scenes, music_structure, format_type),
        "animation_timing": validate_animation_timing(scenes, music_structure),
        "caption_sync": validate_caption_sync(scenes, music_structure, format_type),
        "tempo_consistency": validate_tempo_consistency(scenes, music_structure),
        "transitions": validate_transitions(scenes, music_structure),
        "completeness": validate_completeness(scenes, format_type)
    }

    return report

def validate_scene_durations(scenes):
    """Check timing math"""
    issues = []

    # Check total
    total = sum(s.duration for s in scenes)
    target = scenes[-1].end_time
    if abs(total - target) > 5:
        issues.append(f"Total duration mismatch: {total}s vs target {target}s")

    # Check gaps/overlaps
    for i in range(1, len(scenes)):
        if scenes[i].start_time != scenes[i-1].end_time:
            gap = scenes[i].start_time - scenes[i-1].end_time
            issues.append(f"Scene {i}: Gap/overlap of {gap}s")

    # Check duration math
    for s in scenes:
        calculated = s.end_time - s.start_time
        if calculated != s.duration:
            issues.append(f"Scene {s.number}: Duration mismatch")

    return {"pass": len(issues) == 0, "issues": issues}
```

---

## Validation Report Template

```markdown
# Music-to-Scene Validation Report

**Video Title:** [Title]
**Format:** [Song/Drama]
**Target Duration:** [X] seconds
**Scene Count:** [N] scenes

---

## ✅ VALIDATION RESULTS

### 1. Music Structure: [PASS/FAIL]
- [ ] Song structure defined with all sections
- [ ] Each section has duration specified
- [ ] Total music duration: [X]s (target: [Y]s, delta: [Z]s)
- [ ] Tempo specified: [BPM]
- [ ] Issues: [list or "None"]

### 2. Scene Duration Math: [PASS/FAIL]
- [ ] All scenes have start/end/duration
- [ ] Duration calculations correct: [N/N scenes]
- [ ] No timing gaps: [PASS/FAIL]
- [ ] No timing overlaps: [PASS/FAIL]
- [ ] Total duration: [X]s (target: [Y]s, delta: [Z]s)
- [ ] Issues: [list or "None"]

### 3. Music-to-Scene Mapping: [PASS/FAIL]
- [ ] Mapping table exists: [YES/NO]
- [ ] All scenes mapped to music sections: [N/N scenes]
- [ ] Lyrics specified for each scene: [N/N scenes]
- [ ] Timing alignment: [PASS/FAIL]
- [ ] Issues: [list or "None"]

### 4. Animation Timing: [PASS/FAIL]
- [ ] Duration specified in prompts: [N/N scenes]
- [ ] Timing breakdown provided: [N/N scenes]
- [ ] Pacing matched to tempo: [N/N scenes]
- [ ] Camera timing specified: [N/N scenes]
- [ ] Issues: [list or "None"]

### 5. Caption Synchronization: [PASS/FAIL]
- [ ] All captions have timing: [N/N captions]
- [ ] Caption duration appropriate: [N/N captions]
- [ ] Captions match lyrics: [PASS/FAIL]
- [ ] No caption overlaps: [PASS/FAIL]
- [ ] Issues: [list or "None"]

### 6. Tempo-Animation Consistency: [PASS/FAIL]
- [ ] Tempo specified: [BPM]
- [ ] Animation pacing descriptors: [PASS/FAIL]
- [ ] Character movement speed: [PASS/FAIL]
- [ ] Camera movement speed: [PASS/FAIL]
- [ ] Issues: [list or "None"]

### 7. Transitions: [PASS/FAIL]
- [ ] All transitions specified: [N/N scenes]
- [ ] Transition durations appropriate: [PASS/FAIL]
- [ ] Synced to music beats: [PASS/FAIL]
- [ ] Issues: [list or "None"]

### 8. Production Completeness: [PASS/FAIL]
- [ ] All scenes have image prompts: [N/N scenes]
- [ ] All scenes have animation prompts: [N/N scenes]
- [ ] All scenes have captions/dialogue: [N/N scenes]
- [ ] All scenes have transitions: [N/N scenes]
- [ ] Missing elements: [list or "None"]

---

## 🚨 CRITICAL ISSUES (must fix before production)

[List any critical issues that would cause production to fail]

---

## ⚠️ WARNINGS (should fix for quality)

[List any warnings that could affect quality]

---

## 📊 SUMMARY

**Overall Status:** [READY FOR PRODUCTION / NEEDS FIXES]

**Scenes Ready:** [N]/[Total]
**Critical Issues:** [N]
**Warnings:** [N]

**Next Steps:**
1. [Action item 1]
2. [Action item 2]
...

**Estimated Fix Time:** [X] minutes

---

**Validation Date:** [Date]
**Validated By:** Claude AI Video Creator
```

---

## Example Validation: Max & Momo

```markdown
# Music-to-Scene Validation Report

**Video Title:** Max & Momo's Magic Christmas Bells
**Format:** Song (High-Energy)
**Target Duration:** 220 seconds (3:40)
**Scene Count:** 11 scenes

---

## ✅ VALIDATION RESULTS

### 1. Music Structure: ✅ PASS
- [x] Song structure defined: Intro → Verse 1 → Chorus → Verse 2 → Chorus → Bridge → Final Chorus → Outro
- [x] Each section has duration: Intro (6s), Verse 1 (22s), Chorus (28s), etc.
- [x] Total music duration: 220s (target: 220s, delta: 0s) ✅
- [x] Tempo specified: 180-200 BPM (Carol of the Bells style)
- [x] Issues: None

### 2. Scene Duration Math: ✅ PASS
- [x] All scenes have start/end/duration: 11/11 ✅
- [x] Duration calculations correct: 11/11 scenes ✅
- [x] No timing gaps: PASS ✅
- [x] No timing overlaps: PASS ✅
- [x] Total duration: 220s (target: 220s, delta: 0s) ✅
- [x] Scene breakdown:
  - Scene 1: 0:00-0:18 (18s) ✅
  - Scene 2: 0:18-0:34 (16s) ✅
  - Scene 3: 0:34-0:54 (20s) ✅
  - Scene 4: 0:54-1:16 (22s) ✅
  - Scene 5: 1:16-1:32 (16s) ✅
  - Scene 6: 1:32-1:54 (22s) ✅
  - Scene 7: 1:54-2:14 (20s) ✅
  - Scene 8: 2:14-2:34 (20s) ✅
  - Scene 9: 2:34-2:58 (24s) ✅
  - Scene 10: 2:58-3:20 (22s) ✅
  - Scene 11: 3:20-3:40 (20s) ✅
- [x] Issues: None

### 3. Music-to-Scene Mapping: ✅ PASS
- [x] Mapping table exists: YES (lines 256-272)
- [x] All scenes mapped to music sections: 11/11 scenes ✅
- [x] Lyrics specified for each scene: 11/11 scenes ✅
- [x] Timing alignment: PASS ✅
  - Scene 1 → Intro + Verse 1 Part 1 ✅
  - Scene 2 → Verse 1 Part 2 ✅
  - Scene 3 → Chorus Part 1 ✅
  - Etc.
- [x] Issues: None

### 4. Animation Timing: ✅ PASS
- [x] Duration specified in prompts: 11/11 scenes ✅
- [x] Timing breakdown provided: 11/11 scenes ✅
- [x] Pacing matched to tempo (180-200 BPM): 11/11 scenes ✅
  - All prompts include "FAST-PACED", "HIGH-ENERGY", "RAPID"
  - Scene 11 correctly uses "GENTLE" for outro (appropriate)
- [x] Camera timing specified: 11/11 scenes ✅
- [x] Issues: None

### 5. Caption Synchronization: ✅ PASS
- [x] All captions have timing: 18/18 captions ✅
- [x] Caption duration appropriate (2-4s for fast tempo): 18/18 captions ✅
- [x] Captions match lyrics from song structure: PASS ✅
- [x] No caption overlaps: PASS ✅
- [x] Dual-language format consistent: PASS ✅
- [x] Issues: None

### 6. Tempo-Animation Consistency: ✅ PASS
- [x] Tempo specified: 180-200 BPM (FAST)
- [x] Animation pacing descriptors: PASS ✅
  - Scenes 1-10: "FAST-PACED", "RAPID", "HIGH ENERGY", "QUICK"
  - Scene 11: "GENTLE" (appropriate for outro)
- [x] Character movement speed: PASS ✅
  - "Max runs quickly", "Momo swings rapidly", "bouncing energetically"
- [x] Camera movement speed: PASS ✅
  - "Rapid cuts", "Quick zoom", "Dynamic movement"
- [x] Issues: None

### 7. Transitions: ✅ PASS
- [x] All transitions specified: 10/10 transitions ✅
- [x] Transition durations: 0.5s (fast tempo) ✅
- [x] Synced to music beats: PASS ✅
- [x] Issues: None

### 8. Production Completeness: ✅ PASS
- [x] All scenes have image prompts: 11/11 scenes ✅
- [x] All scenes have animation prompts: 11/11 scenes ✅
- [x] All scenes have captions: 11/11 scenes ✅
- [x] All scenes have transitions: 10/10 (no transition after last scene) ✅
- [x] Character references provided: YES ✅
- [x] Music prompt complete: YES ✅
- [x] Missing elements: None

---

## 🚨 CRITICAL ISSUES

**None** ✅

---

## ⚠️ WARNINGS

**None** ✅

---

## 📊 SUMMARY

**Overall Status:** ✅ **READY FOR PRODUCTION**

**Scenes Ready:** 11/11 ✅
**Critical Issues:** 0 ✅
**Warnings:** 0 ✅

**Next Steps:**
1. Generate character references (Max & Momo)
2. Generate music on Suno (ensure 180-200 BPM)
3. Generate 11 scene images on Leonardo.ai
4. Generate 11 scene animations on MiniMax
5. Assemble with captions and transitions

**Estimated Production Time:** 12-19 hours

---

**Validation Date:** 2025-01-28
**Validated By:** Claude AI Video Creator
**Status:** ✅ ALL VALIDATIONS PASSED
```

---

## Quick Validation Checklist

Use this during Steps 1-3 to quickly verify:

```markdown
## ⚡ QUICK VALIDATION CHECKLIST

**Before generating production prompts:**

### Music (Step 2)
- [ ] Song structure OR drama music description complete
- [ ] All sections have durations
- [ ] Total duration calculated
- [ ] Tempo specified (BPM for songs)

### Scenes (Step 4)
- [ ] Scene count matches format (11 for song, 10-12 for drama)
- [ ] Each scene has start time, end time, duration
- [ ] Scene durations add up to target duration (±5s)
- [ ] No gaps or overlaps in timing
- [ ] Music-to-scene mapping table exists (for songs)

### Animation Requirements (Step 4)
- [ ] Each scene animation prompt has "MINIMUM [X] seconds"
- [ ] Timing breakdown within each animation
- [ ] Pacing matched to music tempo

### Captions (Step 4)
- [ ] Each caption has timing (start-end)
- [ ] Caption duration appropriate for tempo
- [ ] Captions match song lyrics exactly

### Transitions (Step 4)
- [ ] Each scene has transition specified
- [ ] Transition duration appropriate for tempo
- [ ] Transitions sync to music beats (for songs)

**IF ALL CHECKED:** ✅ Proceed to Step 5 (Generate Production Prompts)

**IF ANY UNCHECKED:** ⚠️ Fix issues before proceeding
```

---

## Benefits of Validation

### Saves Time & Money
- Catch timing errors BEFORE expensive AI generation
- Avoid regenerating scenes due to duration mismatches
- Prevent caption sync issues in post-production

### Improves Quality
- Ensures professional synchronization
- Maintains consistent energy/pacing
- Creates seamless viewing experience

### Reduces Frustration
- Clear validation report shows exactly what needs fixing
- Systematic approach prevents "what's wrong?" confusion
- Confidence before starting production

---

**END OF VALIDATION FRAMEWORK**
