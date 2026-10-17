# Telugu -> English Transcript Translation: Handoff

_Last updated 2026-10-17 08:52 UTC. This file is generated from the translation tracker; regenerate it rather than editing the tables by hand._

## Goal

Translate the 117 Telugu YouTube auto-caption transcripts in the repo root (`<videoId>.txt`) into English and save each one, in the same folder, as `<English title>.txt`, where the title is an appropriate name of at most 4 words. The original Telugu files stay untouched. The non-transcript files (`Bhava & Yoga.txt`, `Birth Dates.txt`, the `.md` notes) are out of scope.

## Status

- Files: **24 of 117 done** (23 committed to `claude/wonderful-fermat-szzyo8`), 7 in progress, 86 not started.
- Caption lines translated: 18,495 of 129,483 (14.3%).
- Estimated completion: about 2026-10-17 14:51 UTC at the current rate (310 lines/min).

## Pending

- [ ] Translate the remaining files (see the table below).
- [ ] Commit and push finished files in batches to `claude/wonderful-fermat-szzyo8` (a draft PR tracks the branch).
- [ ] Final QA: every English file has the same number of caption lines as its source, no Telugu script, header line present.
- [ ] Final commit; mark the PR ready for review.

## Conventions

- **Output format**: line 1 is a header `# <videoId>\t<original YouTube title>\tlang=en (translated from te)`; every following line is `<timestamp> <English>` with exactly the same timestamps as the source, one line per caption line. CRLF line endings, like the source files.
- **File names**: at most 4 words, derived from the YouTube title, safe on Windows/macOS/Linux (no `/ \ : * ? " < > |`).
- **Translation**: faithful line by line, no summarising; conversational tone kept; Telugu/Sanskrit terms of art romanized (bhava, dasha, bhukti, nakshatra, yoga, dosha, karaka, gandanta, ...); planets and signs in English; `lagnam` = ascendant; star lord / sub lord / sign lord; `(?)` marks a word that is unclear in the auto-captions; `(inaudible)` marks a caption line with no intelligible speech.
- **Workflow**: ten background agents (queues 1-10) plus the coordinator (queue 0) translate in blocks of about 60 lines; a validator checks each block (timestamps match the source, no Telugu script, no condensed output) before it is saved; a transcript is written to the repo only when all its lines are done.

## Resuming after an interruption

- Finished transcripts are committed on `claude/wonderful-fermat-szzyo8`; anything marked *Done (committed)* below is safe.
- In-progress blocks live only in the session's scratchpad (`scratchpad/work/<videoId>.en.txt`) and do not survive the cloud container. A fresh session restarts those files from line 1; nothing else is lost.
- The video ID -> English file name mapping is the table below.

## File status

