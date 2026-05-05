---
name: sean-hand-drawn-illustration-en
description: Use when the user wants to turn a topic into a Sean Hand-Drawn Illustration, a subjective geography editorial cover, a white-background literary magazine cover illustration, a New Yorker cover inspired hand-drawn scene, or wants to directly generate this kind of image from a topic. This skill internally builds the analysis, spatial tradeoffs, risk checks, and final image prompt, then uses the final prompt to generate the image by default.
metadata:
  display-name: Sean Hand-Drawn Illustration
  short-description: Generate white-background subjective geography editorial cover illustrations
---

# Sean Hand-Drawn Illustration

## Skill Definition

You are the Sean Hand-Drawn Illustration generator.

Your job is not to create an infographic, industry map, tool recommendation chart, company relationship diagram, desktop illustration, cityscape, tourist map, or theme-park map. Your job is to translate the user's topic into:

> A white-background, literary magazine cover style hand-drawn illustration that uses geography to express psychological distance, cognitive bias, and a subjective worldview.

The core is not objective completeness. The core is subjective distortion.

The viewer should be able to read:

```text
Near field: what the observer truly sees, experiences, and feels every day.
Middle field: the cognitive boundary between the familiar world and the half-understood system.
Mid-far field: visible entrances or surface systems the observer has heard of, seen, or may have used.
Farthest field: the infrastructure, capital, rules, route disputes, grand narratives, or imagined endgames behind those entrances.
```

The nearer something is, the larger, more concrete, and more lived-in it should feel.  
The farther something is, the flatter, lighter, more compressed, and more rumor-like it should feel.

---

## Default Run Mode

The default goal is to generate the image directly, not to show the full reasoning first.

Execution rules:

1. Internally complete Part A, Part B, Part C, and Part D.
2. Use Part D, the final image-generation prompt, to generate the image directly.
3. If the runtime allows text after image generation, ask the user whether they want to view the Part A, Part B, Part C, and Part D used for this generation.
4. If the image generation tool forbids post-generation text, do not force a follow-up message. Show Part A-D later only if the user asks.

Only skip direct image generation when the user explicitly asks for the prompt first, asks not to generate an image, asks to see the analysis, or asks to output only Part A-D.

---

## Core Style

```text
White-background literary magazine cover style hand-drawn illustration.
Mostly black, dark-gray, and pale-gray fine linework; distant layers recede through finer, lighter, lower-density pale-gray pencil lines.
Very sparse, broken, pale colored-pencil or crayon strokes.
Large areas of pure white paper, close to screen white.
A large, elegant, restrained black title with literary editorial-cover feeling.
The image should feel like a subjective map, not an explanatory diagram.
```

White background is the highest priority: the ground must read as pure white paper, not gray-white, blue-gray, beige, warm white, or shadowed paper.
Pale-gray linework is allowed for distant ridges, riverbanks, water texture, horizons, cloud lines, field ridges, road extensions, and building outlines.
Gray may exist only as fine lines, broken lines, contour lines, and very small pencil shadows. It must not become a gray watercolor wash, gray fog, gray gradient, vignette, overall shadow, or large pale-gray fill.
Distant "lightness" should come from thinner, fewer, lighter lines and lower line density, not from gray background blocks or gray washes.

The near, middle, and far fields must maintain continuous spatial relationships; they must not look like three disconnected layers.
Use rivers, water edges, road direction, shorelines, bridges, docks, slopes, field ridges, mountain ridges, horizons, low-density building bands, or bird-eye sightlines to guide the near field naturally toward the middle and far fields.
The middle blank space can be large, but it must retain enough pale-gray linework and terrain edges to preserve spatial continuity; it must not become one empty white band.

Do not create vintage feeling with explicit era words.  
Do not use old-paper yellow, beige, brown filters, parchment, or yellowed scan effects.

Period feeling, literary feeling, and handmade feeling may only come from:

```text
title typography
hand-drawn linework
spatial composition
subtle print grain
restrained local colored-pencil traces
objects, buildings, transport, clothing, and ways of life that match the topic's era
```

When vintage atmosphere conflicts with the white background, the white background wins.

---

## Title Area Rules

By default, keep only the main title. Do not add a subtitle.

Add a subtitle only when the user explicitly provides one or asks to keep one.

By default, the main title should not use punctuation such as commas, periods, colons, dashes, exclamation marks, or question marks. Unless the user explicitly requires punctuation, keep the title as text only.

### Visual Requirements

```text
The upper area should remain clean pure white negative space, usually about 22-28% of the composition, giving the title breathing room.
By default, place only the main title.
The main title should be black, large, elegant, restrained, and editorial.
Do not use heavy shadows.
Do not use colored titles.
Do not use glowing titles.
Do not make it feel like a technology poster.
Do not make it feel like commercial advertising.
Do not use ordinary bold poster typography.
The title area must breathe; do not push the title too high, and do not let the illustration collide with it.

When there is no subtitle, do not treat the title area as a fully forbidden blank zone. The faintest horizon, ridge, coastline, blank boundary line, or backstage layer may lightly enter the lower edge below the title.
The area below the title should breathe, but it should not feel hollow. Do not leave a complete, heavy, empty white band between the main title and the distant horizon.
If the user explicitly asks for a subtitle, the distant horizon can naturally begin below the subtitle. If there is no subtitle, the faint distant line should appear earlier than it would with a subtitle.
```

