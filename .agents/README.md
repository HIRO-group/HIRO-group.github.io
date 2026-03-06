# Agent Documentation

This directory contains resources specifically designed to help AI agents understand the HIRO Group website repository.

## Table of Contents
- [Repository Structure](structure.md) - Overview of the project architecture.
- [Verification Guide](#verifying-changes) - How to test changes locally.

## Core Purpose
The HIRO Group website is a Jekyll-based static site that serves as the official portal for the Human Interaction and Robotics Group. It manages people, publications, and research subteams via structured YAML data and Markdown posts.

> [!IMPORTANT]
> These documentation files should be reviewed and updated every time a major change or a site release occurs to ensure they remain accurate for future agents.

## Verifying Changes
To verify changes locally:
1. Run `bundle exec jekyll serve`.
2. Open the local address (usually `http://127.0.0.1:4000`) in a browser.
3. Navigate to the relevant page (e.g., `/people.html`) to ensure the UI renders correctly and data is updated.
