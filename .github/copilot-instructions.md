## Project Overview
This is a single-file React application for learning Spanish verb conjugations. The entire app (HTML, CSS, JavaScript, React components) is embedded in `index.html` using Babel for JSX transformation and external CDNs for dependencies.

## Architecture & Key Components
### Core Data Structures
- **VERBS**: Array of 150+ Spanish verbs with properties:
    - `inf`: Infinitive form
    - `type`: Conjugation pattern ('reg', 'irr', 'go', 'ue', 'ie', 'i', 'zc')
- **IRREGULARS**: Complete irregular verb conjugations for all 10 tenses
- **TENSES**: 10 Spanish tenses (Presente Simple, Pretérito Indefinido, Imperfecto, Perfecto, Futuro, Condicional, Subjuntivo Presente/Imperfecto, Pluscuamperfecto, Futuro Compuesto)
- **PERSONS**: Grammatical persons (Yo, Tú, Él/Ella/Usted, etc.)
- **STREAK_BADGES**: Achievement system with 6 milestone badges

### Main Components
- **App**: Main router between game/study/test views
- **GameSection**: Core gameplay with timer, scoring, difficulty selection, immediate feedback, and streak badges
- **StudySection**: Verb reference with full conjugation tables
- **TestSection**: Multiple-choice testing with sentence contexts
- **BadgeNotification**: Achievement popup notifications
- **StreakBadges**: Visual badge display component
### Conjugation Engine
The `conjugate()` function handles all verb conjugations:
- Regular verbs: Follow standard -ar/-er/-ir patterns
- Irregular verbs: Look up in IRREGULARS object
- Stem-changing verbs: Apply vowel changes (ue, ie, i)
- Special cases: Go verbs, zc verbs, orthographic changes
- New tenses: Conditional, Pluperfect, Future Perfect
## Development Workflow

### Local Development
Open `index.html` directly in a web browser
- No build process required
- Hot reload by refreshing the browser
- Debug using browser DevTools console
### Dependencies
All loaded via CDN:
- React 18 & ReactDOM 18
- Babel standalone for JSX
- Tailwind CSS
- Web Speech API (no external library)

### Data Persistence
- User progress stored in `localStorage` as JSON
- Streak badges persist across sessions
- Automatic save on state changes
- Reset via "Borrar Datos" button

## Code Patterns & Conventions
### Component Structure
```jsx
const ComponentName = ({ prop1, setProp1 }) => {
    const [state, setState] = useState(initialValue);
    // Effects for side effects
    useEffect(() => {
        // Logic here
    }, [dependencies]);
    return (
        <div className="tailwind-classes">
            {/* JSX content */}
        </div>
    );
};
```

### State Management
- Extensive use of React hooks (`useState`, `useEffect`, `useRef`)
- Props drilling for shared state (score, errors, combo, streakBadges, etc.)
- Local storage integration in main App component
- Immediate feedback state management
### Styling Approach
- Tailwind CSS utility classes
- Custom CSS in `<style>` tag for:
    - Theme gradients (Spanish-speaking country flags)
    - Animations (spin, fadeIn, shake, pop, glow, shimmer)
    - Custom scrollbar styling
- Responsive design with `md:` breakpoints
- Dynamic styling based on immediate feedback state
### Audio Integration
```javascript
const speakText = (text) => {
    const u = new SpeechSynthesisUtterance(text);
    u.lang = 'es-ES';
    window.speechSynthesis.speak(u);
};
```

### Game Mechanics
- **Difficulty System**: Easy (22s, +1/-2), Medium (15s, +2/-1), Hard (10s, +3/-1)
- **Combo Multipliers**: x2 after 3 correct, x3 after 6 correct
- **Level Progression**: 6 levels unlocked by score thresholds
- **Time Attack**: 60-second survival mode with penalties
- **Review Mode**: Practice previously incorrect conjugations
- **Immediate Feedback**: Real-time hints and corrections while typing
- **Streak Badges**: Achievement system (5, 10, 15, 20, 25, 30 consecutive correct answers)
### Verb Type System
- `'reg'`: Regular verbs (-ar/-er/-ir)
- `'irr'`: Fully irregular (lookup in IRREGULARS)
- `'go'`: Go verbs (tengo, hago)
- `'ue'`: O→UE stem change (poder, dormir)
- `'ie'`: E→IE stem change (querer, sentir)
- `'i'`: E→I stem change (pedir, servir)
- `'zc'`: C→ZC in first person (conocer, nacer)

## Common Tasks
### Adding New Verbs
1. Add to VERBS array with correct type classification
2. If irregular, add complete conjugations to IRREGULARS object
3. Test conjugation in all tenses via StudySection

### Modifying Game Balance
- Adjust difficulty time limits and scoring in DIFFICULTIES
- Modify combo thresholds in `getMultiplier()`
- Update level thresholds in LEVELS array
- Adjust streak badge milestones in STREAK_BADGES

### Adding New Features
- Create new component functions within the `<script>` tag
- Add new views by extending the `view` state in App
- Update navigation tabs in header
- Add new tenses to TENSES array and conjugation logic

### Styling Changes
- Use Tailwind classes for layout and basic styling
- Add custom CSS in `<style>` tag for animations/themes
- Test responsiveness across mobile/desktop
- Add dynamic styling for immediate feedback states