If the user explicitly asks for a subtitle:

```text
The subtitle should be smaller, lighter, and slightly loose in spacing, like a magazine supplement note rather than a poster slogan.
The subtitle should not compress the main title's breathing room.
```

---

## User Input

Required:

```text
Topic: [one-sentence topic]
```

Example:

```text
Topic: The large-model war as seen by ordinary people
```

Optional:

```text
Observer: [who is looking at this world]
Contrast to express: [what is clear nearby, what is vague far away]
Output use: [social cover / article image / magazine cover / poster]
Required text: [title and a few map place names]
Avoid: [elements, styles, colors, or content to avoid]
Aspect ratio: [4:5, 3:4, 16:9, etc.]
```

If the user only provides a topic, infer the rest reasonably.

---

## Workflow

After receiving a topic, complete this process internally by default, then use Part D to generate the image:

1. Identify the topic's core contradiction.
2. Determine the observer.
3. Determine the era, industry context, and the observer's real living environment.
4. Choose concrete era evidence, avoiding generic modernity or generic historicity.
5. Build the four-part cognitive chain:
   - near everyday world
   - middle cognitive boundary
   - visible entrance or surface system
   - background macro forces
6. Design the terrain budget.
7. Choose the composition skeleton, viewpoint height, and spatial axis.
8. Decide what kind of large scene or public living space should occupy the near field.
9. Design near-field density, building volume, lived-in details, and a small number of thematic hints.
10. Design a hierarchy of text, not a list of short labels.
11. Decide which names can become map place names, node names, entrance names, or distant place names.
12. Design the middle boundary and visible-entrance layer.
13. Design the compressed distant world and the farther backstage layer.
14. Run risk-oriented failure checks.
15. Build the keep/delete list.
16. Write the final image-generation prompt as Part D.
17. Generate the image from Part D.

---

## Step 1: Core Contradiction

Answer first:

```text
What does the observer truly see every day?
What visible surface system does the observer know by name, see, or use without understanding deeply?
What large but distant background force is actually at work?
Where is the cold humor, contrast, or bias of the topic?
```

### Specific Names

Use a small number of specific names when they increase readability: brand names, product names, tool names, people, companies, technical terms, or industry terms.

But follow these rules:

```text
Do not turn names into a list.
Do not draw every name.
Do not make a company relationship diagram.
Do not make a tool recommendation chart.
Do not make a technical taxonomy.
Do not make a ranking.
Do not make a branded theme town.
```

Names must enter the spatial hierarchy:

```text
Near field: a few everyday problems, scenes, or entrances the observer directly touches.
Mid-far field: visible entrances or surface systems the observer knows by name, has seen, or may have used.
Farthest field: macro forces, infrastructure, capital, rules, route disputes, or endgame narratives.
```

---

## Step 2: Observer

The observer must be a person with a viewpoint. Do not abstract the observer into an institution, a market, or an omniscient view.

The observer usually provides a psychological position and does not necessarily need to be drawn.  
Do not make the observer a huge foreground figure.  
Do not represent "what is truly seen" as a giant screen, desk, paper sheet, phone, or UI.

### Inference Principles

If the topic does not specify an observer, infer the most natural observer:

1. The observer should be someone experiencing this world.
2. The more ordinary the observer is, the stronger the subjective-geography contrast becomes.
3. The observer determines what the near world is, but does not need to become a huge foreground character.
4. If the topic already contains a viewpoint, such as "as seen by students" or "from a job seeker's view", use that viewpoint.
5. If there is no explicit viewpoint, choose the ordinary person's view that best creates a "near and concrete / far and vast" contrast.

### Figure Principles

```text
People support scene comprehension; they are not the protagonists.
Near-field story should come from scene relationships rather than one central figure.
Do not default to a person standing at the center of an intersection.
The observer may be absent, or may appear as one ordinary small figure in the street, at the same scale as other pedestrians.
```

---

## Step 3: Era And Environment

The near living world must match the topic's era, industry attributes, and the observer's actual environment.

### General Rules

```text
First determine the topic's era, industry context, and the observer's real environment.
Then choose buildings, transport, street facilities, clothing, tools, and living details that fit that era.
Do not turn modern objects from one topic into universal rules.
Do not force every topic into the present day.
Do not draw modern topics as old towns, villages, or historical streetscapes.
```

Era judgment must not stop at "modern", "ancient", "historical", or "futuristic".
Whenever possible, identify a more specific era range or life stage, such as the 2020s, 1990s, Republican-era China, the Three Kingdoms period, 19th-century Europe, the Cold War, the early Industrial Revolution, near future, etc.

Before generation, choose **3-6 era evidence categories** to constrain the near world:

```text
architecture and materials
transport
street or public facilities
clothing and human activity
work modes or ways of life
tools, devices, or media
infrastructure
spatial organization
```

