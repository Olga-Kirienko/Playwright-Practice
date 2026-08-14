# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: modalWindow.spec.ts >> Check Click Me Button
- Location: tests/modalWindow.spec.ts:4:5

# Error details

```
Test timeout of 30000ms exceeded.
```

```
Error: page.goto: net::ERR_ABORTED; maybe frame was detached?
Call log:
  - navigating to "https://webdriveruniversity.com/Popup-Alerts/index.html", waiting until "load"

```

# Test source

```ts
  1  | import { type Page, type Locator } from '@playwright/test';
  2  | 
  3  | export class ModalWindow {
  4  |   readonly page: Page;
  5  |   readonly clickMeButton: Locator;
  6  |   readonly closeButton: Locator;
  7  |   readonly modalContainer: Locator;
  8  |   readonly modalBody: Locator;
  9  | 
  10 |   constructor(page: Page) {
  11 |     this.page = page;
  12 |     this.clickMeButton = page.locator('#button2');
  13 |     this.closeButton = page.getByRole('button', { name: 'Close' });
  14 |     this.modalContainer = page.locator('.modal-content');
  15 |     this.modalBody = page.locator('.modal-body');
  16 |   }
  17 | 
  18 |   async goto() {
> 19 |     await this.page.goto(
     |                     ^ Error: page.goto: net::ERR_ABORTED; maybe frame was detached?
  20 |       'https://webdriveruniversity.com/Popup-Alerts/index.html'
  21 |     );
  22 |   }
  23 | 
  24 |   async openModalWindow() {
  25 |     await this.clickMeButton.click();
  26 |   }
  27 | 
  28 |   async closeModalWindow() {
  29 |     await this.closeButton.click();
  30 |   }
  31 | }
  32 | 
```