| # | Video ID | Original title | English file | Status | Queue |
|---|----------|----------------|--------------|--------|-------|
| 1 | `Nf_09LbAKyU` | Astrology Utility in Modern Life | `Astrology in Modern Life.txt` | Done (committed) | 3 |
| 2 | `PIBb3OXMtrM` | Planet Strength & Bhava Scoring Methodology | `Bhava Scoring Methodology.txt` | Done (committed) | 7 |
| 3 | `zMEp7ApMcVo` | Dynamic Natal Chart, Retrograde & Dasha Flow | `Dynamic Chart Dasha Flow.txt` | Done (committed) | 5 |
| 4 | `wF7gxcR5Ii4` | Dynamic Natal Chart, Retro & Planet Scoring | `Dynamic Chart Planet Scoring.txt` | Done (committed) | 2 |
| 5 | `O6ioSyDizWg` | Dynamic Natal Chart & Rule 4 Analysis | `Dynamic Chart Rule 4.txt` | Done (committed) | 6 |
| 6 | `KYySjjrBNhk` | Foreign Travel with KP Horary & Birth Chart | `Foreign Travel KP Horary.txt` | Done (committed) | 6 |
| 7 | `LPJBFQ5jO2o` | How KP Horary Confirms Birth Chart Prediction | `KP Horary Confirms Prediction.txt` | Done (committed) | 9 |
| 8 | `fDHx24NWJSE` | KP Horary for Stock Market Predictions | `KP Horary Stock Market.txt` | Done (committed) | - |
| 9 | `nM-LOi7ApsE` | KP Prashna for Stock Market Analysis | `KP Prashna Stock Market.txt` | Done (committed) | 1 |
| 10 | `4H-YpdY4gmk` | KP Astrology & Rahu, Ketu, Vak Shuddhi | `KP Rahu Ketu Vakshuddhi.txt` | Done (committed) | - |
| 11 | `Xk_ZKNnhvIk` | Interpreting Kundali Using Structural Method | `Kundali Structural Interpretation Method.txt` | Done (committed) | - |
| 12 | `cunqWeMtS-o` | Argentine Footballer Lionel Messi Birth Chart Analysis | `Lionel Messi Birth Chart.txt` | Done (committed) | 0 |
| 13 | `b25cZKmUtVg` | Medical Astrology & Disease Predictions | `Medical Astrology Disease Predictions.txt` | Done (committed) | - |
| 14 | `PItot96_dMM` | Birth Time Rectification Using Pancha Tatwa | `Pancha Tatwa Birth Rectification.txt` | Done (committed) | 5 |
| 15 | `JY3De2pTAKU` | Planets Capacity with Performance & Resource | `Planet Capacity Performance Resource.txt` | Done (committed) | 2 |
| 16 | `p7T9GSuiqlw` | Q & A : Rule 4, Retrograde & Chart Analysis | `Q&A Rule 4 Retrograde.txt` | Done (committed) | - |
| 17 | `zrOI9lcHdR0` | RVA Playground & Lagna, Planet Friendship | `RVA Playground Planet Friendship.txt` | Done (committed) | 9 |
| 18 | `PgLi-AtRP7U` | Real-Time KP Astrology Chart Analysis | `Real-Time KP Chart Analysis.txt` | Done (committed) | 3 |
| 19 | `XQEXup6y6QA` | Understanding the Role of Sign in Predictions | `Sign Role in Predictions.txt` | Done (committed) | - |
| 20 | `6hLZ0Vi4kwU` | Interpretation Practice with One Planet Only | `Single Planet Interpretation Practice.txt` | Done (committed) | 4 |
| 21 | `RIk8bJcDg8Q` | Quiz: Reading Chart From Just Two Planets | `Two Planet Chart Quiz.txt` | Done (committed) | 1 |
| 22 | `e1x6ZnSS-s8` | Q&A of Vignana Course Class Q&A 5, 6 | `Vignana Course Q&A 5-6.txt` | Done (committed) | - |
| 23 | `fS2QLzKX9jw` | Q&A of Vignana Astrology Course - YouTube Comments | `YouTube Comments Q&A.txt` | Done (committed) | - |
| 24 | `VIisiDz80ME` | Planet Performance & Capacity Explained | `Planet Performance Capacity Explained.txt` | Done (not yet committed) | 10 |
| 25 | `wTfdyfZ105k` | Interpret Functional Malefics in 12 Houses | `Functional Malefics 12 Houses.txt` | In progress: 130/861 lines | 2 |
| 26 | `yX41uXvgLfk` | Multiple Love Breakups, Family Responsibility | `Love Breakups Family Responsibility.txt` | In progress: 670/955 lines | 6 |
| 27 | `SmeZp0Ugsm0` | Movie Dialogues into Planetary Positions | `Movie Dialogues Planetary Positions.txt` | In progress: 138/939 lines | 3 |
| 28 | `p1RuLdqiaD4` | Planet Capacity Calculator & Dynamic Chart | `Planet Capacity Calculator.txt` | In progress: 405/942 lines | 1 |
| 29 | `mnQNq_CYgA8` | Planetary Retrograde Practice Session | `Planetary Retrograde Practice Session.txt` | In progress: 709/981 lines | 5 |
| 30 | `yVcBeij58SM` | Planetary Rules, Dasha & House Analysis | `Planetary Rules Dasha Analysis.txt` | In progress: 828/862 lines | 8 |
| 31 | `AHXG7zU2cG0` | Western Progression Practice on Real Charts | `Western Progression Real Charts.txt` | In progress: 66/1009 lines | 9 |
| 32 | `RDwAfrgk1Dc` | Many Planets in 10th & 11th Houses Make Rich? | `10th 11th House Wealth.txt` | Pending | 6 |
| 33 | `0M9ts6BH-Yw` | 6th Lord Influence on Marriage Breakdown | `6th Lord Marriage Breakdown.txt` | Pending | - |
| 34 | `wxxVYO2Q5iM` | Aquarius Ascendant – Time Factor vs Horoscope | `Aquarius Ascendant Time Factor.txt` | Pending | 6 |
| 35 | `TtveM_uHyvw` | Aquarius Ascendant – Game of Wealth Creation | `Aquarius Ascendant Wealth Creation.txt` | Pending | 6 |
| 36 | `_81TvF9dbFA` | Aries Ascendant - Planetary Conjunctions | `Aries Ascendant Planetary Conjunctions.txt` | Pending | - |
| 37 | `DiVcOg2DMwo` | Advantages & Disadvantages of Every Ascendant | `Ascendant Advantages and Disadvantages.txt` | Pending | 9 |
| 38 | `HufSiPpvHhY` | Astrology Avadhanam / Reading Multiple Charts | `Astrology Avadhanam Multiple Charts.txt` | Pending | - |
| 39 | `woVSBGLmyEk` | Astrology for Beginners: Easy Roadmap | `Astrology Beginners Easy Roadmap.txt` | Pending | - |
| 40 | `sqR0OU-D9iA` | Astrology Fundamentals: Ascendant, Bhavas | `Astrology Fundamentals Ascendant Bhavas.txt` | Pending | 1 |
| 41 | `oTlAGxnxliI` | Building Astrology Knowledge Using NotebookLM | `Astrology Knowledge with NotebookLM.txt` | Pending | 5 |
| 42 | `tHtt26jXe9Q` | Astrology Quiz, Planets & Digbala | `Astrology Quiz Planets Digbala.txt` | Pending | 1 |
| 43 | `fvI985bpFKI` | Astrology Software & Calculators Updates | `Astrology Software Calculator Updates.txt` | Pending | 2 |
| 44 | `Sdu53mYVmsI` | Bhava Vibajana Explained | `Bhava Vibajana Explained.txt` | Pending | 2 |
| 45 | `_r4OWcwdcRg` | Why Cancer Ascendant is Blessed Explained | `Cancer Ascendant Is Blessed.txt` | Pending | 5 |
| 46 | `ouSrE3IHZhc` | Capricorn Ascendant – Work is Worship | `Capricorn Work Is Worship.txt` | Pending | - |
| 47 | `Q8RhctpY60Y` | Committed Marriage & Career-Oriented Analysis | `Committed Marriage Career Analysis.txt` | Pending | 5 |
| 48 | `_dUMqXvV_xs` | Conjunction of Planets for every Ascendant | `Conjunctions for Every Ascendant.txt` | Pending | 6 |
| 49 | `hZq3Ii7VBCo` | Analyze Personality Traits Step by Step in D1 | `D1 Personality Traits Analysis.txt` | Pending | 1 |
| 50 | `kkG7NCxeOZg` | Navamsa Chart, Dashamsha Chart, D9, D10 & D24 | `D9 D10 D24 Charts.txt` | Pending | 5 |
| 51 | `R8Z4wtdAiN4` | How to Predict Events Using Dasha Patterns | `Dasha Patterns Event Prediction.txt` | Pending | - |
| 52 | `WL3-5djCYlc` | Debilitated Ascendant & Moon Starlord Effects | `Debilitated Ascendant Moon Starlord.txt` | Pending | - |
| 53 | `W63E0o7lW5Y` | Diwali Magic - Predictions Like Crackers! | `Diwali Magic Predictions.txt` | Pending | 3 |
| 54 | `IZAO0yMM7NE` | What is Doshas in Astrology? Explained | `Doshas in Astrology Explained.txt` | Pending | - |
| 55 | `K0_BSFdTB2k` | Dynamic Retrograde Rules & Yogas in Astrology | `Dynamic Retrograde Rules Yogas.txt` | Pending | - |
| 56 | `k5sACoas02g` | Dynamic Retrograde Analysis with Progression | `Dynamic Retrograde with Progression.txt` | Pending | - |
| 57 | `_ohJkDcNySQ` | Fingertip Prediction, Performance & Resource | `Fingertip Prediction Performance Resource.txt` | Pending | - |
| 58 | `8Bm7oiJg6lc` | Participants Fun & Live Discussions | `Fun Live Participant Discussions.txt` | Pending | - |
| 59 | `XTsy1J_j690` | Gandanta & Sandhi Lagna Practice Session | `Gandanta Sandhi Lagna Practice.txt` | Pending | 9 |
| 60 | `V0Ts42eTewU` | Golden Prediction Technique, Astro Data Bank | `Golden Prediction Technique.txt` | Pending | - |
| 61 | `-UOrTfwy4jg` | Grading Methodology & 27 Nakshatra Stories | `Grading Methodology Nakshatra Stories.txt` | Pending | 2 |
| 62 | `mDo8Frv4vK8` | Secrets of a Great Ascendant Based on Planets | `Great Ascendant Planet Secrets.txt` | Pending | 3 |
| 63 | `OBQMvyF2I4w` | KP Astrology Introduction& Basics Explained | `KP Astrology Basics Explained.txt` | Pending | 9 |
| 64 | `xB6acg1C2_w` | KP Astrology– Practical Prediction Methods | `KP Practical Prediction Methods.txt` | Pending | - |
| 65 | `efDde6aFd_M` | Karma, Astrology Articles & Editing Insights | `Karma Articles Editing Insights.txt` | Pending | - |
| 66 | `D-YH7chNzKY` | Born to Rule : Leo Ascendant Combinations | `Leo Ascendant Ruling Combinations.txt` | Pending | 3 |
| 67 | `58Xal0HPR3o` | Leo Ascendant: Wealth & Protection Secrets | `Leo Ascendant Wealth Protection.txt` | Pending | 3 |
| 68 | `GQUqQiD5HCw` | Libra Ascendant: Reverse Combinations | `Libra Ascendant Reverse Combinations.txt` | Pending | - |
| 69 | `Dt_wD1txJ2s` | Libra Ascendant: Why Exalted Planets Fail | `Libra Exalted Planets Fail.txt` | Pending | - |
| 70 | `rUuYkiXDUzc` | Malefics Impact on Purva Phalguni Nakshatra | `Malefics on Purva Phalguni.txt` | Pending | 5 |
| 71 | `Mjac_xUOWR0` | Choose Marriage Dasha Bhukthi Based on Fate | `Marriage Dasha Bhukthi Fate.txt` | Pending | - |
| 72 | `-kPUSpNrGGk` | Powerful Results of Mars in Rahu Mahadasha | `Mars in Rahu Mahadasha.txt` | Pending | 1 |
| 73 | `XkvMHMSG1rc` | Mercury Decides Fate of Capricorn Ascendant | `Mercury Decides Capricorn Fate.txt` | Pending | 1 |
| 74 | `udLGiYZo80E` | Power of Movable Ascendant (Chara Lagna) | `Movable Ascendant Chara Lagna.txt` | Pending | - |
| 75 | `zmaogH64mIA` | Navamsha Calculation, Nakshatras Explained | `Navamsha Calculation Nakshatras Explained.txt` | Pending | - |
| 76 | `LlGLu4MrDlg` | NotebookLM for Astrology Notes & Docs | `NotebookLM Astrology Notes.txt` | Pending | 3 |
| 77 | `DvNkY2HDa5k` | Performance Scoring & Progression Analysis | `Performance Scoring Progression Analysis.txt` | Pending | - |
| 78 | `4YpumAUZbjQ` | Personality Traits & Bhava Interpretation | `Personality Traits Bhava Interpretation.txt` | Pending | - |
| 79 | `5WGr1E-bClM` | Pisces Ascendant – One Planet Saved Life | `Pisces Ascendant Life-Saving Planet.txt` | Pending | - |
| 80 | `V9fZiw6ZLCs` | Pisces Ascendant – Spirituality & Materialism | `Pisces Spirituality and Materialism.txt` | Pending | 9 |
| 81 | `dV1mqy396gU` | Planet Capacity Worksheet & Chart Analysis | `Planet Capacity Worksheet.txt` | Pending | 6 |
| 82 | `EcMj2xE5nfY` | Step-by-Step Planet & House Analysis Marks | `Planet House Analysis Marks.txt` | Pending | - |
| 83 | `S1NbGwwmPcE` | How to Interpret using, Planet, Rashi & Bhava | `Planet Rashi Bhava Interpretation.txt` | Pending | 9 |
| 84 | `D17R6UrvI5s` | Planet Strength, House Analysis & Scoring | `Planet Strength House Analysis.txt` | Pending | 5 |
| 85 | `zBuXyEYjsT8` | Planetary Capacity & Detailed Chart Analysis | `Planetary Capacity Chart Analysis.txt` | Pending | - |
| 86 | `85sbtRa82Ho` | Advanced Planetary Combinations & Detachment | `Planetary Combinations and Detachment.txt` | Pending | 6 |
| 87 | `K1qUdgLX1tA` | Real Chart Practice - Planets & Star Lords | `Planets Star Lords Practice.txt` | Pending | - |
| 88 | `ajUKaHKMV00` | Planets Role & Practical Stellar Astrology | `Planets in Stellar Astrology.txt` | Pending | 2 |
| 89 | `c1URMNIVbnM` | Power of Gemini Ascendant Explained | `Power of Gemini Ascendant.txt` | Pending | 6 |
| 90 | `N4tmZ5GP46E` | Powerful Planet Rules & Performance Explained | `Powerful Planet Performance Rules.txt` | Pending | 6 |
| 91 | `SE0cR4wRja8` | Practical Experience of Time Chart Prediction | `Practical Time Chart Prediction.txt` | Pending | 5 |
| 92 | `E4hOb4AFFLQ` | Progression & Real Life Event Mapping | `Progression Life Event Mapping.txt` | Pending | 2 |
| 93 | `Aw9y0H3Sbvo` | Progressions Practice Session by Participants | `Progressions Practice by Participants.txt` | Pending | 9 |
| 94 | `MEIMAytyyiw` | Can Progressions Predict Longevity? | `Progressions Predict Longevity.txt` | Pending | - |
| 95 | `SnNxZb7Y2YU` | Progressive Timelines & Life Correlations | `Progressive Timelines Life Correlations.txt` | Pending | 5 |
| 96 | `woiOI4bqQgE` | Prompt to Judge Horoscope Step by Step | `Prompt to Judge Horoscope.txt` | Pending | - |
| 97 | `cvCNN5qYJe8` | Yoga Bhanga Due to Rahu & Ketu Influence | `Rahu Ketu Yoga Bhanga.txt` | Pending | 3 |
| 98 | `xDwTZ9qq41I` | Fun Astrology Exercise Rakhi Pournami Special | `Rakhi Pournami Astrology Exercise.txt` | Pending | 2 |
| 99 | `00UXbzNHkNU` | Step-by-Step Practice of Retrograde Rules | `Retrograde Rules Step-by-Step.txt` | Pending | - |
| 100 | `4_Suv99zoHk` | Retrograde Planets, Rules & Exceptions | `Retrograde Rules and Exceptions.txt` | Pending | - |
| 101 | `Rrr9uJ6YLMQ` | Sagittarius Ascendant – Birth Chart Analysis | `Sagittarius Ascendant Chart Analysis.txt` | Pending | - |
| 102 | `kieGqNhfjgQ` | Sagittarius Ascendant – Truly Blessed ? | `Sagittarius Ascendant Truly Blessed.txt` | Pending | 1 |
| 103 | `uBZwa6_5FoU` | Same Birth Time but Only One CM or PM ? | `Same Birth Different Fates.txt` | Pending | - |
| 104 | `DMkk4HRRw3s` | Scorpio Ascendant – Ultimate Power, Property | `Scorpio Ascendant Power Property.txt` | Pending | - |
| 105 | `QXXYb9FqiW8` | Scorpio Ascendant – Surprising Real Charts | `Scorpio Ascendant Surprising Charts.txt` | Pending | 3 |
| 106 | `XV9ZHhCuG28` | Live Q&A and Stellar Astrology Segment Finish | `Stellar Astrology Finale Q&A.txt` | Pending | - |
| 107 | `-_hJEZmaPH4` | Storytelling with Planets | `Storytelling with Planets.txt` | Pending | - |
| 108 | `mWxcA15ZRuQ` | Affliction of Stree Karaka Grahas in Jathakam | `Stree Karaka Grahas Affliction.txt` | Pending | - |
| 109 | `DRMrp_4JTQg` | Strongest Planet in One Sign | `Strongest Planet in Sign.txt` | Pending | 2 |
| 110 | `Iq7NeRaSe70` | Students Learning Through Practice Session | `Students Learning Practice Session.txt` | Pending | 5 |
| 111 | `lMFmxlnk3hs` | Taurus Ascendant Secrets Explained | `Taurus Ascendant Secrets Explained.txt` | Pending | 3 |
| 112 | `LaKeVc0cD9g` | Understanding Yogas: Basics & Chart Reading | `Understanding Yogas Chart Reading.txt` | Pending | 1 |
| 113 | `NTpHeI4yidw` | How Astrologers Verify Events from a Kundali | `Verify Events from Kundali.txt` | Pending | 9 |
| 114 | `YhfJldEAexI` | Virgo Ascendant Deep Karmic Secrets | `Virgo Ascendant Karmic Secrets.txt` | Pending | 9 |
| 115 | `9L1wy4ONMi0` | Virgo Ascendant : Mastering Real-Time Charts | `Virgo Ascendant Real-Time Charts.txt` | Pending | 2 |
| 116 | `QZhHCHCS0jo` | Western Progression Basics & 5 Major Aspects | `Western Progression Basics.txt` | Pending | 1 |
| 117 | `43wY6GwZdxo` | What have we learned up to this point? | `What We Have Learned.txt` | Pending | 6 |