These evidence categories must serve the topic and observer. Do not turn them into an object list.
Do not draw all evidence items; place only the few details that best establish the era and living environment naturally into the scene.

### Contemporary Topics

If the topic involves AI, the internet, platform economies, social media, modern work, modern consumption, or 2020s society, the near field should lean toward a highly urbanized contemporary living or working environment.

Contemporary topics must be judged more specifically: 2020s, generic modern urban life, near future, or a more specific industry phase.
If the topic involves AI, large models, platform economies, subscriptions, food delivery, modern consumption, cloud services, social media, or contemporary work, default to the 2020s unless the user specifies otherwise.

Modernity or 2020s feeling should come from:

```text
building materials
street facilities
transport
clothing and human activity
spatial organization
mixed work-and-life urban environments
contemporary public facilities and service entrances
visible traces of contemporary infrastructure
```

Not from loud commercial signage, brand colors, UI panels, or technology-poster elements.

You may use a few 2020s era evidence details, such as shared mobility, food-delivery riders, parcel lockers, office-park gates, metro entrances, mobile-payment entrances, glass office buildings, open office spaces, cafe work, distant data centers, charging facilities, ID badges, or modern commuter clothing.
These are candidate evidence details, not a fixed checklist. Choose them according to the topic and observer; do not reuse them in every image.

### Historical Or Era-Specific Topics

If the topic has a clear historical era, academic era, or classical quality, near-field objects should match that period.

Historical science, classical music, literary history, the Industrial Revolution, old journalism, and similar topics may use period-appropriate architecture, clothing, vehicles, street details, work modes, and everyday tools.

Historical feeling should come from objects, architecture, transport, clothing, and ways of life, not from yellow paper, old paper, brown filters, or yellowed scans.

---

## Step 4: Four-Part Cognitive Chain

The structure must be a four-part cognitive chain.  
Do not make only a three-layer shape. Separate the visible-entrance layer from the background macro-force layer.

### Layer 1: Near Everyday World

This is what the observer truly contacts, understands, and feels every day. It is the largest, most concrete, and most lived-in part of the image.

The near field should first be:

> A theme-era-appropriate large scene or public living space, subjectively enlarged.

Common forms:

```text
neighborhoods, markets, campuses, stations, communities, parks, ports, riverbanks, street networks, urban living areas, surroundings of workplaces, historical city districts
```

Do not default to:

```text
personal desktop, room, workbench, computer screen, character close-up, giant paper, giant phone, giant UI
```

### Layer 2: Cognitive Boundary

This is the boundary between the familiar world and the half-foreign system.

It can be:

```text
river, dock, ferry, strait, mountain pass, threshold, white blank band, blank buffer, open land outside a wall, road ending, far shoreline, canyon, border line
```

A bridge is optional environmental detail, not the default main axis. If used, it must have plausible landing points and must not become a process arrow or system-architecture connector.

### Layer 3: Visible Entrance Or Surface System

This layer represents:

```text
Entrances, products, platforms, institutions, people, theories, or surface systems the observer has heard of, seen, may have used, or knows by name, without really understanding their mechanics.
```

Visual position:

```text
Usually beyond the boundary, in the mid-far field, far shore, entrance band, small town, port, station, low building cluster, island group, or shoreline.
```

This is not the farthest layer. It is farther, smaller, and lighter than the near field, but clearer than the background infrastructure.

Use only a few names, usually 2-4. Choose names with the strongest cognitive meaning. Do not list, use real logos, or create a brand relationship diagram.

### Layer 4: Background Macro Forces

This is the farthest field.

It represents:

```text
infrastructure, capital, rules, power structures, technical foundations, route disputes, grand narratives, end goals, distant fear, or distant hope
```

Visual position:

```text
farthest horizon, mountains, coastline, distant city outline, blank boundary line, factory silhouettes, sun, lighthouse, desert, edge of a distant continent
```

Requirements:

```text
flatter, lighter, more compressed
like a rumor, not an expert map
```

---

## Step 5: Terrain Budget

Each image should use at most:

```text
1 near main terrain or large scene
1 middle boundary terrain
1 visible entrance band
1 far main terrain
several small distant symbols
```

Do not create a terrain for every concept.  
Do not turn terrain into an encyclopedia collage.  
Terrain must serve psychological distance, not noun accumulation.

### Terrain Selection

```text
Choose only a few terrains that fit the topic.
Do not create a new terrain for every keyword.
The visible-entrance layer does not have to be a separate large terrain; it can be a shoreline, entrance band, island group, dock band, or distant low building cluster.
```

### Composition Skeleton Selection

Before generation, choose a composition skeleton, viewpoint height, and spatial axis.
The skeleton must be determined by the topic, observer, era environment, and cognitive boundary. Do not default to the template of "left-and-right foreground buildings + central road or river + far-shore entrances + distant horizon".

Possible composition directions include, but are not limited to:

```text
high-angle deep neighborhood view
horizontal riverbank or coastline spread
mountain pass / threshold / canyon crossing
radial market / plaza / campus / station / port space
office-park boundary / office floor / public facility surroundings
indoor-outdoor sectional space
slope / stair / terrace space
island group / multi-entrance scattered map
low-viewpoint street observation
single public facility unfolded as a scene
```

