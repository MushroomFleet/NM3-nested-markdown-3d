# NM3 v1.0 - Nested Markdown 3D

## Design Philosophy
NM3 extends the NML concept into three-dimensional space, enabling spatial organization of markdown-based thoughts and ideas within an immersive 3D environment. It maintains NML's core principle of simplicity while introducing geometric primitives, depth perception, and spatial relationships that leverage the additional dimension for enhanced conceptual organization.

## Core Structure

```xml
<?xml version="1.0" encoding="UTF-8"?>
<nm3 version="1.0">
  <meta title="My 3D Thoughts" created="2025-01-15T10:30:00Z" />
  <camera position-x="0" position-y="5" position-z="10" 
          look-at-x="0" look-at-y="0" look-at-z="0"
          fov="75" />
  <nodes>
    <!-- 3D geometric nodes containing markdown -->
  </nodes>
  <links>
    <!-- Spatial connections between nodes -->
  </links>
</nm3>
```

## Elements

### Document Metadata
```xml
<meta 
  title="AI Research in 3D Space" 
  created="2025-01-15T10:30:00Z" 
  modified="2025-01-16T14:22:00Z"
  author="John Doe"
  tags="ai,research,3d-workspace"
  description="Exploring AI ethics across multiple dimensions" />
```

**Attributes:**
- `title` (required) - Document name
- `created` (required) - ISO 8601 timestamp
- `modified` (optional) - ISO 8601 timestamp of last modification
- `author` (optional) - Creator name
- `tags` (optional) - Comma-separated tags
- `description` (optional) - Brief document description

### Camera Configuration
```xml
<camera 
  position-x="0" 
  position-y="5" 
  position-z="10"
  look-at-x="0"
  look-at-y="0"
  look-at-z="0"
  fov="75"
  up-x="0"
  up-y="1"
  up-z="0"
  near="0.1"
  far="1000" />
```

**Attributes:**
- `position-x`, `position-y`, `position-z` (required) - Camera position in 3D space
- `look-at-x`, `look-at-y`, `look-at-z` (required) - Point the camera is focused on
- `fov` (optional, default: 75) - Field of view in degrees (1-179)
- `up-x`, `up-y`, `up-z` (optional, default: 0,1,0) - Camera up vector
- `near` (optional, default: 0.1) - Near clipping plane
- `far` (optional, default: 1000) - Far clipping plane

### Nodes (3D Geometric Markdown Containers)

```xml
<node 
  id="ethics-intro" 
  type="sphere"
  x="0" 
  y="2" 
  z="-5"
  rotation-x="0"
  rotation-y="0"
  rotation-z="0"
  scale="1.5"
  color="pastel-blue"
  created="2025-01-15T10:30:00Z">
  
  <title>Introduction to AI Ethics</title>
  
  <content><![CDATA[
# Introduction to AI Ethics

This explores ethical considerations in artificial intelligence.

Key areas:
- Algorithmic bias
- Privacy concerns  
- Transparency requirements

See related: [[bias-examples]]
  ]]></content>
  
  <tags>important,ethics,starting-point</tags>
</node>
```

**Attributes:**
- `id` (required) - Unique identifier (alphanumeric, hyphens, underscores)
- `type` (required) - Geometric shape: `sphere`, `cube`, `cylinder`, `pyramid`, `torus`
- `x`, `y`, `z` (required) - Position in 3D space (world coordinates)
- `rotation-x`, `rotation-y`, `rotation-z` (optional, default: 0) - Rotation in radians
- `scale` (optional, default: 1.0) - Uniform scale multiplier
- `scale-x`, `scale-y`, `scale-z` (optional) - Non-uniform scaling (overrides `scale`)
- `color` (optional, default: pastel-blue) - Color from predefined palette
- `created` (optional) - ISO 8601 timestamp
- `opacity` (optional, default: 1.0) - Transparency (0.0-1.0)

