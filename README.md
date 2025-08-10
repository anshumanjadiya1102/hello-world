# Hello everybody

A brief description of what this project does and who it's for.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Installation

```bash
# Clone the repository
git clone https://github.com/your-username/your-repo.git

# Change directory
cd your-repo

# Install dependencies (if any)
npm install
```

## Usage

Explain how to use your project with code examples or commands.

```bash
# Example command to run your project
npm start
```

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
my-repo/
├── README.md
├── src/
├── package.json
└── ...
name: Check README Location

on: [push, pull_request]

jobs:
  check-readme:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Ensure README is only at root
      run: |
        misplaced=$(find . -type f -iname 'readme.md' ! -path './README.md')
        if [[ -n "$misplaced" ]]; then
          echo "README.md found in subfolder(s):"
          echo "$misplaced"
          exit 1
        fi