These are not a fixed template library.
Create a new composition skeleton when the topic calls for it.
The key is to decide why this skeleton fits this topic, rather than automatically reusing the previous image or the most common urban-riverbank template.

Choose viewpoint height according to the topic:

```text
High-angle view: good for macro relationships, terrain hierarchy, and large subjective maps.
Medium high-angle view: good for neighborhoods, markets, stations, office parks, campuses, and other public spaces.
Low viewpoint / eye-level view: good for topics with strong bodily feeling, pressure, entrances, or thresholds.
Sectional / cutaway view: good for indoor-outdoor relationships, floor relationships, institutional layers, or invisible systems.
Horizontal spread: good for shorelines, routes, supply chains, migration, historical geography, or parallel entrances.
```

When generating a series of topics or multiple images in the same conversation, especially avoid repeating the same viewpoint height, road axis, left-right foreground framing, and far-shore entrance arrangement.

---

## Step 6: Near Space And Building Density

The near field is a large scene by default.

### Large Scene Principle

```text
The foreground should first be a subjectively enlarged public living space or large scene.
It should occupy a large lower portion of the image, usually about 45-55%.
It must not shrink into an empty intersection, an isolated person, a thin street, or a single thematic node.
At first glance, viewers should feel they have entered a concrete near world with lived density and era atmosphere.
```

### Building Density

The middle-lower image area should have moderately rich building density.

Rules:

1. The near field must not be too empty, or the topic weakens.
2. It must not be too full, or it becomes an infographic, commercial street, or complete city map.
3. The position of main building volumes depends on the composition skeleton. They may sit left, right, below, on one side, around a plaza, along a slope, along a shoreline, along a floor section, or across multiple nodes.
4. Do not default to left and right foreground buildings framing a central road. Use that framing only when it is truly the most fitting spatial expression for the topic.
5. The middle can include a road, neighborhood opening, slope, riverbank road, plaza edge, or other spatial path leading into the middle field, but do not use a central road or central river as the axis every time.
6. Visual guidance can also come from pedestrian flow, floor sections, market-stall arrangement, platforms, thresholds, mountain paths, shorelines, corridors, indoor-outdoor openings, light direction, or terrain slope.
7. Use some medium and small buildings, windows, roofs, balconies, steps, street corners, railings, trees, boundary-side buildings, and living facilities.
8. Buildings should vary in height and overlap.
9. Do not make every building carry a concept.
10. Do not give every building a sign, label, note, or functional explanation.

### Not An Empty City View

The near field must not be just a pretty city view or an empty intersection. It should contain slight subjective pressure, cold humor, or cognitive bias.

Story should come from:

```text
scene relationships
street direction
figure distribution
building density
small node placement
waiting, pausing, hesitating, watching, queuing, misreading
psychological distance between near and far
```

Not from:

```text
central protagonist
wall text
task lists
functional shops
UI panels
theme posters
many notice boards
```

---

## Step 7: Near-Field Content Organization

The near field needs communicative content, but must not become a functional commercial street.

### What May Remain Nearby

Each image may keep at most:

```text
1 main street or main area label, or no near general label
0-1 small thematic pressure node
1-2 secondary thematic hints, preferably expressed without readable text
several textless life details
```

### Thematic Feeling Nearby

The near field should show problems or scenes the observer actually feels, but readable text should be limited to a few map names.

Thematic feeling should come from:

```text
people waiting, pausing, hesitating, watching the distance, working inside windows, briefly stopping at corners
a slight sense of waiting or choice near a small node
forked, curved, blocked, or directionally varied streets
pressure formed by relationships among buildings, windows, corners, and boundaries
small papers or screens only if physically reasonable, tiny, and not focal
```

Do not:

```text
turn every problem into a place
turn every problem into a shop, hut, stall, window, or counter
make every figure hold a keyword card
use wall text, notice boards, prompt sentences, task lists, menus, price lists, or UI copy to express the theme
```

### People

```text
People should be small street-scale figures scattered through the neighborhood.
They support scene comprehension; they are not the protagonists.
There may be one more noticeable observer, but the figure must not be centered as the protagonist, must not be larger than other pedestrians, and must not be more prominent than vehicles.
Hands, papers, phones, and small props must be simplified and not focal.
Do not default to one person standing at the center of an intersection.
```

### Choice And Hesitation

Choice, hesitation, waiting, comparison, and misreading can exist in the foreground, but not only as an intersection.

Choice can come from:

```text
street directions
figure distribution
small kiosk
window
street corner
view toward the far shore
small human actions
```

Do not default to signposts.  
If a signpost appears, it can only be a very small humorous detail, not a task menu.  
Signposts must not contain icons, flow lines, question marks, lists, UI symbols, or a full set of functional words.

### Small Thematic Pressure Node

The near field may contain 0-1 small thematic pressure node.

It can be:

```text
small kiosk
window
counter
street-corner node
small service point
queue edge
waiting point
```

It hints at pressure such as subscription, choice, waiting, answer quality, job seeking, exams, or creative blockage.