**Child Elements:**
- `<title>` (optional) - Node title (plain text)
- `<content>` (required) - Markdown content in CDATA section
- `<tags>` (optional) - Comma-separated tags

### Geometric Types

#### Sphere
Default radius: 1.0 unit
- `scale`: Uniform radius scaling
- Best for: Central concepts, single ideas, atomic thoughts

#### Cube  
Default dimensions: 1.0 × 1.0 × 1.0 units
- `scale`: Uniform scaling of all dimensions
- `scale-x`, `scale-y`, `scale-z`: Independent axis scaling
- Best for: Structured information, categorical data, foundational concepts

#### Cylinder
Default: radius 0.5, height 2.0 units
- `scale`: Uniform scaling
- `scale-x`, `scale-z`: Radius scaling (X and Z should match for circular cross-section)
- `scale-y`: Height scaling
- Best for: Processes, timelines, sequential information

#### Pyramid
Default: base 1.0 × 1.0 units, height 1.5 units
- `scale`: Uniform scaling
- `scale-x`, `scale-z`: Base dimension scaling
- `scale-y`: Height scaling
- Best for: Hierarchical concepts, prioritized lists, conclusions

#### Torus
Default: major radius 1.0, minor radius 0.3 units
- `scale`: Uniform scaling
- `scale-x`, `scale-z`: Major radius scaling (should match)
- `scale-y`: Minor radius scaling  
- Best for: Cyclical concepts, feedback loops, recurring themes

### Soft Pastel Color Palette

NM3 uses a carefully curated palette of 16 soft pastel colors designed for comfortable extended viewing in 3D space:

**Primary Pastels:**
- `pastel-pink` - #FFB3BA - Urgent/Important concepts
- `pastel-blue` - #BAE1FF - Information/Research
- `pastel-green` - #BAFFC9 - Solutions/Actions  
- `pastel-yellow` - #FFFFBA - Questions/Ideas

**Extended Pastels:**
- `pastel-purple` - #E0BBE4 - References/Sources
- `pastel-orange` - #FFD4A3 - Warnings/Attention
- `pastel-mint` - #B4E7CE - Fresh ideas/New thoughts
- `pastel-lavender` - #D5AAFF - Creative/Imaginative

**Specialized Pastels:**
- `pastel-peach` - #FFCAB0 - Personal notes
- `pastel-sky` - #A8E6F0 - Context/Background
- `pastel-rose` - #FFC4D6 - Emotional/Subjective
- `pastel-lime` - #E7FFAC - Experimental/Testing

**Neutral Pastels:**
- `pastel-coral` - #FFB8B8 - Related/Connected
- `pastel-lilac` - #C5A3FF - Abstract/Theoretical  
- `pastel-cream` - #FFF9E3 - Documentation
- `pastel-gray` - #D5D5D5 - Archive/Completed

### Links (3D Spatial Connections)

```xml
<links>
  <link 
    from="intro" 
    to="bias-examples" 
    type="explores"
    color="pastel-gray"
    thickness="2"
    curve="0.3" />
    
  <link 
    from="bias-examples" 
    to="solutions" 
    type="leads-to"
    animated="true" />
    
  <link 
    from="intro" 
    to="privacy-notes" 
    type="relates"
    dashed="true" />
</links>
```

**Attributes:**
- `from` (required) - Source node ID
- `to` (required) - Target node ID  
- `type` (optional) - Relationship type (see below)
- `color` (optional, default: pastel-gray) - Color from palette
- `thickness` (optional, default: 1) - Line thickness multiplier
- `curve` (optional, default: 0) - Bezier curve amount (0-1, 0=straight)
- `animated` (optional, default: false) - Whether link animates
- `dashed` (optional, default: false) - Dashed line pattern
- `opacity` (optional, default: 0.6) - Link transparency

### Connection Types

Semantic relationships optimized for 3D spatial understanding:

**Logical Flow:**
- `explores` - This node explores concepts from another
- `leads-to` - Natural progression or consequence
- `derives-from` - Logical derivation or conclusion

