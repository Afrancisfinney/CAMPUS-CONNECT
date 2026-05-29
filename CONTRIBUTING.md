# Contributing to Campus Connect

## Welcome!

Thank you for your interest in contributing to Campus Connect! This document provides guidelines and instructions for contributing to the project.

## Code of Conduct

- Be respectful and inclusive
- Report issues professionally
- Provide constructive feedback
- Help others learn and grow

## Getting Started

### 1. Fork and Clone
```bash
git clone <your-fork-url>
cd CONNECTIT
```

### 2. Create Feature Branch
```bash
git checkout -b feature/feature-name
# or for bug fixes
git checkout -b fix/bug-name
```

### 3. Follow Coding Standards

#### Frontend (React)
```javascript
// Use functional components
const MyComponent = ({ prop1, prop2 }) => {
  return (
    <div className="flex items-center">
      {/* Use Tailwind classes */}
    </div>
  );
};

export default MyComponent;
```

#### Backend (Node.js)
```javascript
// Use async/await
export const getUsers = async (req, res) => {
  try {
    const users = await User.find();
    res.status(200).json({ users });
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
};
```

## Commit Messages

Use clear, descriptive commit messages:

```
✨ feat: add user profile page
🐛 fix: resolve authentication bug
📚 docs: update API documentation
🎨 style: improve button component
♻️ refactor: reorganize folder structure
```

### Types
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation
- `style:` - Code style changes
- `refactor:` - Code refactoring
- `test:` - Tests
- `chore:` - Dependencies, build

## Pull Request Process

### Before Submitting PR
- [ ] Code follows style guide
- [ ] Tests pass (if applicable)
- [ ] Documentation updated
- [ ] No console errors
- [ ] Commit messages are clear
- [ ] Features are tested locally

### PR Description Template
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] New feature
- [ ] Bug fix
- [ ] Documentation update
- [ ] Breaking change

## Related Issue
Closes #(issue number)

## Screenshots
If applicable, add screenshots

## Testing
Describe tests performed

## Checklist
- [ ] Changes follow code style
- [ ] Self-review completed
- [ ] Comments added
- [ ] Documentation updated
- [ ] No new warnings generated
- [ ] Tests pass locally
```

## Development Guidelines

### Frontend
- Use functional components with hooks
- Keep components small and focused
- Use Redux for global state
- Use local state for component state
- Add PropTypes or TypeScript (future)
- Follow Tailwind utility-first approach
- Use Framer Motion for animations
- Make components responsive

### Backend
- Use async/await, not callbacks
- Validate all inputs with Zod
- Add proper error handling
- Use environment variables
- Follow MVC pattern
- Add meaningful comments
- Use consistent naming
- Keep functions focused

### Database
- Use appropriate indexes
- Validate data in schema
- Document schema changes
- Use timestamps for records
- Implement soft deletes if needed

## Feature Implementation Checklist

When adding a new feature:

### Backend
- [ ] Create route in appropriate file
- [ ] Create/update controller
- [ ] Create/update model if needed
- [ ] Add validation
- [ ] Add error handling
- [ ] Test with Postman/Thunder Client
- [ ] Document API endpoint

### Frontend
- [ ] Create component(s)
- [ ] Add service method
- [ ] Connect Redux if needed
- [ ] Add styling (Tailwind)
- [ ] Test in browser
- [ ] Check responsive design
- [ ] Test error states

### Testing
- [ ] Test happy path
- [ ] Test error cases
- [ ] Test edge cases
- [ ] Cross-browser test
- [ ] Mobile test

## File Naming Conventions

```
Components:     MyComponent.jsx
Pages:          MyPage.jsx
Hooks:          useFetch.js
Utils:          helpers.js
Services:       services.js
Styles:         Use Tailwind, no separate CSS files
Controllers:    myController.js
Models:         MyModel.js
Routes:         myRoutes.js
```

## Folder Structure Rules

- Keep files organized by feature
- One main component per file
- Export components as default
- Keep imports organized
- Use relative imports for local files

## Documentation

- Update README.md if API changes
- Document complex logic with comments
- Keep DEVELOPMENT_GUIDE.md updated
- Document new environment variables
- Add inline comments for non-obvious code

## Testing Checklist

Before submitting PR:

**Frontend:**
- [ ] Page loads without errors
- [ ] Form validation works
- [ ] API calls succeed
- [ ] Error messages display
- [ ] Responsive on mobile
- [ ] Dark mode works
- [ ] Animations smooth

**Backend:**
- [ ] Endpoint returns correct data
- [ ] Validation works
- [ ] Error handling works
- [ ] Database operations correct
- [ ] Authentication checks pass
- [ ] Rate limiting works
- [ ] No console errors

## Performance Considerations

- Use React.memo for heavy components
- Implement lazy loading for routes
- Optimize images
- Debounce search inputs
- Use pagination for lists
- Minimize API calls
- Use caching where appropriate

## Security Checklist

- [ ] No sensitive data in frontend
- [ ] Passwords hashed on backend
- [ ] Tokens securely stored
- [ ] CORS properly configured
- [ ] Input validation on both ends
- [ ] SQL injection prevention (via Mongoose)
- [ ] XSS prevention (React built-in)
- [ ] Rate limiting implemented

## Questions or Need Help?

- Check existing code for patterns
- Review DEVELOPMENT_GUIDE.md
- Check API_DOCUMENTATION.md
- Review similar features
- Open an issue for discussion

## License

By contributing, you agree that your contributions will be licensed under the same license as the project.

---

Thank you for contributing to Campus Connect! 🎉