## Testing & Validation
- Manual testing: Open in browser, test all game modes
- Verify conjugations against Spanish grammar references
- Check localStorage persistence across browser sessions
- Test audio pronunciation on different devices
- Test immediate feedback with various input scenarios
- Verify streak badge unlocking and persistence

## Deployment
- Single file deployment - upload `index.html` to any web server
- No build step required
- Ensure CDN links remain accessible
- Test on various browsers (Chrome, Firefox, Safari, Edge)
# Ruleta de Verbos - AI Coding Guidelines

## Project Overview
This is a single-file React application for learning Spanish verb conjugations. The entire app (HTML, CSS, JavaScript, React components) is embedded in `index.html` using Babel for JSX transformation and external CDNs for dependencies.

## Architecture & Key Components

### Core Data Structures
- **VERBS**: Array of 60+ Spanish verbs with properties:
  - `inf`: Infinitive form
  - `type`: Conjugation pattern ('reg', 'irr', 'go', 'ue', 'ie', 'i', 'zc')
  - `trans`: English translation
  - `ctx`: Example context phrase
- **IRREGULARS**: Complete irregular verb conjugations for all 7 tenses
- **TENSES**: 7 Spanish tenses (Presente Simple, Pretérito Indefinido, etc.)
- **PERSONS**: Grammatical persons (Yo, Tú, Él/Ella/Usted, etc.)

### Main Components
- **App**: Main router between game/study/test views
- **GameSection**: Core gameplay with timer, scoring, difficulty selection
- **StudySection**: Verb reference with full conjugation tables
- **TestSection**: Multiple-choice testing with sentence contexts

### Conjugation Engine
The `conjugate()` function handles all verb conjugations:
- Regular verbs: Follow standard -ar/-er/-ir patterns
- Irregular verbs: Look up in IRREGULARS object
- Stem-changing verbs: Apply vowel changes (ue, ie, i)
- Special cases: Go verbs, zc verbs, orthographic changes

## Development Workflow

### Local Development
- Open `index.html` directly in a web browser
- No build process required
- Hot reload by refreshing the browser
- Debug using browser DevTools console

### Dependencies
All loaded via CDN:
- React 18 & ReactDOM 18
- Babel standalone for JSX
- Tailwind CSS
- Web Speech API (no external library)

### Data Persistence
- User progress stored in `localStorage` as JSON
- Automatic save on state changes
- Reset via "Borrar Datos" button

## Code Patterns & Conventions

### Component Structure
```jsx
const ComponentName = ({ prop1, setProp1 }) => {
    const [state, setState] = useState(initialValue);
    
    // Effects for side effects
    useEffect(() => {
        // Logic here
    }, [dependencies]);
    
    return (
        <div className="tailwind-classes">
            {/* JSX content */}
        </div>
    );
};
```

### State Management
- Extensive use of React hooks (`useState`, `useEffect`, `useRef`)
- Props drilling for shared state (score, errors, etc.)
- Local storage integration in main App component

### Styling Approach
- Tailwind CSS utility classes
- Custom CSS in `<style>` tag for:
  - Theme gradients (Spanish-speaking country flags)
  - Animations (spin, fadeIn, shake, pop)
  - Custom scrollbar styling
- Responsive design with `md:` breakpoints

### Audio Integration
```javascript
const speakText = (text) => {
    const u = new SpeechSynthesisUtterance(text);
    u.lang = 'es-ES';
    window.speechSynthesis.speak(u);
};
```

### Game Mechanics
- **Difficulty System**: Easy (22s, +1/-2), Medium (15s, +2/-1), Hard (10s, +3/-1)
- **Combo Multipliers**: x2 after 3 correct, x3 after 6 correct
- **Level Progression**: 6 levels unlocked by score thresholds
- **Time Attack**: 60-second survival mode with penalties
- **Review Mode**: Practice previously incorrect conjugations

### Verb Type System
- `'reg'`: Regular verbs (-ar/-er/-ir)
- `'irr'`: Fully irregular (lookup in IRREGULARS)
- `'go'`: Go verbs (tengo, hago)
- `'ue'`: O→UE stem change (poder, dormir)
- `'ie'`: E→IE stem change (querer, sentir)
- `'i'`: E→I stem change (pedir, servir)
- `'zc'`: C→ZC in first person (conocer, nacer)

## Common Tasks

### Adding New Verbs
1. Add to VERBS array with correct type classification
2. If irregular, add complete conjugations to IRREGULARS object
3. Test conjugation in all tenses via StudySection

### Modifying Game Balance
- Adjust difficulty time limits and scoring in DIFFICULTIES
- Modify combo thresholds in `getMultiplier()`
- Update level thresholds in LEVELS array

### Adding New Features
- Create new component functions within the `<script>` tag
- Add new views by extending the `view` state in App
- Update navigation tabs in header

### Styling Changes
- Use Tailwind classes for layout and basic styling
- Add custom CSS in `<style>` tag for animations/themes
- Test responsiveness across mobile/desktop

## Testing & Validation
- Manual testing: Open in browser, test all game modes
- Verify conjugations against Spanish grammar references
- Check localStorage persistence across browser sessions
- Test audio pronunciation on different devices

## Deployment
- Single file deployment - upload `index.html` to any web server
- No build step required
- Ensure CDN links remain accessible
- Test on various browsers (Chrome, Firefox, Safari, Edge)