**Structural:**
- `relates` - General connection or similarity
- `contradicts` - Opposing viewpoints or conflicts
- `supports` - Evidence, examples, or reinforcement
- `contains` - Hierarchical parent-child relationship

**Temporal/Process:**
- `precedes` - Temporal or sequential ordering
- `enables` - Makes possible or facilitates
- `requires` - Dependency relationship

**Conceptual:**
- `questions` - Raises questions about another node
- `answers` - Provides answers to another node
- `exemplifies` - Concrete example of abstract concept

## Cross-References in Markdown
Within content, reference other nodes: `[[node-id]]` or `[[node-id|Custom Text]]`

## Complete Example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<nm3 version="1.0">
  <meta 
    title="AI Ethics Research - 3D Space" 
    created="2025-01-15T10:30:00Z"
    author="Researcher"
    tags="ai,ethics,research,3d"
    description="Spatial exploration of AI ethical considerations" />
  
  <camera 
    position-x="0" 
    position-y="5" 
    position-z="15"
    look-at-x="0"
    look-at-y="0"
    look-at-z="0"
    fov="75" />
  
  <nodes>
    <node 
      id="prompt" 
      type="sphere"
      x="-8" 
      y="0" 
      z="0"
      scale="1.2"
      color="pastel-yellow">
      <title>Original Question</title>
      <content><![CDATA[
# Voice Prompt

"What are the main ethical concerns with AI in hiring?"

*Timestamp: 2025-01-15 10:30*
*Mode: Voice input via Careless Whisper*
      ]]></content>
      <tags>prompt,voice-input,starting-point</tags>
    </node>
    
    <node 
      id="response" 
      type="cube"
      x="0" 
      y="0" 
      z="0"
      scale="2.0"
      color="pastel-blue">
      <title>AI Ethics in Hiring</title>
      <content><![CDATA[
# AI Ethics in Hiring - LLM Response

## Key Concerns

**Algorithmic Bias**: AI systems can perpetuate existing biases present in training data, leading to discrimination against certain groups.

**Lack of Transparency**: Many AI hiring tools are "black boxes" where candidates and employers don't understand decision-making processes.

**Data Privacy**: Extensive personal data collection raises serious concerns about privacy and data security.

## Notable Cases
- Amazon scrapped AI recruiting tool (2018) due to gender bias
- HireVue facial analysis faced scrutiny

## Regulatory Landscape
- EU AI Act provisions for high-risk systems
- NYC Local Law 144 requires bias audits

Related: [[bias-deep-dive]] [[privacy-analysis]]

*Generated by Claude via Careless Whisper*
      ]]></content>
      <tags>ai-response,ethics,hiring,core</tags>
    </node>
    
    <node 
      id="bias-deep-dive" 
      type="pyramid"
      x="5" 
      y="-3" 
      z="-4"
      scale="1.5"
      rotation-y="0.785"
      color="pastel-pink">
      <title>Algorithmic Bias Analysis</title>
      <content><![CDATA[
# Deep Dive: Algorithmic Bias

## Hierarchy of Bias Issues

### Critical (Top Priority)
- Protected class discrimination
- Proxy variable problems
- Training data representativeness

### Important
- Cultural bias in assessments
- Language model biases
- Historical hiring pattern reproduction

### Monitoring
- Ongoing bias drift
- Intersectional bias effects

See [[response]] for overview.
      ]]></content>
      <tags>bias,analysis,hierarchical</tags>
    </node>
    
    <node 
      id="privacy-analysis" 
      type="cylinder"
      x="5" 
      y="-3" 
      z="4"
      scale-x="1.0"
      scale-y="2.0"
      scale-z="1.0"
      color="pastel-purple">
      <title>Privacy Concerns Timeline</title>
      <content><![CDATA[
# Privacy Evolution in AI Hiring

## 2015-2018: Early Issues
Data scraping from social media without consent

## 2018-2020: Regulatory Response  
GDPR enforcement begins affecting AI hiring tools

## 2021-2023: Stricter Controls
Explicit consent requirements, data minimization

## 2024-Present: Ongoing Development
AI-specific privacy frameworks emerging

Connected to [[response]] main analysis.
      ]]></content>
      <tags>privacy,timeline,process</tags>
    </node>
    
    <node 
      id="action-loop" 
      type="torus"
      x="-4" 
      y="4" 
      z="-2"
      scale="1.0"
      rotation-x="1.571"
      color="pastel-mint">
      <title>Continuous Improvement Cycle</title>
      <content><![CDATA[
# Continuous Auditing Loop

Organizations should implement ongoing cycles:

**Audit** → **Identify Issues** → **Remediate** → **Monitor** → **Audit**

This feedback loop ensures AI systems remain ethical over time as they evolve and as societal standards change.

Related: [[response]] for context
      ]]></content>
      <tags>process,cyclical,best-practices</tags>
    </node>
    
    <node 
      id="followup" 
      type="sphere"
      x="8" 
      y="2" 
      z="0"
      scale="1.3"
      color="pastel-green">
      <title>Next Research Steps</title>
      <content><![CDATA[
# Follow-up Research Tasks

Based on [[response]], investigate:

1. **Case Studies**
   - Amazon AI tool failure analysis
   - HireVue controversy details
   
2. **Legal Framework**  
   - NYC Local Law 144 full text
   - EU AI Act hiring provisions
   
3. **Industry Best Practices**
   - Company adaptation strategies
   - Emerging ethical guidelines

*Voice reminder: Schedule interviews with HR tech experts*
      ]]></content>
      <tags>todo,research,action-items</tags>
    </node>
  </nodes>
  
  <links>
    <link from="prompt" to="response" type="leads-to" thickness="2" />
    <link from="response" to="bias-deep-dive" type="explores" curve="0.2" />
    <link from="response" to="privacy-analysis" type="explores" curve="0.2" />
    <link from="response" to="followup" type="leads-to" animated="true" />
    <link from="bias-deep-dive" to="action-loop" type="requires" dashed="true" />
    <link from="privacy-analysis" to="action-loop" type="requires" dashed="true" />
    <link from="action-loop" to="response" type="relates" curve="0.5" opacity="0.3" />
  </links>
