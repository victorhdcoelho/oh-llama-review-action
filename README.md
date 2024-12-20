# Ollama Code Review

This action can automatically review the pull request, will give comment and help to enhance the code quality.

## Inputs

| input | require |type  | description                      | default |
|-------|---------|------|----------------------------------|---------|
|model  | Y       |string|choose the model you'd like to use|codellama|
||||

You can choose the model that Ollama provided, can be search [here](https://ollama.com/search).

## Features

- Automatically get files changed in a pull request.
- Runs the Ollama with the model you choose
- Give comments for every change it reviewed

## Usage

Here is a simple demo for this action.

```yml
name: PReviewer

on:
  pull_request:

jobs:
  # Single deploy job since we're just deploying
  reviewer:
    runs-on: ubuntu-latest
    permissions:
      contents: write
      pull-requests: write
    steps:
      - name: PR Review
        uses: RiceBen/oh-llama-review-action
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          model: llama3.2:3b
```