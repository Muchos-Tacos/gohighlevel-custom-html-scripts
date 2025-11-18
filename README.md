# Custom HTML Scripts for GoHighLevel Surveys

This repository contains custom HTML scripts used to extend and enhance the functionality of surveys within the GoHighLevel platform for **MuchoRed** projects.

These scripts are organized to match how assets are structured inside GoHighLevel accounts so developers can easily locate, maintain, and update code for specific environments.

---

## Repository Structure

Scripts are organized in the following hierarchy:

```text
├── gohighlevel-custom-html-scripts
|   └── <ProjectName>
|       └── <SurveyName>
|           └── <scriptName>.html
```

### **Project Folder**

Each project gets its own folder and holds survey-specific assets and logic.

### **Survey Folder**

Contains a single `<scriptName>.html` file intended to be inserted inside the corresponding GoHighLevel survey slide’s **Custom HTML** block.

---

## Purpose

GoHighLevel surveys provide limited native customization. These custom HTML snippets extend functionality such as:

-   Advanced validation
-   Enhanced UI/UX behavior
-   Conditional logic
-   API calls
-   Hidden field automation
-   Multi-step or dynamic survey interactions

This repo serves as a centralized documentation hub for maintaining consistent behavior across projects.

---

## Usage

1. Open the corresponding survey inside GoHighLevel.
2. Navigate to the corresponding slide.
3. Add a **Custom HTML** element.
4. Paste the content of the matching `<scriptName>.html` file.
5. Publish or update the survey.

---

## Development Guidelines

-   **Keep scripts isolated** to avoid conflicts with GoHighLevel’s built-in styles and JavaScript.
-   **Avoid global variables** unless required.
-   **Comment thoroughly** for maintainability.
-   **Keep scripts idempotent** so re-rendering inside GoHighLevel does not cause duplicate bindings.
-   **Use project folder names** that clearly reflect client or internal project identifiers.
-   **Ensure compatibility** with GoHighLevel’s sandboxed environment.

---

## Naming Conventions

| Folder  | Convention               | Example               |
| ------- | ------------------------ | --------------------- |
| Project | PascalCase               | `MyFavoriteTherapist` |
| Survey  | PascalCase or SurveyName | `HiringSurvey2`       |
| Script  | camelCase                | `availability.html`   |
