# Example Well-Defined Features

These examples demonstrate how to write clear, testable feature specifications. Use them as reference when breaking down features.

---

## Example 1: User Prompt Input

A core input feature for a chat application.

### User Prompt Input

**Status:** 🔴 Not Started

**Description:** User can enter text and submit messages to the AI via a text input area at the bottom of the chat interface.

**Dependencies:** None (core feature)

**Tests:**
- [ ] Text area is visible at bottom of chat view
- [ ] Text area is focused on initial page load
- [ ] User can type and see text appear in the text area
- [ ] Text area expands vertically as content grows (up to max height)
- [ ] Microphone button is visible next to text area
- [ ] Clicking microphone activates speech-to-text
- [ ] Dictated text streams into text area in real-time
- [ ] Pressing Enter submits the message (when not shift+enter)
- [ ] Shift+Enter creates a new line without submitting
- [ ] Send button is visible and clickable
- [ ] Clicking Send button submits the message
- [ ] Text area clears after successful submission
- [ ] Text area is disabled while AI is responding
- [ ] Empty submissions are prevented (button disabled, enter ignored)

**Notes:** Consider debouncing the auto-resize calculation.

---

## Example 2: User Authentication

A standard authentication feature.

### User Authentication

**Status:** 🔴 Not Started

**Description:** Users can create accounts, log in, and log out. Authentication state persists across browser sessions.

**Dependencies:** None (core feature)

**Tests:**
- [ ] Sign up form is accessible from landing page
- [ ] Sign up requires email, password, and password confirmation
- [ ] Password must be at least 8 characters
- [ ] Password confirmation must match password
- [ ] Invalid email format shows error message
- [ ] Successful signup redirects to main app
- [ ] Login form is accessible from landing page
- [ ] Login accepts email and password
- [ ] Invalid credentials show error message (without revealing which is wrong)
- [ ] Successful login redirects to main app
- [ ] User remains logged in after closing and reopening browser
- [ ] Logout button is visible when logged in
- [ ] Clicking logout returns user to landing page
- [ ] Protected routes redirect to login when not authenticated

**Notes:** Use secure httpOnly cookies for session management.

---

## Example 3: Dark Mode Toggle

A UI preference feature.

### Dark Mode Toggle

**Status:** 🔴 Not Started

**Description:** Users can switch between light and dark color themes. Preference persists across sessions.

**Dependencies:** Feature 1 (Basic UI Layout)

**Tests:**
- [ ] Toggle switch is visible in settings or header
- [ ] Default theme matches system preference
- [ ] Clicking toggle switches from light to dark mode
- [ ] Clicking toggle again switches from dark to light mode
- [ ] All text remains readable in both themes
- [ ] All interactive elements remain visible in both themes
- [ ] Theme preference persists after page refresh
- [ ] Theme preference persists after closing and reopening browser
- [ ] Transition between themes is smooth (no flash)
- [ ] Icons and images adapt appropriately to theme

**Notes:** Use CSS custom properties for theme colors. Consider prefers-color-scheme media query for initial state.

---

## Example 4: Search Functionality

A data retrieval feature.

### Item Search

**Status:** 🔴 Not Started

**Description:** Users can search through their items by title and content. Results update in real-time as they type.

**Dependencies:** Feature 3 (Item Display List)

**Tests:**
- [ ] Search input is visible above item list
- [ ] Search input has placeholder text indicating its purpose
- [ ] Typing in search filters the displayed items
- [ ] Search matches items by title (case-insensitive)
- [ ] Search matches items by content/description (case-insensitive)
- [ ] Results update as user types (debounced, not on every keystroke)
- [ ] Empty search shows all items
- [ ] No matches shows "No results found" message
- [ ] Clear button appears when search has text
- [ ] Clicking clear button empties search and shows all items
- [ ] Search term is highlighted in results
- [ ] Result count is displayed (e.g., "5 items found")

**Notes:** Debounce search to 300ms to avoid excessive filtering.

---

## Example 5: Drag and Drop Reordering

An interaction-heavy feature.

### List Item Reordering

**Status:** 🔴 Not Started

**Description:** Users can drag items to reorder them in their list. Order persists after page reload.

**Dependencies:** Feature 3 (Item Display List)

**Tests:**
- [ ] Drag handle is visible on each list item
- [ ] Cursor changes to grab icon when hovering drag handle
- [ ] Clicking and holding drag handle initiates drag
- [ ] Dragged item follows cursor position
- [ ] Visual indicator shows where item will be dropped
- [ ] Other items shift to make room for drop position
- [ ] Releasing mouse drops item in new position
- [ ] Item order updates immediately after drop
- [ ] New order persists after page refresh
- [ ] Drag can be cancelled by pressing Escape
- [ ] Keyboard users can reorder using arrow keys
- [ ] Screen readers announce position changes

**Notes:** Use a library like dnd-kit for accessibility. Test on touch devices.

---

## Common Patterns

### Visibility Tests
- [ ] [Element] is visible at [location]
- [ ] [Element] has [expected content/state]

### Interaction Tests
- [ ] Clicking [element] [does action]
- [ ] Pressing [key] [does action]
- [ ] [Action] when [condition]

### State Tests
- [ ] [State] persists after [event]
- [ ] [Element] updates when [change occurs]

### Validation Tests
- [ ] [Invalid input] shows error message
- [ ] [Valid input] proceeds without error

### Edge Case Tests
- [ ] Empty [thing] shows [appropriate response]
- [ ] Maximum [thing] is handled gracefully

### Accessibility Tests
- [ ] Keyboard users can [do action]
- [ ] Screen readers announce [change]

---

## Anti-Patterns to Avoid

### Too Vague
❌ "Feature works correctly"
❌ "User experience is good"
❌ "Performance is acceptable"

### Not Observable
❌ "Code is clean"
❌ "Database is optimized"
❌ "Security is handled"

### Multiple Things at Once
❌ "User can create, edit, and delete items"
(This should be 3 separate features)

### Implementation Details
❌ "React component renders without errors"
❌ "API returns 200 status"
(Focus on what the user sees, not how it works)
