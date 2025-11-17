---
id: dialog
title: Dialog
sidebar_label: Dialog Component
---


# Dialog

The Dialog component provides a lightweight modal with automatic theme detection, async action handling, and simple open/close behavior. It opens when its child element is clicked.

---


## Installation

```bash
pnpm add @mudasarmajeed5/dialog
# or
npm add @mudasarmajeed5/dialog
```

---

## Interaction Behavior

* Clicking the child element opens the dialog
* Clicking outside closes it
* Pressing `Escape` closes it
* `onComplete` shows a loading state until resolved

---
import { Dialog } from "@mudasarmajeed5/dialog";
import React from "react";

export const Preview = () => {
  return (
    <Dialog
      title="Example Dialog"
      description="The Dialog description will go here."
      onComplete={() => new Promise(r => setTimeout(r, 800))}
    >
      <button  style={{ padding: "8px 12px"}}>
        Open Dialog
      </button>
    </Dialog>
  );
};

# Dialog Preview

This is a live preview of the dialog component.

<Preview />
---
## Import

```tsx
import { Dialog } from "@mudasarmajeed5/dialog";
```

---

## Basic Usage


```tsx
<Dialog
  title="Confirm"
  description="Are you sure you want to continue?"
  onCancel={() => console.log("Canceled")}
  onComplete={yourFunction}
>
  <button className="m-btn">Open Dialog</button>
</Dialog>
```


---

## Props

| Prop          | Type                  | Required | Description                                      |
| ------------- | --------------------- | -------- | ------------------------------------------------ |
| `title`       | `string`              | Yes      | Title displayed at the top of the dialog.        |
| `description` | `string`              | Yes      | Text shown under the title.                      |
| `children`    | `ReactNode`           | Yes      | The trigger element that opens the dialog.       |
| `variant`     | `"light" \| "dark"`   | No       | Override theme manually.                         |
| `onCancel`    | `() => void`          | No       | Called when Cancel is clicked.                   |
| `onComplete`  | `() => Promise<void>` | No       | Async handler for Continue. Shows loading state. |

---

## Theme Control

The dialog automatically detects light/dark theme based on:

* `document.documentElement.classList`
* `data-theme` attribute
* System preference (`prefers-color-scheme`)

To lock a theme:

```tsx
<Dialog variant="dark" ... />
```

---

## Async Example (Loading State)


```tsx
<Dialog
  title="Processing"
  description="Please wait..."
  onComplete={async () => {
    await new Promise(r => setTimeout(r, 1500));
  }}
>
  <button className="m-btn">Process</button>
</Dialog>
```
---