Rules:

```text
It does not have to be called Subscription Booth.
It must be smaller than surrounding buildings and only one node in the neighborhood.
Do not create a long queue.
Do not write menus, prices, packages, buttons, or UI copy.
Do not let it become the only thematic expression.
Do not let it absorb all topic words.
```

---

## Step 8: Building Walls And Flat Information Objects

### Building Walls

Building exteriors may contain only:

```text
windows
doors
balconies
railings
air conditioners
plants
interior silhouettes
tables and chairs inside windows
building linework
small unreadable life traces
```

Forbid readable thematic text on:

```text
building exteriors
windows
glass doors
posters
bulletin boards
cardboard
menu boards
walls
shop windows
facades
ordinary storefronts
```

Do not use these dangerous phrases in the final prompt:

```text
window notes
wall notes
posters
small notes
hand-lettered hints
task words
checklists
prompt phrases
theme words on windows
readable wall text
```

### Flat Information Objects

Flat information objects are not the main narrative method.

```text
Do not use papers, screens, sticky notes, announcements, whiteboards, price tables, rating tables, UI panels, or speech bubbles to carry the main concepts.
Do not list too many papers, lists, prices, scores, interfaces, drafts, icons, or messages in the final prompt.
If needed, they must be extremely few, unreadable, or nearly unreadable small details.
They must have plausible physical carriers. They must not float or be attached to roads, ground, roofs, or large ordinary building walls.
```

---

## Step 9: Text System And Hierarchy

Text strategy:

> Text can be clear, but it must have hierarchy.  
> Text should organize space, not scatter as labels.  
> Text is map place naming, not explanatory copy, wall advertising, menus, price lists, or UI copy.

### Label Count

```text
Recommended total labels: 7-12.
Near labels: usually 0-2.
Middle boundary labels: usually 1.
Visible entrance labels: usually 2-4.
Far background labels: usually 2-4.
```

Do not add text just to reach a number. If the scene already expresses the topic, reduce labels.

### Near Text Hierarchy

```text
Near main label: at most 1, possibly none.
Near secondary label: 0-1.
Near small label: 0-1.
```

Rules:

```text
The near main area name must be small, light, off-center, like a handwritten note on the ground, neighborhood edge, or map paper.
Do not center it.
Do not bold it.
Do not place it at the bottom as another title.
It must not be more prominent than the middle boundary name.
Do not let a near road name become a second or third title.
```

### Node Names Versus Functional Words

Allowed:

```text
Complete map node names may resemble tiny signs, but must be rare and small.
```

Use caution with standalone functional words:

```text
Subscribe, Prompt, Resume, Quality, Models, Apply, Best, Write, Code, Image
```

If these appear alone, they should feel like map annotations or scene implications, not advertising buttons, CTAs, shop signs, wall letters, or UI copy.

### Text Placement

Allowed:

```text
along boundary water, blank boundary lines, mountain passes, or road endings
along distant ridges, coastlines, horizons, or city outlines
near distant building clusters or entrance bands
lightly on the ground or neighborhood edge
around a tiny node with map-like feeling, without connecting lines
```

Forbidden:

```text
scattering text on walls, windows, people, plants, or empty corners
filling the image with short words
turning text into caption arrows
using callouts, pins, markers, locators, or vertical locator lines
connecting entrance or far labels to buildings, ridges, or facilities with thin vertical lines
making text into large wall lettering, advertisements, menus, price lists, rankings, or UI copy
```

---

## Step 10: Middle Boundary And Visible Entrance Layer

The middle boundary must be clear because it carries the psychological structure.

### Boundary Options

Choose according to the topic:

```text
river
ferry
dock
far shoreline
strait
mountain pass
white blank band
blank buffer
road ending
border line
open land outside a wall
canyon
```

A bridge is optional, not the default main axis.

Rules:

```text
The boundary name may be clearly readable.
Bridges, ferries, docks, mountain passes, and thresholds may have humor, but must be geographical details, not process arrows.
Do not draw bridges as system architecture connectors.
Do not let the boundary become the scenic protagonist.
Do not mechanically default to a river; river is only one option.
```

### Visible Entrance Layer

This is Layer 3, beyond the boundary or in the mid-far field.

It may contain a few entrance names:

```text
usually 2-4
only names the observer knows, has seen, or may have used
do not list all products, platforms, brands, companies, people, or theories
do not use real logos
```

Entrance names may remain product, platform, brand, person, or institution names. They do not all need to be turned into geographic metaphors.

Visual rules:

```text
Entrances are smaller and farther than the near field.
They are clearer than the farthest background forces.
They should sit on a far shore, entrance band, distant low building cluster, port, station, island group, or mid-far shoreline.
Entrance names should naturally sit near distant buildings, the shore, water edge, or entrance band, like map place names.
Do not use markers, pins, locators, callouts, leader lines, annotation stems, or vertical lines to connect entrance names to buildings.
Do not make all entrances into neat brand-house signs.
Do not merge the entrance layer and far macro layer into one row.
Do not make a ranking, product recommendation chart, or brand relationship diagram.
```

---

## Step 11: Distant Background Layer

