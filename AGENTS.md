## Project rules
- Business rules (stock code generation, search/matching) live as pure functions in `src/lib/domain/` with tests in `src/lib/domain/__tests__/`; UI only calls them. Why: the same rules will back the future admin panel and backend.
- Storefront sample data lives in `src/lib/catalog/data.ts` until a backend exists. Why: design phase only; swap the data source later without touching pages.
- Order workflow permissions (who may forward/approve/reject/issue proforma) live in `allowedActions`/`applyAction` in `src/lib/domain/order.ts`; panel screens under `/panel` only call them. Why: the same rules must back the future real login and backend.
- Storefront data is shaped as the MySQL tables (`urunler`, `markalar`, `kategoriler`, `oem_kodlari`, `urun_oem`, `satislar.OdemeTipi`) and mapped to `Product` by `productsFromTables` in `src/lib/domain/db-mapping.ts`. Why: the real database will feed the site in the same shape.
