# Лаб 8. Bootstrap ба Tailwind CSS — нэг хуудас, хоёр арга

- `bootstrap.html` — Bootstrap 5.3.3 (CDN), `css/brand.css` дахь `.btn-brand`
- `tailwind.html` — Tailwind v4 (`@tailwindcss/cli`), `src/input.css` → `css/tailwind.css`

```
npm install
npm run build     # css/tailwind.css үүснэ (минифай хийсэн)
```

## Хэмжилтийн хүснэгт

| Үзүүлэлт | Bootstrap | Tailwind |
|---|---|---|
| CSS файл (raw / gzip) | 227.4 KB / 30.1 KB | 15.0 KB / 3.8 KB |
| JS (raw / gzip) | 78.8 KB / 23.2 KB (bundle) | 0 (framework JS байхгүй) |
| Өөрийн нэмэлт CSS | `brand.css` 13 мөр, 0.4 KB | `input.css` 13 мөр (build-д орно) |
| HTML (raw / gzip) | 7.3 KB / 2.2 KB | 9.3 KB / 2.4 KB |
| Нийт raw (HTML+CSS+JS) | ≈ 314 KB | ≈ 25 KB |
| Нэг card-ын class тоо* | 20 | 39 |
| Lighthouse Performance | _____ | _____ |
| Lighthouse Accessibility | _____ | _____ |
| Lighthouse Best Practices | _____ | _____ |
| Lighthouse SEO | _____ | _____ |

\* `<article>` дотрох бүх элементийн `class` токенуудын нийлбэр (grid-ийн `col` wrapper-ийг оролгүй).
Файлын хэмжээг `npm`-ийн `bootstrap@5.3.3` dist болон build-ийн үр дүнгээс gzip -9-ээр хэмжсэн (CDN-ий жинхэнэ дамжуулалт brotli-тэй бол арай бага).
Lighthouse: Chrome DevTools → Lighthouse → Mobile, дээрх хоёр хуудсыг GitHub Pages дээр тус тусад нь ажиллуулж нөхнө.

## Дүгнэлт

Хоёр хуудас ижил агуулга, ижил dark mode, validation-тэй хэдий ч жин нь эрс ялгаатай: Bootstrap нь бүтэн CSS (≈ 30 KB gzip) болон JS bundle (≈ 23 KB gzip) ачаалдаг бол Tailwind нь зөвхөн хуудсанд ашигласан класс-аа агуулсан ≈ 4 KB gzip CSS үүсгэсэн бөгөөд JS огт шаардаагүй. Нөгөө талаар Bootstrap-ийн card нь 20 класстай, Tailwind-ийнх 39 класстай тул Bootstrap-ийн HTML нь уншихад товч, бэлэн component (navbar-collapse, `needs-validation`) өгдөг; Tailwind нь HTML-д хэв маяг бүрийг тодорхой бичүүлдэг ч `bg-brand`, `dark:`, `user-invalid:` зэрэг token ба variant-аар илүү нарийн хяналт, жижиг эцсийн CSS өгдөг. Тиймээс хурдан, стандарт харагдацтай хуудсыг бэлэн component-оор хийх бол Bootstrap, гүйцэтгэл ба өөрийн дизайн систем чухал бол Tailwind илүү тохиромжтой гэж үзлээ; Lighthouse-ийн оноог хэмжсэний дараа энэ дүгнэлтийг тоогоор баталгаажуулна.