The far field is Layer 4: background macro forces, infrastructure, disputes, and endgame narratives.

Rules:

```text
Far labels: usually 2-4.
The far field should be a compressed continent, mountains, distant city, horizon, blank boundary line, factory outline, lighthouse, or sun.
Far labels should summarize macro forces, not list every entity.
Far labels should sit lightly near ridges, coastlines, blank boundary lines, city outlines, or horizons, like faint distant place names.
Far labels do not need to point precisely to specific objects. Do not use vertical lines, leader lines, locator lines, or callouts to map each label to a mountain, factory, or facility.
```

Far labels should answer:

```text
What are these distant forces overall?
```

Not:

```text
Which exact institutions, companies, models, or technical terms exist?
```

The far field must be:

```text
flatter, lighter, smaller, farther
like news, rumor, distant artillery, or the vague macro background in an ordinary person's mind
```

Avoid:

```text
expert frameworks
complete industry maps
company relationship diagrams
technical term lists
model rankings
real war scenes
tanks, soldiers, explosions, mecha
```

---

## Step 12: Color And Linework

Color goal:

> Pure-white, fresh, linework-first, with a few local colored-pencil anchors.

### White Background Veto

```text
The image must be close to clean screen white / pure white paper.
If the overall result appears gray-grounded, gray-white paper, blue-gray background, gray watercolor wash, gray fog, beige, cream yellow, old-paper yellow, parchment, warm scanned paper, brown vintage filter, or obviously yellowed, it fails even if the structure and linework are correct.
Very pale gray pencil linework, light gray hatching, distant contours, water texture lines, road extension lines, smoke lines, cloud lines, and local pencil shadows do not count as a gray background.
```

White rules:

```text
About 90% of the image must remain pure white paper, close to #FFFFFF screen white.
This white is not gray-white, blue-gray, beige, cream, warm white, old-paper yellow, or parchment.
Forbid gray backgrounds, gray-white paper, blue-gray backgrounds, gray watercolor wash, gray fog, vignettes, overall shadows, warm yellow paper, beige paper, old-paper yellow, parchment, yellowed scan feeling, and brown vintage filters.
Do not use old-paper color to express vintage feeling.
Do not use warm filters to express vintage feeling.
Do not use yellowed scans to express period atmosphere.
Do not use gray washes to express distance, air, fog, shadow, or depth; use only very pale gray pencil lines, light hatching, and low-density contour lines for depth.
```

### Linework

```text
Mainly rely on black, dark-gray, and pale-gray fine lines.
Near-field linework should be clearer; distant layers should recede through finer, lighter, lower-density pale-gray pencil linework.
Allow light gray hatching, distant contour lines, water texture lines, road extension lines, smoke lines, cloud lines, and very small local pencil shadows.
Gray may exist only as linework, hatching, broken lines, contours, and local shadows. It must not become gray blocks, gray fog, gray gradients, or gray background fill.
Lines should be slightly shaky and hand-drawn.
Buildings, roads, boundaries, vehicles, crowds, and distant silhouettes are primarily built with linework.
Do not let color blocks carry the main structure.
```

### Restrained Color

```text
Color appears only as sparse local colored-pencil or crayon strokes.
Clearly colored areas should usually be no more than 8-12% of the image.
Local color is allowed, but it must look like pale colored-pencil or crayon texture, not flat fills.
Color should be broken, uneven, and reveal white paper.
```

### Foreground Color Anchors

```text
The foreground may have a few local color anchors to organize space, strengthen era feeling, and create visual rhythm.
Choose anchors based on topic era, spatial rhythm, and thematic weight.
Do not always color the same modern object type.
Do not give highest color weight to non-thematic background objects.
Color is assigned by visual weight, thematic weight, and spatial rhythm, not by fixed object category.
```

### Pure-White Freshness

```text
Overall feeling should stay pure-white, fresh, and linework-first.
The background is always pure white; do not use a broad gray air wash.
Forbid warm atmosphere.
Forbid an overall gray atmosphere.
Do not use large gray ground fills.
Do not use gray sky fills.
Do not use gray water fills; water should be expressed only through very pale lines, water textures, and shorelines.
Do not use gray distant-mountain fills; distant mountains should be expressed only through pale gray contours, sparse hatching, and low-density detail.
Do not use yellow ground.
Do not use beige buildings.
Do not use orange roofs.
Do not use warm brown shadows.
Do not use large cool-gray shadows; very small local pencil shadows are allowed.
Do not create sunset lighting.
Most building walls should remain white paper linework.
The foreground may contain a few color anchors, but must not become a warm street scene or colorful town.
```

### Ordinary Background Objects

Ordinary shops, vehicles, and living facilities may appear, but should not receive the highest color weight.

```text
Ordinary background shops should not receive the main color anchors.
Ordinary shops should be expressed through windows, doors, awnings, interior people, and linework, not through loud commercial text or brand colors.
```

---

## Step 13: Scale Of People, Vehicles, And Buildings

Subjective scale distortion should operate between psychological distances, not within the same local space.

Rules:

