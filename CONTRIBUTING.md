# Contributing to CDE Motif Desktop

Thanks for your interest in contributing! This is a single-file project so contributions are easy to review and merge.

## Getting Started

1. Fork the repository
2. Open `index.html` in a browser — no build step needed
3. Make your changes
4. Test in at least Chrome/Firefox
5. Open a Pull Request

## Code Style

- **Indentation**: 2 spaces
- **CSS**: Keep Motif 3D rules consistent — always use `var(--hi)` / `var(--lo)` for bevels
- **JavaScript**: Vanilla JS only, no libraries
- **Keep it one file**: Everything must remain in `index.html`

## Adding a Terminal Command

Find the `handleCmd()` function in the `<script>` section. Commands follow this pattern:

```javascript
if (cmd === 'mycommand') {
  tText('output text here');
  renderPromptLine();
  return;
}
```

For commands with arguments, `args` is already parsed as an array.

## Adding a Virtual File

Find the `const FS = {` object and add your entry:

```javascript
'/home/user/myfile.txt': {
  type: 'f',
  size: 123,
  date: 'Mar 9 12:00',
  perm: '-rw-r--r--',
  content: 'your content here'
},
```

Also add the filename to the `children` array of its parent directory.

## Adding a New Application Window

1. Add a `<div class="win" id="win-myapp">` skeleton in the HTML
2. Add an `openWin('win-myapp')` call to a panel button or desktop icon
3. Add a `case 'win-myapp':` in the `wOpen()` init switch if setup is needed

## Reporting Bugs

Open a GitHub Issue with:
- Browser and OS
- Steps to reproduce
- What you expected vs what happened

## Ideas Welcome

- Terminal commands (man, grep, diff, curl simulation, ...)
- Easter eggs hidden in the virtual filesystem
- More Motif-style apps (xcalc, xclock standalone, xedit)
- Better mobile/touch support
- Performance improvements for the chess AI
