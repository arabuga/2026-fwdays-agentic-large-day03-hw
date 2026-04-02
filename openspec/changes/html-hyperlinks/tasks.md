# Tasks: html-hyperlinks

Чеклист реалізації (можна відмічати по мірі виконання).

## Реалізація

- [ ] **Canvas**: у `packages/element/src/renderElement.ts` для `isTextElement` з `element.link` задати колір посилання (наприклад `COLOR_PALETTE.blue[4]` + `applyDarkModeFilter` у dark) і намалювати підкреслення під кожним непорожнім рядком (`measureText`, урахування `textAlign`).
- [ ] **Hit-test**: у `packages/excalidraw/components/hyperlink/helpers.ts` у `isPointHittingLink` додати гілку для `isTextElement(element)` + `hitElementBoundingBox` при `!isMobile` і не вибраному елементі (зберегти існуючу логіку view mode та іконки).
- [ ] **SVG**: у `packages/excalidraw/renderer/staticSvgScene.ts` для тексту з `element.link` виставити `fill` як у canvas і `text-decoration: underline` у `style` на `<text>`.
- [ ] **Без регресій**: переконатися, що текст **без** `link` рендериться як раніше (колір `strokeColor`, без підкреслення).

## Дані / UX (вже частково в коді)

- [ ] Переконатися, що сабміт тексту з `[label](url)` через `parseMarkdownLink` у `App.tsx` виставляє `text = label` і `link` = нормалізований URL (існуюча поведінка + toast за потреби).

## Перевірка

- [ ] `yarn test:typecheck`
- [ ] `yarn build`
- [ ] `yarn test` (або `yarn test:update` лише якщо снапшоти очікувано змінились)
- [ ] Ручна перевірка: клік по підпису відкриває URL у новій вкладці; вибраний елемент не відкриває посилання з першого кліку по тексту.

## Документація (за потреби)

- [ ] Оновити `docs/memory/decisionLog.md` або ADR, якщо фіксуєте навмисну зміну UX (bbox vs лише іконка).
- [ ] Після merge: позначити change `html-hyperlinks` як застосований або архівувати в `openspec/changes/archive/` (якщо заведете такий процес).
