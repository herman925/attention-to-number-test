# Attention to Number Test Generator

A web-based cognitive assessment tool for investigating the interplay between numerical attention (subitizing) and visual feature processing in human perception.

## Overview

This application generates standardized visual tests designed to explore how humans attend to numerical quantities versus visual features (shape, color, pattern) when processing sets of objects. The tool is particularly useful for researchers studying numerical cognition, subitizing, visual attention, and perceptual decision-making.

## Academic Background

### Subitizing and Numerical Cognition

Subitizing refers to the rapid, accurate, and confident enumeration of small quantities (typically 1-4 items) without conscious counting. This cognitive phenomenon has been extensively studied in cognitive psychology and neuroscience as a fundamental aspect of numerical cognition.

**Key Research Areas:**
- **Numerical vs. Feature Attention**: Research has shown that numerical quantity can be processed as a primary perceptual feature, similar to color or shape (Burr & Ross, 2008; Anobile et al., 2016)
- **Subitizing Range**: The classical subitizing range is typically limited to 3-4 items, after which enumeration becomes slower and less accurate (Kaufman et al., 1949)
- **Parallel Processing**: Subitizing is believed to involve parallel processing mechanisms in the visual system, distinguishing it from serial counting
- **Cross-Modal Integration**: Numerical processing interacts with other visual features, providing insights into multidimensional perceptual integration

### Theoretical Framework

This test generator is designed to investigate two primary cognitive mechanisms:

1. **Quantity Discrimination**: The ability to rapidly distinguish between different numerosities
2. **Feature Integration**: How numerical information competes with or integrates with other visual features (shape, color, pattern)

The experimental paradigm creates a controlled environment where:
- **Target stimuli** are defined by multiple visual dimensions (shape/fruit type, color, pattern, and quantity)
- **Choice stimuli** systematically vary specific dimensions while keeping others constant
- **Correct responses** require attending to numerical quantity while potentially ignoring salient visual features

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
- **Target Pattern**: Solid, striped, dotted, or grid
- **Target Count**: 2-6 objects

**Choice Generation Rules:**
- **Correct choice**: Same count as target, different shape and color
- **Foil choices**: Different counts, varied shapes and colors
- All counts across choices are unique
- All colors across choices are unique

**Cognitive Focus**: This condition tests whether participants can focus on numerical quantity while ignoring shape identity and color—features that are typically more salient in visual processing.

#### 2. Fruit-Based Tests
Tests using fruit imagery to examine ecological validity and pattern processing.

**Target Parameters:**
- **Target Fruit**: Apple, pear, orange, banana, or cherry
- **Target Pattern**: Solid, striped, dotted, grid, or "Full Random"
- **Target Count**: 2-6 objects

**Choice Generation Rules:**
- **Correct choice**: Same count as target, different fruit type
- **Foil choices**: Different counts, all different fruit types
- Each choice uses a unique fruit type
- All counts across choices are unique

**Spatial Arrangement Feature:**
- Fruit groups can be positioned at different locations within boxes (top, bottom, left, right, center)
- This adds spatial attention as an additional dimension

**Pattern Modes:**
- **Fixed Pattern**: All stimuli use the same pattern (solid, striped, dotted, or grid)
- **Full Random**: Each choice box uses a different pattern from a pool of all four patterns, testing pattern discrimination alongside numerical attention

**Cognitive Focus**: Fruit stimuli provide more ecologically valid, real-world objects, allowing investigation of whether numerical processing differs for familiar vs. abstract objects.

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
   - **Pattern Selection**: Solid, striped, dotted, grid, or full random

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
   - New test is created with randomized correct answer position
   - Console logs indicate correct answer number

4. **Export for Study**
   - Click "Download as PNG" to save the test image
   - Use images in your experimental software or print for paper-based testing
   - Organize files by timestamp

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

This tool is suitable for investigating:

1. **Development of Numerical Cognition**
   - Test children at different ages to track subitizing development
   - Compare performance across different age groups

2. **Individual Differences**
   - Examine whether some individuals have stronger number vs. feature attention
   - Correlate with other cognitive measures (working memory, math ability)

3. **Perceptual Load Effects**
   - Manipulate visual complexity through pattern variations
   - Study how increased perceptual load affects numerical processing

4. **Cross-Cultural Studies**
   - Test whether numerical attention patterns are universal or culturally influenced
   - Use shape vs. fruit conditions to examine familiarity effects

5. **Clinical Populations**
   - Assess numerical cognition in dyscalculia, ADHD, autism spectrum disorder
   - Compare numerical attention patterns to neurotypical controls

6. **Neuroimaging Research**
   - Use as stimulus material in fMRI or EEG studies
   - Identify neural correlates of numerical vs. feature attention

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

3. **Varied Arrangements**: Spatial arrangement variations prevent participants from using position or configuration as a cue (must truly enumerate)

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

## References and Further Reading

### Key Papers on Subitizing:
- Kaufman, E. L., Lord, M. W., Reese, T. W., & Volkmann, J. (1949). The discrimination of visual number. *American Journal of Psychology, 62*(4), 498-525.
- Trick, L. M., & Pylyshyn, Z. W. (1994). Why are small and large numbers enumerated differently? A limited-capacity preattentive stage in vision. *Psychological Review, 101*(1), 80-102.

### Numerical Cognition:
- Dehaene, S. (2011). *The Number Sense: How the Mind Creates Mathematics*. Oxford University Press.
- Feigenson, L., Dehaene, S., & Spelke, E. (2004). Core systems of number. *Trends in Cognitive Sciences, 8*(7), 307-314.

### Numerosity as a Perceptual Feature:
- Burr, D., & Ross, J. (2008). A visual sense of number. *Current Biology, 18*(6), 425-428.
- Anobile, G., Cicchini, G. M., & Burr, D. C. (2016). Number as a primary perceptual attribute: A review. *Perception, 45*(1-2), 5-31.

### Visual Attention and Features:
- Treisman, A. M., & Gelade, G. (1980). A feature-integration theory of attention. *Cognitive Psychology, 12*(1), 97-136.
- Wolfe, J. M., & Horowitz, T. S. (2004). What attributes guide the deployment of visual attention and how do they do it? *Nature Reviews Neuroscience, 5*(6), 495-501.

## Citation

If you use this tool in your research, please cite:

```
Attention to Number Test Generator [Computer software]. (2024). 
Retrieved from https://github.com/herman925/attention-to-number-test
```

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