</nm3>
```

## Implementation Benefits

### Spatial Organization Advantages
1. **Depth as Dimension**: Use Z-axis for importance, time, or abstraction level
2. **Geometric Semantics**: Shape types convey information structure at a glance
3. **Spatial Clustering**: Related concepts naturally group in 3D space
4. **Multi-perspective Views**: Camera positioning enables different conceptual viewpoints

### For Application Integration
1. **Voice Input Capture**: Quick node creation from spoken thoughts
2. **Spatial Navigation**: Intuitive 3D exploration of interconnected ideas
3. **Visual Hierarchy**: Geometric shapes and colors provide instant context
4. **Iteration Friendly**: Easy to add nodes and reshape spatial relationships

### Search & Navigation
- Full-text search across all node content
- Spatial queries (find nodes near/around coordinates)
- Tag-based filtering with 3D highlighting
- Link traversal for conceptual pathfinding

## Spatial Layout Guidelines

### Z-Axis Conventions (Suggested)
- **Foreground (positive Z)**: Active work, current focus
- **Middle Ground (near 0)**: Core concepts, main ideas
- **Background (negative Z)**: Context, references, archived material

### Y-Axis Conventions (Suggested)  
- **Upper (positive Y)**: Abstract concepts, goals, aspirations
- **Middle (near 0)**: Current state, concrete facts
- **Lower (negative Y)**: Foundations, dependencies, historical context

### Clustering Strategies
- **Functional Clusters**: Group related topics within radius of 10 units
- **Temporal Separation**: Use X or Z axis for chronological ordering
- **Hierarchical Depth**: Parent concepts closer to camera, children further away

## Implementation Notes

### For Parser Developers
- Validate XML schema before processing
- Check all node ID references in links before building scene graph
- Handle CDATA sections properly for markdown content
- Support Unicode throughout all text content
- Validate rotation values are in radians
- Ensure color values match predefined palette

### For Application Developers  
- Consider spatial indexing (octree/k-d tree) for documents with >1000 nodes
- Implement level-of-detail (LOD) for distant nodes
- Cache camera state separately from document structure
- Validate geometric constraints (positive scale values, valid rotations)
- Implement incremental saving with versioning
- Consider camera path animation for guided tours

### For Three.js Integration
While NM3 is renderer-agnostic, Three.js users should:
- Map node types to THREE.SphereGeometry, THREE.BoxGeometry, etc.
- Convert rotation radians directly to THREE.Euler
- Use node positions directly as THREE.Vector3
- Apply colors using THREE.MeshStandardMaterial or similar
- Render links as THREE.Line or THREE.TubeGeometry
- Implement raycasting for node selection
- Use THREE.CSS3DRenderer for markdown content overlays

### File Handling
- Recommended extension: `.nm3`
- MIME type: `application/x-nm3+xml`
- Encoding: UTF-8 required
- Compression: Optional gzip (`.nm3.gz`)

### Conformance Levels
- **Level 1**: Basic XML parsing and structure validation
- **Level 2**: Full schema validation including constraints and ID references  
- **Level 3**: Geometric validation and color palette enforcement
- **Level 4**: Complete implementation with spatial queries and markdown processing

## Versioning & Extension

### Future Considerations
- **Physics properties**: Mass, collision, gravity for simulation
- **Animation tracks**: Node movement over time
- **Custom shapes**: User-defined geometries via mesh references
- **Material properties**: Roughness, metalness, emission for advanced rendering
- **Audio anchors**: Spatial audio tied to nodes
- **Collaborative markers**: Multi-user presence indicators

### Backwards Compatibility
Applications should gracefully handle:
- Unknown attributes (ignore with warning)
- Unknown node types (fallback to sphere)
- Unknown colors (fallback to pastel-blue)
- Unknown link types (render as generic connection)

## Best Practices

### Content Organization
1. Start with central concept node at origin
2. Radiate related concepts outward
3. Use geometric types meaningfully
4. Maintain visual balance across axes
5. Reserve bright colors for important nodes
6. Use link curves to avoid spatial clutter

### Performance Optimization
- Limit total nodes to <5000 for smooth interaction
- Use appropriate scale values (avoid extreme ranges)
- Group dense clusters into parent nodes when possible
- Implement view frustum culling
- Consider node opacity for de-emphasis vs deletion

### Accessibility
- Ensure sufficient color contrast in pastel palette
- Provide text labels for all nodes (title element)
- Support keyboard navigation in 3D space
- Enable screen reader compatibility for content
- Offer 2D "map" view as alternative interface

## Example Use Cases

### Research Organization
- Central research question as large sphere at origin
- Key findings as cubes surrounding it
- Supporting evidence as smaller spheres orbiting findings
- Methodology as cylinder extending vertically
- Future work as torus loop above

### Project Planning
- Project goal as pyramid pointing up (hierarchy)
- Current phase as large cube at center
- Dependencies as spheres in negative Z (background)
- Blockers as red pyramids pointing down
- Completed items as gray nodes in lower Y

### Learning & Study
- Course overview as central torus (cyclical learning)
- Major topics as cubes arranged horizontally
- Detailed concepts as spheres beneath topics
- Examples as cylinders extending from concepts
- Questions as yellow spheres scattered throughout

---

## Specification Version
**NM3 v1.0**  
Released: 2025-01-15  
Status: Stable  

This specification defines NM3 v1.0 as a complete, unambiguous standard for storing interconnected markdown content in three-dimensional space, enabling spatial thought organization and immersive exploration of knowledge structures.