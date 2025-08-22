# Software Agents Documentation Library

A comprehensive collection of software agent documentation and collaboration workflows that can be used as a library in other projects.

## 📚 Contents

This repository contains:

- **Agent Documentation** (`agents/` directory):
  - `architect_agent.md` - Technical architecture and system design guidelines
  - `design_agent.md` - UX/UI design processes and standards
  - `documentation_agent.md` - Documentation standards and processes
  - `engineering_agent.md` - Development guidelines and best practices
  - `product_agent.md` - Product management and requirements definition

- **Workflow Documentation**:
  - `workflow_and_collaboration.md` - Team collaboration workflows and artifact ownership matrix

## 🚀 Using as a Library

### Option 1: Download Release Package

Go to the [Releases](../../releases) page and download the latest version:

```bash
# Download and extract tar.gz
wget https://github.com/[YOUR_USERNAME]/software-agents/releases/download/v1.0.0/software-agents-1.0.0.tar.gz
tar -xzf software-agents-1.0.0.tar.gz

# Or download and extract zip
wget https://github.com/[YOUR_USERNAME]/software-agents/releases/download/v1.0.0/software-agents-1.0.0.zip
unzip software-agents-1.0.0.zip
```

### Option 2: Git Submodule

Add this repository as a submodule to your project:

```bash
# Add as submodule
git submodule add https://github.com/[YOUR_USERNAME]/software-agents.git docs/software-agents

# Initialize and update submodule
git submodule update --init --recursive

# Switch to a specific version
cd docs/software-agents
git checkout v1.0.0
```

### Option 3: Direct Clone

```bash
git clone https://github.com/[YOUR_USERNAME]/software-agents.git
cd software-agents
git checkout v1.0.0  # Use specific version
```

## 📦 Automatic Versioning

This repository uses GitHub Actions to automatically:

- **Version bumping**: Based on commit messages
  - `feat:` or `feature:` → Minor version bump (1.0.0 → 1.1.0)
  - `BREAKING CHANGE` or `major:` → Major version bump (1.0.0 → 2.0.0)
  - Other commits → Patch version bump (1.0.0 → 1.0.1)

- **Package creation**: Automatically creates `.tar.gz` and `.zip` packages
- **GitHub releases**: Creates releases with download links and usage instructions
- **Version tracking**: Includes `VERSION` and `MANIFEST.txt` files in packages

## 🔄 Integration Examples

### In Documentation Projects

```bash
# Copy specific agent documentation
cp software-agents/agents/architect_agent.md docs/architecture/
cp software-agents/agents/product_agent.md docs/product/
cp software-agents/workflow_and_collaboration.md docs/team-processes/
```

### In Project Templates

```bash
# Create a new project with agent templates
mkdir my-new-project
cd my-new-project
tar -xzf software-agents-1.0.0.tar.gz
mv agents/ docs/team-guides/
mv workflow_and_collaboration.md docs/
```

### Version-Specific Usage

Check the `VERSION` file to ensure compatibility:

```bash
# Check version
cat VERSION

# Check what's included
cat MANIFEST.txt
```

## 📋 Version History

Each release includes:
- Complete markdown documentation
- Version information (`VERSION` file)
- Package manifest (`MANIFEST.txt`)
- Structured directory layout for easy integration

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes to the documentation
4. Commit with conventional commit messages
5. Push and create a pull request

The automated workflow will handle versioning and packaging when changes are merged to main.

## 📄 License

MIT License - see LICENSE file for details.