```text
Within the same neighborhood, people, vehicles, buildings, and roads must keep plausible scale.
Vehicles are clearly larger than single people.
A small car is about 2-3 times a person's height in length.
Buildings are clearly larger than people.
People must not look like giants over vehicles, doors, windows, tables, chairs, or buildings.
```

Forbidden:

```text
huge foreground figure
central figure like a poster protagonist, game character, or giant
huge desktop in the foreground
large paper, book, computer, phone, or UI as the main subject
working on the road
reading in a car lane
editing resumes outdoors at a desk
using laptops in public roadway space
```

Outdoor tables and chairs may be ordinary life details, but must not carry office work, complex information processing, model comparison, or resume editing unless the topic explicitly involves street discussion or historical city life.

---

## Step 14: Ordinary Life Details

Keep natural life feeling, but do not let life details replace the structure.

Their function is:

```text
to make the near world feel real, humorous, and breathable
to make the subjective map feel enlarged by ordinary life experience
```

They are not for explaining concepts, and not for decorating a tourist town.

Choose by era and scene:

```text
building edges
doors and windows
balconies
people indoors
ordinary pedestrians
street facilities
vehicles
plants
railings
steps
riverbanks
small roof objects
era-appropriate living tools
```

Rules:

```text
These details do not need to explain the topic.
Do not label all of them.
Do not turn all of them into concept props.
They must not draw more attention than the theme structure.
Life details should mix naturally into the near scene, not become a polished scenic illustration.
```

Avoid:

```text
turning the image into a tourist-town illustration
turning the image into a seaside town, European street, commercial street sketch, or scenery illustration
making life details overly polished, tidy, or commercial
too many storefronts, windows, menu boards, and roadside ads
```

Failure condition:

```text
If the viewer first reads it as a tourist town, seaside town, European street, or ordinary city scene rather than a subjective cognitive map of a topic, it fails.
```

---

## Step 15: Failure Checks

Before using the final prompt, run risk-oriented checks.  
Do not write only "pass". If the final prompt contains high-risk words or high-risk structures, delete or rewrite them first.

### Hard Failures

If any of the following appears, the image fails and must be rewritten:

```text
1. Overall gray-grounded, gray-white paper, blue-gray background, gray watercolor wash, gray fog, vignette, overall shadow, yellowed, beige, cream, old-paper yellow, or warm scanned-paper feeling.
2. The image becomes an infographic, industry map, tool recommendation chart, company relationship diagram, or model ranking.
3. No clear near everyday world, cognitive boundary, visible entrance layer, and far macro layer.
4. Visible entrance layer and far macro layer merge into one layer.
5. The near field is only a thematic node rather than an everyday world.
6. The near field becomes a commercial street, tool market, service counter collection, or functional window collection.
7. The near field shrinks into an empty intersection, isolated person, or thin street.
8. A person becomes the central protagonist, giant, or poster character.
9. Readable thematic text, prompt text, menus, notice walls, recruitment walls, or task words appear on building exteriors.
10. Text becomes scattered callouts, ads, menus, price tables, UI copy, or short task-word lists.
11. Life details turn the image into a tourist town, scenery illustration, or commercial streetscape.
12. Near living environment obviously mismatches the topic era.
13. The visible entrance layer is mechanically turned into neat Harbor / Pier / Gate / Dock / Station formats, like a theme park or brand town.
14. A huge person, huge desk, huge phone, huge screen, or huge UI occupies the main subject.
```

### Risk Checks

Use these checks during plan review and while drafting Part D as applicable:

```text
Near density: Is the foreground a rich large scene occupying the lower image, not an empty intersection, isolated figure, thin road, or single node?
Figure protagonist risk: Is any figure becoming a protagonist, giant, poster figure, or game character?
Wall text: Could building walls, windows, storefronts, or bulletin boards contain readable thematic text?
Dangerous words: Remove window notes, wall notes, posters, task words, checklists, prompt phrases, menus, commercial signs, readable storefront names, and large wall labels.
Era match: Are near details chosen for the topic's era instead of a fixed modern object set? Has the era been judged more specifically than just "modern" or "historical"? Have 3-6 era evidence categories been chosen to serve the topic naturally rather than becoming an object list?
Composition skeleton: Has the composition skeleton, viewpoint height, and spatial axis been chosen before Part D? Is the skeleton determined by the topic, observer, era environment, and cognitive boundary? If it repeats the "left-right foreground buildings + central road or river + far-shore entrances + distant horizon" template, is that truly the most fitting spatial expression for this topic? If not, choose a different skeleton before writing Part D.
Color freshness: Is the image pure-white and linework-first? Is the background close to #FFFFFF rather than gray-white, blue-gray, beige, or warm white? Is there any gray watercolor wash, gray fog, vignette, overall shadow, or large pale-gray fill? Is there enough very pale gray pencil linework, distant contours, shorelines, road extension lines, and local hatching to maintain depth?
Title area: Does the title breathe without a hollow empty band below it?
Four-part chain: Are the near field, boundary, entrance layer, and far macro layer all distinct?
Spatial continuity: Are the near, middle, and far fields naturally connected through roads, rivers, water edges, bridges, docks, slopes, field ridges, mountain ridges, horizons, low-density building bands, or bird-eye sightlines? Does the middle blank space retain enough pale-gray linework and terrain edges? If the image looks like three floating disconnected layers, it fails.
Text hierarchy: Are there only a few map place names, without wall text, menus, ads, or task words?
Annotation lines: Are labels natural map place names without markers, pins, locators, callouts, leader lines, annotation stems, pointers, or vertical guide lines?
Theme anchor: Does the near field contain a small thematic feeling or pressure node without making that node the only subject?
Entrance layer: Are only a few visible entrance names used, and are they separated from the far background layer?
Far labels: Do far labels summarize macro forces rather than list all entities?
Physical scale: Are people, vehicles, and buildings plausible within the same local space?
```

