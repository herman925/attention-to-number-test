# Attention to Number Test Generator

A web-based stimulus generator for designing cognitive assessment materials that investigate the interplay between numerical attention (subitizing) and visual feature processing in human perception. The application produces standardized image stimuli for deployment in external experimental platforms; it does not administer participant-facing tasks or record behavioural data.

## Table of Contents

- [Attention to Number Test Generator](#attention-to-number-test-generator)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Academic Background](#academic-background)
    - [Subitizing and Numerical Cognition](#subitizing-and-numerical-cognition)
    - [Theoretical Framework](#theoretical-framework)
  - [Experiment Methodology](#experiment-methodology)
    - [Test Structure](#test-structure)
    - [Experimental Conditions](#experimental-conditions)
      - [1. Shape-Based Tests](#1-shape-based-tests)
      - [2. Fruit-Based Tests](#2-fruit-based-tests)
    - [Visual Arrangement Algorithm](#visual-arrangement-algorithm)
  - [Web Application Features](#web-application-features)
    - [User Interface](#user-interface)
    - [Implementation Details](#implementation-details)
  - [Usage Instructions](#usage-instructions)
    - [For Researchers](#for-researchers)
    - [Experimental Design Recommendations](#experimental-design-recommendations)
  - [Research Applications](#research-applications)
  - [Technical Specifications](#technical-specifications)
    - [Output Format](#output-format)
    - [Browser Compatibility](#browser-compatibility)
    - [Performance](#performance)
  - [Theoretical Considerations](#theoretical-considerations)
    - [Why This Test Design?](#why-this-test-design)
    - [Limitations and Considerations](#limitations-and-considerations)
  - [Future Research Directions](#future-research-directions)
  - [References](#references)
  - [Citation](#citation)
  - [License](#license)
  - [Contributing](#contributing)
  - [Contact](#contact)

## Overview

This application generates standardized visual stimulus sets designed to support experiments on how humans attend to numerical quantities versus visual features (shape, color, pattern) when processing sets of objects. Researchers can export stimuli for integration into their own timing, presentation, and data-collection pipelines (e.g., PsychoPy, jsPsych, online survey platforms).

## Academic Background

### Subitizing and Numerical Cognition

Subitizing refers to the rapid, accurate, and confident enumeration of small quantities (typically 1-4 items) without conscious counting. This cognitive phenomenon has been extensively studied in cognitive psychology and neuroscience as a fundamental aspect of numerical cognition.

Research on numerosity demonstrates that numerical quantity can function as a primary perceptual feature, similar to color or shape, reinforcing the need for stimuli that isolate number from other attributes (Anobile et al., 2016; Burr & Ross, 2008). Attentional manipulations further show that directing spatial or object-based attention to target arrays improves estimation accuracy and speed, indicating that well-crafted cues can amplify numerical sensitivity (Pomè et al., 2020). Structured configurations, including shape templates and grid-based layouts, have been linked to enhanced subitizing performance and distinctive neural signatures, underscoring the value of controlling spatial composition in experimental materials (Gheorghiu & Dering, 2020; Gheorghiu & Goldschmitt, 2022). Foundational picture-matching experiments also demonstrated that salient competing features can suppress children’s focus on numerosity unless those distractors are carefully managed, motivating the generator’s systematic feature controls (Chan & Mazzocco, 2017). In parallel, studies reveal that color diversity and other contextual variations can bias magnitude perception, necessitating deliberate management of feature contrasts when designing research stimuli (Li et al., 2018, 2025). Broader investigations highlight how spatial information transfers across sensory modalities and how individual differences shape numerosity attention, situating subitizing within a complex network of parallel processing and cross-modal integration mechanisms (Feigenson et al., 2004; Kaufman et al., 1949; Ziegler et al., 2023).

### Theoretical Framework

The generator is structured to illuminate two interconnected mechanisms—rapid quantity discrimination and the integration of numerical and non-numerical features—by allowing researchers to manipulate which attributes align or conflict within a single stimulus. Target arrays can combine shape, fruit type, color, pattern, and quantity, while comparison arrays selectively vary these attributes to reveal whether participants prioritise number or are captured by competing visual features. Because correct responses emerge only when observers privilege numerosity over salient distractors, the resulting image sets offer a controlled platform for probing how attention, perceptual grouping, and feature-based competition interact during subitizing and related cognitive processes.

## Experiment Methodology

### Test Structure

Each generated test follows a consistent structure:

```
[Target Box] [Choice 1] [Choice 2] [Choice 3] [Choice 4]
```

- **Target Box (目标)**: Displays the reference stimulus with a specific number of objects
- **Four Choice Boxes**: Present alternative options, where exactly ONE matches the target's numerical quantity

### Experimental Conditions

#### 1. Shape-Based Tests
Tests using geometric shapes to investigate number vs. shape/color attention.

**Target Parameters:**
- **Target Shape**: Circle, square, triangle, rectangle, or star
- **Target Color**: Six distinct colors (orange, teal, yellow, purple, blue, red)
- **Target Pattern**: Solid fill, horizontal stripes, vertical stripes, checkered, or white dots
- **Target Count**: 2-6 objects

**Choice Generation Rules (Four-Role Structure):**
- **Color-only foil**: Shares the target color but uses a different shape and a different count
- **Shape-only foil**: Shares the target shape but uses a different color and a different count
- **Count-only option (correct answer)**: Shares the target count but differs in both shape and color
- **Full distractor**: Differs from the target in shape, color, and count
- All counts and colors across the four choices remain unique to preserve diagnostic clarity
- Patterns mirror the target selection so that texture never signals the answer; in other words, pattern is held constant across all four shape choices unless you explicitly vary it for the target

**Cognitive Focus**: This condition tests whether participants can focus on numerical quantity while ignoring shape identity and color—features that are typically more salient in visual processing. Structured shapes have been shown to prime numerosity estimates when spatial layouts reinforce shape templates (Gheorghiu & Dering, 2020; Gheorghiu & Goldschmitt, 2022).

#### 2. Fruit-Based Tests
Tests using fruit imagery to examine ecological validity and pattern processing.

**Target Parameters:**
- **Target Fruit**: Apple, pear, orange, banana, or cherry
- **Target Pattern**: Horizontal stripes, vertical stripes, checkered, white dots, or "Full Random"
- **Target Count**: 2-6 objects

**Choice Generation Rules (Four-Role Structure, with pattern as the "color" dimension):**
- **Pattern-only foil**: Shares the target’s overlay pattern (e.g., horizontal stripes) but uses a different fruit type and a different count
- **Fruit-only foil**: Shares the target fruit type (e.g., apple) but uses a different overlay pattern and a different count
- **Count-only option (correct answer)**: Shares the target count but uses a different fruit type and typically a different overlay pattern
- **Full distractor**: Differs from the target in fruit type, overlay pattern, and count
- Each choice uses a unique fruit type and a unique count to maximize diagnostic clarity

**Spatial Arrangement Feature:**
- Fruit groups can be positioned at different locations within boxes (top, bottom, left, right, center)
- Per-fruit X/Y offset controls shift whole clusters independently along horizontal and vertical axes, yielding symmetric centering by default while enabling intentional spatial cues
- This adds spatial attention as an additional dimension

**Pattern Modes:**
- **Fixed Pattern**: All fruit stimuli in a given test use the same selected white-on-color overlay (horizontal stripes, vertical stripes, checkered, or white dots) for the target, and the four comparison choices are then constructed according to the four-role rule above (pattern-only, fruit-only, count-only, distractor).
- **Full Random**: The target uses a single concrete overlay pattern drawn from the four-pattern pool, and the four comparison choices are again constructed according to the four-role rule, with their overlays sampled from the same pool. This mode tests pattern discrimination alongside numerical attention and prevents color-driven numerosity biases observed in high-variety displays (Li et al., 2025).

**Cognitive Focus**: Fruit stimuli provide more ecologically valid, real-world objects, allowing investigation of whether numerical processing differs for familiar vs. abstract objects. The condition also enables examination of how individual differences in spontaneous attention to numerosity manifest across task contexts (Mazzocco et al., 2020) and how spatial organisation or cross-modal cues influence enumeration strategies (Li et al., 2018; Ziegler et al., 2023).

### Visual Arrangement Algorithm

The application uses intelligent spatial arrangement algorithms:

**For Shape Tests:**
- Grid-based layouts optimized for each count (2: horizontal pair, 3: triangle, 4: 2×2 grid, 5: pentagon-like, 6: 3×2 grid)
- Ensures all objects are fully visible within box boundaries
- Consistent spatial distribution for comparable visual density

**For Fruit Tests:**
- Compact grouping of fruits within each box
- Entire groups can be offset to different positions (spatial attention manipulation)
- Layout adapts based on count and position (e.g., 6 fruits arranged as 3×2 horizontally or 2×3 vertically)
- Independent X/Y offset controls per fruit type keep clusters centered by default while allowing systematic shifts that mirror evidence on contextual numerosity cues (Gheorghiu & Goldschmitt, 2022; Li et al., 2018).

## Web Application Features

### User Interface

The generator provides an intuitive interface with real-time preview:

1. **Target Type Selection**
   - Shape mode: Geometric shapes with color selection
   - Fruit mode: Realistic fruit illustrations

2. **Configurable Parameters**
   - **Target Count**: Select 2-6 objects
   - **Shape/Fruit Selection**: Choose from 5 shape types or 5 fruit types
   - **Color Selection**: (Shape mode only) Six predefined colors
   - **Pattern Selection**: Shape mode offers solid fill plus the four overlays; fruit mode uses the overlay set with optional Full Random cycling

3. **Visual Previews**
   - Real-time preview of selected shape/fruit
   - Color swatch preview
   - Pattern preview with visual representation

4. **Test Generation**
   - One-click generation with randomized correct answer position
   - High-resolution canvas output (2400×800 pixels)
   - Ensures unique counts and features across all choices

5. **Export Functionality**
   - Download tests as PNG images
   - Timestamped filenames for organization
   - Suitable for printing or digital presentation

### Implementation Details

**Technology Stack:**
- Pure HTML5, CSS3, and JavaScript (no external dependencies)
- HTML Canvas API for high-quality rendering
- Responsive design for various screen sizes

**Rendering Features:**
- **Custom Shape Drawing**: Mathematically defined geometric shapes with precise rendering
- **Fruit Illustrations**: Stylized fruit drawings with botanical details (stems, leaves, highlights)
- **Pattern Overlay System**: Clipping-based pattern application maintains shape integrity
- **Anti-aliasing**: Smooth edges for professional appearance

**Randomization:**
- Correct answer position randomly distributed across four choices
- Foil counts generated to ensure diversity without repetition
- Pattern assignment in "Full Random" mode ensures variety

## Usage Instructions

### For Researchers

1. **Open the Application**
   - Open `index.html` in any modern web browser
   - No installation or server required

2. **Configure Test Parameters**
   - Select target type (Shape or Fruit)
   - Choose target count (number of objects)
   - Select specific shape/fruit type
   - For shapes: select color
   - Select pattern type

3. **Generate Tests**
   - Click "Generate Test" button
   - New test image is created with randomized correct answer position
   - Console logs indicate correct answer number for experimenter reference

4. **Export for Study**
   - Click "Download as PNG" to save the test image
   - Import images into your experimental software or print for paper-based testing
   - Organize files by timestamp

5. **Integrate with Experimental Platform**
   - Present images within your preferred data-collection environment (e.g., PsychoPy, jsPsych, Gorilla)
   - Implement timing, response capture, and analytics externally; the generator supplies stimuli only

### Experimental Design Recommendations

**Within-Subjects Design:**
- Generate multiple tests varying count while keeping other features constant
- Counterbalance presentation order

**Between-Subjects Design:**
- Create different test sets with varying complexity (e.g., different pattern conditions)

**Practice Trials:**
- Generate simpler tests (count = 2 or 3) for participant familiarization

**Measurement Variables:**
- Response accuracy (correct choice selection)
- Response time (implement timing in your experimental software)
- Error patterns (which foils are selected)

## Research Applications

This stimulus generator supports investigations of:

1. **Development of Numerical Cognition**
   - Test children at different ages to track subitizing development
   - Compare performance across different age groups

2. **Individual Differences**
   - Examine whether some individuals have stronger number vs. feature attention
   - Correlate with other cognitive measures (working memory, math ability)
   - Leverage task contexts to study variability in spontaneous numerosity focus across populations (Mazzocco et al., 2020)

3. **Perceptual Load Effects**
   - Manipulate visual complexity through pattern variations.
   - Study how increased perceptual load affects numerical processing, including color-driven biases and grouping effects (Li et al., 2018; Li et al., 2025).

4. **Cross-Cultural Studies**
   - Test whether numerical attention patterns are universal or culturally influenced
   - Use shape vs. fruit conditions to examine familiarity effects

5. **Clinical Populations**
   - Assess numerical cognition in dyscalculia, ADHD, autism spectrum disorder
   - Compare numerical attention patterns to neurotypical controls

6. **Neuroimaging Research**
   - Use as stimulus material in fMRI or EEG studies
   - Identify neural correlates of numerical vs. feature attention while maintaining precise control over spatial context (Gheorghiu & Dering, 2020; Pomè et al., 2020).

## Technical Specifications

### Output Format
- **Resolution**: 2400×800 pixels (high DPI for printing)
- **Format**: PNG image with white background
- **Color Space**: RGB

### Browser Compatibility
- Chrome/Edge (recommended)
- Firefox
- Safari
- Any modern browser with HTML5 Canvas support

### Performance
- Instant generation (< 100ms)
- Lightweight (single HTML file, ~54KB)
- No network requests required (fully offline capable)

## Theoretical Considerations

### Why This Test Design?

The experimental paradigm implemented here addresses several methodological challenges in numerical cognition research:

1. **Feature Conflict**: By making the correct choice differ in salient features (shape, color) while matching in number, we create a situation where number must be explicitly attended to

2. **Unique Foils**: Ensuring all choices have unique counts prevents confusion and makes the numerical discrimination task clearer

3. **Varied Arrangements**: Spatial arrangement variations prevent participants from using position or configuration as a cue (must truly enumerate) and enable controlled investigations of grouping effects on perceived numerosity (Gheorghiu & Goldschmitt, 2022; Li et al., 2018).

4. **Pattern Variation**: Pattern overlays add complexity without changing object identity, allowing study of how texture/pattern affects enumeration

### Limitations and Considerations

- **Presentation Timing**: This tool generates static images; researchers must implement timing controls in their experimental software
- **No Built-in Data Collection**: Response recording must be handled separately
- **Limited to Visual Modality**: Does not test auditory or tactile numerosity perception
- **Fixed Complexity Levels**: Number range limited to 2-6 (subitizing range + immediate post-subitizing range)

## Future Research Directions

Potential extensions of this paradigm:

1. **Dynamic Stimuli**: Animate objects appearing/disappearing to study numerosity encoding in temporal sequences
2. **Mixed Modalities**: Combine visual numerosity with auditory tones
3. **Continuous vs. Discrete**: Add tests with continuous quantities (liquid volumes, line lengths)
4. **Ratio Effects**: Systematically vary the ratio between correct and foil counts to study Weber's law for numerosity
5. **Interference Effects**: Add distractor elements that don't count toward the total

## References

<p style="margin-left:0.5in; text-indent:-0.5in;">Anobile, G., Cicchini, G. M., &amp; Burr, D. C. (2016). Number as a primary perceptual attribute: A review. <em>Perception, 45</em>(1–2), 5–31. https://doi.org/10.1177/0301006615614461</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Burr, D., &amp; Ross, J. (2008). A visual sense of number. <em>Current Biology, 18</em>(6), 425–428. https://doi.org/10.1016/j.cub.2008.02.052</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Chan, J. Y.-C., &amp; Mazzocco, M. M. M. (2017). Competing features influence children’s attention to number. <em>Journal of Experimental Child Psychology, 156</em>, 62–81. https://doi.org/10.1016/j.jecp.2016.11.008</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Dehaene, S. (2011). <em>The number sense: How the mind creates mathematics</em> (Revised and expanded ed.). Oxford University Press.</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Feigenson, L., Dehaene, S., &amp; Spelke, E. (2004). Core systems of number. <em>Trends in Cognitive Sciences, 8</em>(7), 307–314. https://doi.org/10.1016/j.tics.2004.05.002</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Gheorghiu, E., &amp; Dering, B. R. (2020). Shape facilitates number: Brain potentials and microstates reveal the interplay between shape and numerosity in human vision. <em>Scientific Reports, 10</em>, 12413. https://doi.org/10.1038/s41598-020-68788-4</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Gheorghiu, E., &amp; Goldschmitt, D. (2022). Spatial and chromatic properties of numerosity estimation in isolation and context. <em>PLOS ONE, 17</em>(9), e0274564. https://doi.org/10.1371/journal.pone.0274564</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Kaufman, E. L., Lord, M. W., Reese, T. W., &amp; Volkmann, J. (1949). The discrimination of visual number. <em>American Journal of Psychology, 62</em>(4), 498–525. https://doi.org/10.2307/1418567</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Li, Q., Nakashima, R., &amp; Yokosawa, K. (2018). Task-irrelevant spatial dividers facilitate counting and numerosity estimation. <em>Scientific Reports, 8</em>, 15424. https://doi.org/10.1038/s41598-018-33877-y</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Li, Q., Ting, G., Kikuno, Y., &amp; Yokosawa, K. (2025). The influence of increasing color variety on numerosity estimation and counting. <em>Psychonomic Bulletin &amp; Review</em>. Advance online publication. https://doi.org/10.3758/s13423-024-02625-x</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Mazzocco, M. M. M., Chan, J. Y.-C., Bye, J. K., Padrutt, E. R., Praus-Singh, T., Lukowski, S., Brown, E., &amp; Olson, R. E. (2020). Attention to numerosity varies across individuals and task contexts. <em>Mathematical Thinking and Learning, 22</em>(4), 258–280. https://doi.org/10.1080/10986065.2020.1818467</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Pomè, A., Thompson, D., Burr, D. C., &amp; Halberda, J. (2020). Location- and object-based attention enhance number estimation. <em>Attention, Perception, &amp; Psychophysics, 82</em>(8), 4181–4196. https://doi.org/10.3758/s13414-020-02178-w</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Trick, L. M., &amp; Pylyshyn, Z. W. (1994). Why are small and large numbers enumerated differently? A limited-capacity preattentive stage in vision. <em>Psychological Review, 101</em>(1), 80–102. https://doi.org/10.1037/0033-295X.101.1.80</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Wolfe, J. M., &amp; Horowitz, T. S. (2004). What attributes guide the deployment of visual attention and how do they do it? <em>Nature Reviews Neuroscience, 5</em>(6), 495–501. https://doi.org/10.1038/nrn1411</p>
<p style="margin-left:0.5in; text-indent:-0.5in;">Ziegler, M. C., Stricker, L. K., &amp; Drewing, K. (2023). The role of spatial information in an approximate cross-modal number matching task. <em>Attention, Perception, &amp; Psychophysics, 85</em>(4), 1253–1266. https://doi.org/10.3758/s13414-023-02658-9</p>

## Citation

If you use this tool in your research and require APA 7th edition formatting, cite it as:

<p style="margin-left:0.5in; text-indent:-0.5in;">Chan, H. K. K. (2025). <em>Attention to number test generator</em> [Computer software]. https://github.com/herman925/attention-to-number-test</p>

*Update the year and add a version identifier if your study uses a different release.*

## License

This project is open source and available for research and educational purposes.

## Contributing

Contributions are welcome! Potential areas for enhancement:
- Additional shape/fruit types
- Configurable color schemes
- Batch generation features
- Integration with experimental software (jsPsych, PsychoPy)
- Accessibility features (screen reader support, keyboard navigation)

## Contact

For questions, suggestions, or collaboration opportunities, please open an issue on the GitHub repository.

---

**Note**: This tool generates stimulus materials for research purposes. Researchers are responsible for obtaining appropriate ethical approval and informed consent for their studies.
