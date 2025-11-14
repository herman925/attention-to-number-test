# Attention to Number Test Generator

A web-based stimulus generator for designing cognitive assessment materials that investigate the interplay between numerical attention (subitizing) and visual feature processing in human perception. The application produces standardized image stimuli for deployment in external experimental platforms; it does not administer participant-facing tasks or record behavioural data.

## Table of Contents

- [Attention to Number Test Generator](#attention-to-number-test-generator)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Academic Background](#academic-background)
    - [Relation to Chan \& Mazzocco (2017)](#relation-to-chan--mazzocco-2017)
    - [Subitizing and Numerical Cognition](#subitizing-and-numerical-cognition)
    - [Theoretical Framework](#theoretical-framework)
  - [Methodology](#methodology)
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

### Relation to Chan & Mazzocco (2017)

The stimulus logic implemented in this generator is intentionally aligned with the picture-matching paradigm introduced by Chan and Mazzocco (2017), in which children view a target picture and must select which of several alternatives “goes with” the target. In their work, the critical question was whether children spontaneously attend to numerosity when other, often more salient, features such as object identity, size, or configuration provide competing bases for matching. The present tool adopts this logic while making the numerical rule fully explicit and programmable: for every generated trial, exactly one comparison array matches the target in object count, whereas the remaining foils selectively match only non-numerical attributes or differ on all controlled dimensions. This design enables direct examination of “competing features” in a Chan and Mazzocco–style task, while providing experimenters with fine-grained control over which features compete on each trial.

Beyond this direct correspondence, the generator offers a flexible platform for extending Chan and Mazzocco’s findings. The inclusion of both abstract geometric shapes and more ecologically valid fruit stimuli within a common four-choice picture-matching framework allows systematic comparison of performance across stimulus classes while holding task structure constant. The capacity to parametrically manipulate the salience of non-numerical features—via colour, pattern, and spatial location—further enables precise tests of how strongly these attributes draw attention away from numerosity under different task demands, age ranges, or individual-difference profiles. Finally, because the tool outputs static images that can be embedded in diverse experimental environments, it supports cross-study and cross-laboratory replication efforts in which the core logic of the original paradigm is preserved but the specific visual realisation can be adapted, localised, or systematically diversified.

Taken together, these features allow researchers to operationalise SFON—understood as spontaneous focus on number within tasks that do not explicitly require numerical processing—within a tightly controlled yet ecologically flexible picture-matching framework.

### Subitizing and Numerical Cognition

Subitizing refers to the rapid, accurate, and confident apprehension of small numerosities (typically 1–4 items) without recourse to serial counting. Classic and contemporary work positions subitizing as a core component of human numerical cognition, supported by limited-capacity perceptual mechanisms that differ qualitatively from those involved in estimating larger sets (Feigenson et al., 2004; Kaufman et al., 1949; Trick & Pylyshyn, 1994). In this view, numerosity is not merely inferred from other stimulus properties (e.g., total area or density) but can function as a quasi-“primary” attribute of visual scenes, available to attention in much the same way as color, orientation, or motion (Anobile et al., 2016; Burr & Ross, 2008).

At the same time, a large body of evidence shows that access to numerosity is constrained by how attention is deployed across space and objects. Studies manipulating spatial and object-based attention demonstrate that directing attention to target arrays can sharpen numerical estimates and reduce variability, whereas dividing attention or increasing perceptual load tends to impair performance (Pomè et al., 2020; Wolfe & Horowitz, 2004). Related work on structured configurations indicates that the spatial organisation of items—such as whether they conform to familiar geometric templates or grid-like layouts—modulates both behavioural subitizing performance and associated neural signatures (Gheorghiu & Dering, 2020; Gheorghiu & Goldschmitt, 2022). These findings motivate the use of carefully controlled spatial arrangements and feature contrasts when designing stimuli intended to probe “pure” numerical processing.

Crucially, numerosity judgments unfold in the presence of multiple, potentially competing visual features. Foundational picture-matching experiments with children have shown that when several attributes (e.g., object identity, colour, size, or spatial arrangement) are simultaneously available, participants do not invariably prioritise number; instead, attention can be captured by highly salient non-numerical features, leading to systematic deviations from number-based matching (Chan & Mazzocco, 2017). This line of work has been developed under the construct of spontaneous focus on number (SFON), which denotes the tendency to attend to and use numerosity spontaneously in situations that do not explicitly demand numerical processing, and which varies across individuals, task demands, and display properties (Feigenson et al., 2004; Mazzocco et al., 2020).

Contextual manipulations further reveal how low-level visual features can bias magnitude perception. For example, spatial dividers and grouping cues can facilitate counting and numerosity estimation by segmenting arrays into subgroups (Li et al., 2018; Ziegler et al., 2023), whereas increasing colour variety or other forms of feature heterogeneity can distort perceived numerosity or alter enumeration strategies (Li et al., 2025). Together, these findings situate subitizing and approximate number processing within a broader framework of attentionally mediated, feature-rich perception in which numerical information is continuously integrated—and sometimes competes—with other dimensions of the visual scene.

### Theoretical Framework

The present generator is designed to operationalise these insights by offering a controlled yet flexible platform for constructing picture-matching stimuli in which numerical and non-numerical attributes can be systematically aligned or placed in conflict. Each trial presents a target array and four comparison arrays that vary along several dimensions: numerosity (object count), object identity (geometric shape or fruit type), surface colour (shape mode), texture or overlay pattern, and spatial location of object clusters within each box. By manipulating which features match the target and which features differ, researchers can induce situations in which the numerically correct choice is also the most visually distinctive, or conversely, in which numerosity is pitted against salient competing features.

In the shape-based condition, the correct alternative is defined solely by matching the target’s numerosity while differing in both shape and colour, whereas the remaining foils selectively share colour, share shape, or differ on all three dimensions. In the fruit-based condition, the design extends this logic by treating the spatial location of clustered fruits within each box, and their overlay pattern, as additional feature dimensions. The four comparison options are constructed so that exactly one matches the target in numerosity alone, one shares only the spatial location, one shares only the pattern, and one is a full distractor differing on all controlled dimensions. Across trials, all four edge locations (top, bottom, left, right) are used in a fully specified manner, mirroring the emphasis in the literature on spatial attention, grouping, and the salience of competing features (Chan & Mazzocco, 2017; Gheorghiu & Goldschmitt, 2022; Li et al., 2018; Pomè et al., 2020).

Conceptually, this architecture aligns with SFON-inspired picture-matching paradigms (Chan & Mazzocco, 2017; Mazzocco et al., 2020) in which participants view a target picture and must identify which of several alternatives “goes with” or “is the same as” the target. Here, however, the mapping rule is explicitly numerical: exactly one option matches the target count, whereas the others instantiate distinct combinations of non-numerical similarity. This enables fine-grained analyses of error patterns—such as preferential selection of colour-only, pattern-only, or location-only foils—as behavioural indicators of which features dominate attention under different conditions, ages, or individual-difference profiles. By embedding these manipulations in a transparent, configurable image generator, the tool is intended to support rigorous experimental tests of how, when, and for whom numerosity functions as an attended dimension in complex, feature-rich visual environments.

## Methodology

### Test Structure

In line with SFON-inspired picture-matching paradigms (Chan & Mazzocco, 2017; Mazzocco et al., 2020), each generated test instance presents a single target array alongside four comparison arrays within a fixed spatial layout (see Figure 1):

```
[Target Box] [Choice 1] [Choice 2] [Choice 3] [Choice 4]
```

- **Target Box (目标)**: Displays the reference stimulus with a specific number of objects and a particular feature configuration (shape or fruit type, colour or overlay pattern, and spatial layout).
- **Four Choice Boxes**: Present alternative options, exactly ONE of which matches the target's numerical quantity; the remaining options are structured foils that share only one feature dimension (e.g., colour, shape, pattern, or spatial location) or differ from the target on all controlled dimensions.

This design preserves the intuitive “which picture goes with the target?” format familiar from child-friendly SFON tasks while making the numerical decision rule transparent and programmable. Because the correct answer is always the unique numerosity match, selection of a non-numerical foil can be interpreted as evidence that a competing feature, rather than number, dominated attention on that trial. In a full APA-style manuscript, the canonical layout illustrated above would typically be presented as **Figure 1** (stimulus configuration for the attention-to-number task).

### Experimental Conditions

#### 1. Shape-Based Tests
Tests using geometric shapes to investigate number vs. shape/color attention.

**Target Parameters:**
- **Target Shape**: Circle, square, triangle, rectangle, or star
- **Target Color**: Six distinct colors (orange, teal, yellow, purple, blue, red)
- **Target Pattern**: Solid fill, horizontal stripes, vertical stripes, checkered, or white dots
- **Target Count**: 2-6 objects

**Table 1**
Feature structure of shape-based comparison options

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

**Table 2**
Feature structure of fruit-based comparison options

**Choice Generation Rules (Four-Role Structure, with fruit, pattern, and location as key dimensions):**

| Role                            | Fruit vs Target               | Pattern vs Target                    | Location vs Target                                  | Count vs Target           |
|---------------------------------|-------------------------------|--------------------------------------|-----------------------------------------------------|---------------------------|
| **Pattern-only foil**           | Different fruit               | **Same pattern**                     | Different spatial location (one of the other edges) | Different count           |
| **Location-only foil**          | Different fruit               | Different pattern                    | **Same spatial location**                           | Different count           |
| **Count-only option (correct)** | Different fruit               | Different pattern                    | Different spatial location (one of the other edges) | **Same count**            |
| **Full distractor**             | Different fruit               | Different pattern                    | Different spatial location (one of the other edges) | Different count           |

Here, "spatial location" refers to the group position within a choice box (restricted to the four edge positions: top, bottom, left, right). For each generated fruit trial, **all four edge locations are used exactly once**: the target group and the location-only foil share one location, and the remaining three roles (pattern-only, count-only, full distractor) each occupy one of the other three edge locations. "Pattern" refers to the white-on-color overlay (horizontal stripes, vertical stripes, checkered, or white dots).

**Spatial Arrangement Feature:**
- Fruit groups can be positioned at different locations within boxes (top, bottom, left, right, center)
- Per-fruit X/Y offset controls shift whole clusters independently along horizontal and vertical axes, yielding symmetric centering by default while enabling intentional spatial cues
- This adds spatial attention as an additional dimension

**Pattern Modes:**
- **Fixed Pattern**: The target uses the selected white-on-color overlay (horizontal stripes, vertical stripes, checkered, or white dots), and the four comparison choices are constructed according to the pattern/location/count/distractor rule above while sampling only from that fixed overlay for the target and alternative overlays for foils.
- **Full Random**: The target is assigned a single concrete overlay pattern drawn from the four-pattern pool, and the four comparison choices are again constructed according to the same four-role rule, with their overlays sampled from the same pool. This mode tests pattern discrimination and spatial attention alongside numerical attention and prevents color-driven numerosity biases observed in high-variety displays (Li et al., 2025).

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

This stimulus generator is designed to support a broad range of basic and applied investigations at the interface of numerical cognition, attention, and visual feature processing:

1. **SFON and Chan & Mazzocco–Style Attention-to-Number Tasks**
   - Implement picture-matching paradigms in which numerosity competes with object identity, colour, pattern, or spatial location as a basis for matching (Chan & Mazzocco, 2017).
   - Use structured foils (colour-only, shape-only, pattern-only, location-only, full distractors) to quantify spontaneous attention to number and competing-feature salience in children and adults (Mazzocco et al., 2020).

2. **Development of Numerical Cognition**
   - Test children at different ages to track subitizing development and approximate number processing.
   - Compare performance across age groups and educational contexts while holding visual structure constant.

3. **Individual Differences**
   - Examine whether some individuals show stronger number- versus feature-based attention, as reflected in systematic error patterns across foil types.
   - Correlate attention-to-number indices with other cognitive measures (e.g., working memory, arithmetic ability, domain-general executive functions).

4. **Perceptual Load and Feature-Salience Effects**
   - Manipulate visual complexity through pattern overlays, colour variety, and spatial groupings.
   - Study how increased perceptual load and feature heterogeneity affect numerical processing, including colour-driven biases and grouping effects (Li et al., 2018; Li et al., 2025; Ziegler et al., 2023).

5. **Cross-Cultural and Ecological Validity Studies**
   - Test whether numerical attention patterns are universal or culturally influenced across diverse samples.
   - Contrast abstract shape-based stimuli with more ecologically valid fruit-based stimuli to examine familiarity effects and generalisability of SFON-related findings.

6. **Clinical and Educational Applications**
   - Assess numerical cognition and attention to number in developmental disorders (e.g., dyscalculia, ADHD, autism spectrum disorder) relative to neurotypical controls.
   - Design targeted screening or intervention materials that manipulate competing-feature salience while preserving a clear numerical rule.

7. **Neuroimaging and Psychophysiological Research**
   - Use the images as stimulus material in fMRI, EEG, or other psychophysiological paradigms.
   - Identify neural correlates of numerical versus feature-based attention while maintaining precise control over spatial layout, numerosity, and feature competition (Gheorghiu & Dering, 2020; Pomè et al., 2020).

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

The experimental paradigm implemented here is intended as a configurable, picture-matching framework that makes the mapping rule explicitly numerical while preserving the ecological and attentional richness highlighted in the literature. Conceptually, it sits at the intersection of research on subitizing and approximate number processing (Anobile et al., 2016; Burr & Ross, 2008; Feigenson et al., 2004), on the guidance of visual attention by multiple competing attributes (Wolfe & Horowitz, 2004), and on spontaneous attention to number in SFON-style tasks (Chan & Mazzocco, 2017; Mazzocco et al., 2020).

Several design choices are motivated directly by these considerations:

1. **Feature Conflict and SFON**: By construction, exactly one comparison array matches the target in numerosity, whereas other arrays share only colour, only shape, only pattern, only spatial location, or differ on all controlled dimensions. This creates scenarios in which a visually salient non-numerical match competes with the numerically correct alternative, closely mirroring the “competing features” logic in picture-matching studies of attention to number (Chan & Mazzocco, 2017). Error patterns thus provide a window into which features participants prioritise when numerical and non-numerical similarity are dissociated.

2. **Unique Foils and Diagnosticity**: Ensuring that all comparison choices have unique counts, and that the correct answer is the only option matching the target numerosity, reduces ambiguity in both participant experience and data interpretation. When a non-numerical foil is chosen, the associated role (e.g., colour-only, pattern-only, or location-only) can be interpreted as an index of feature-driven attention rather than as a by-product of poorly discriminated numerical differences.

3. **Controlled Spatial Arrangements**: Systematic manipulation of spatial layout—including cluster position within each box and grid-like arrangements of items—prevents participants from relying on trivial positional cues while enabling targeted tests of grouping, segmentation, and attention allocation (Gheorghiu & Goldschmitt, 2022; Li et al., 2018; Ziegler et al., 2023). In the fruit-based condition, the constraint that all four edge locations (top, bottom, left, right) are used exactly once per trial enforces a clean spatial counterbalancing that is rarely achievable in hand-crafted stimuli.

4. **Pattern and Texture Variation**: Overlay patterns increase visual complexity without changing object identity, permitting manipulation of perceptual load and texture-based salience while holding numerosity constant. This supports investigations into how additional feature variation (e.g., colour and pattern heterogeneity) influences perceived numerosity and enumeration strategies (Li et al., 2018, 2025).

Collectively, these features are intended to make the generated image sets suitable for both basic and applied work: from testing theoretical claims about the status of numerosity as a perceptual attribute, to evaluating individual differences in SFON, to designing translational tasks for educational or clinical contexts. Because the generator exposes all task parameters transparently and produces exportable images, it can be integrated into diverse methodological pipelines (behavioural, neuroimaging, or cross-cultural) while maintaining strong control over the visual and numerical properties that drive performance.

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

For questions, suggestions, or collaboration opportunities, please open an issue on the GitHub repository or email me at

---

**Note**: This tool generates stimulus materials for research purposes. Researchers are responsible for obtaining appropriate ethical approval and informed consent for their studies.