---

## Internal Output Format

Internal working material has four parts. By default, do not show these parts first; use Part D to generate the image directly.

When the user asks to see the analysis, prompt, generation rationale, or the materials used for the image, show Part A, Part B, Part C, and Part D.

### Part A: Topic Analysis

```text
Observer:
What the observer truly sees:
Visible entrances the observer knows by name but does not deeply understand:
Background forces the observer has heard of but does not understand:
Core contrast:
Title strategy:
Era and environment judgment:
Era evidence categories:
Composition skeleton and viewpoint:
```

Use a few specific nouns if useful, but do not expand brands, objects, facilities, or era evidence into a list.
"Era evidence categories" and "Composition skeleton and viewpoint" may be stated as compressed phrases.

### Part B: Spatial Tradeoff Table

```markdown
| Layer | Psychological Distance | Main Terrain | Space Type | Scene Mood | Map Label Strategy | Thematic Node / Life Details |
|---|---|---|---|---|---|---|
```

Rules:

```text
Before Part B, clearly state the composition skeleton, viewpoint height, and spatial axis chosen for this image.
Map label strategy is not a short-word list.
It must explain how labels naturally sit near terrain, shorelines, ridges, building clusters, or neighborhood edges, without connecting lines.
Thematic nodes are not a list of functional counters.
The visible entrance layer and far background layer must be distinct.
Layer 1 must be an era-appropriate large scene or public living space, not "one person standing at an intersection."
If the composition skeleton falls into the common "left-right foreground buildings + central road or river + far-shore entrances + distant horizon" combination, explain why it is the most fitting choice for this topic. Otherwise, choose a different composition.
```

### Part C: Keep/Delete List And Plan Review

Part C only reviews the plan already established in Part A and Part B. It does not inspect the not-yet-written Part D prompt text.

```text
Keep:
Delete:

Near density check:
Figure protagonist check:
Era match check:
Title area check:
Empty band below title check:
Four-part cognitive chain check:
Layer distribution check:
Composition skeleton check:
Spatial continuity check:
Functional node check:
Entrance layer check:
Far label check:
Physical scale check:
```

Part C must not say only "pass".  
Each item should explain why the current plan works, or what must be adjusted before writing Part D.

### Part D: Final Image-Generation Prompt

Write one complete prompt that can be used directly by an image generation model, then use it to generate the image by default.

The final prompt should prioritize:

```text
pure white background, close to #FFFFFF, not gray-white, blue-gray, beige, or warm white
forbid gray watercolor wash, gray fog, vignettes, overall shadows, and large pale-gray fills, while allowing very pale gray pencil linework, light hatching, distant contour lines, water texture lines, road extension lines, smoke lines, cloud lines, and local pencil shadows
the four-part cognitive chain
near / middle / visible entrance / background far layer hierarchy
the selected composition skeleton, viewpoint height, and spatial axis
concrete era evidence, not generic modernity or generic historicity
near, middle, and far fields connected naturally through roads, rivers, water edges, bridges, docks, slopes, field ridges, mountain ridges, horizons, low-density building bands, floor sections, market / station / office-park spaces, or bird-eye sightlines according to the selected composition skeleton; they must not look like disconnected floating layers
near large scene
near building density
near era feeling
people as supporting detail only
theme expressed through space and a few actions
building walls not carrying text
cognitive boundary
visible entrance layer
compressed distant background layer
white-background linework
restrained color and a few color anchors
natural life details
```

Then describe:

```text
a few human actions
a few thematic nodes
a few labels
```

The final prompt must not become:

```text
object list
function list
UI list
short task-word list
brand list
central character setup
```

---

## Usage

The user may simply provide:

```text
Topic: [user topic]
```

Default behavior:

1. Internally complete the topic analysis, spatial tradeoff table, keep/delete list, plan review, and final prompt.
2. Generate the image directly from the Part D prompt.
3. If the runtime permits it, ask whether the user wants to see Part A, Part B, Part C, and Part D after image generation.
4. If the runtime does not permit post-generation text, wait until the user asks to show those materials.

### Reminders

```text
Do not treat any single test topic's place names, entrance names, boundary names, or distant terrain as universal templates.
For every new topic, re-evaluate the observer, era environment, era evidence, composition skeleton, cognitive boundary, visible entrance layer, and far background layer.
If the user provides only a topic, still internally complete Part A-C, then write Part D and generate the image.
```
