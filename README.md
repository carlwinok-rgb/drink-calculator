# Standard Drink Calculator

A one-page web app for counting US standard drinks (0.6 fl oz of pure alcohol) for popular gas station and liquor store drinks. Search a brand, pick the package, set how many, and adjust ABV or proof as needed.

- No login. Each person's drink log stays in their own browser.
- Team-submitted drinks are stored in Supabase (project "Drink Calculator").

## Approving submitted drinks

New submissions arrive with `status = pending` and don't appear in the app until approved.

1. Open the Supabase dashboard → project **Drink Calculator** → **Table Editor** → `drinks`.
2. Check the name, category, strength and package.
   - `strength` is **proof** for liquor categories (Vodka, Whiskey, Rum, Tequila, Gin, Liqueur & other) and **ABV %** for everything else.
3. Change `status` to `approved` to publish it, or `rejected` to hide it.

Approved drinks show up for everyone the next time they open or return to the page.

## How it's protected

- The page uses Supabase's publishable key, which is meant to be public.
- Database rules let visitors **submit** drinks (always as pending) and **read approved** drinks only. They can't approve, edit or delete anything.
- Duplicate names, out-of-range strengths and long text are rejected, and submissions pause if 200 are already waiting for review.

## Hosting

Static site: `index.html` is the whole app. Served with GitHub Pages from the `main` branch (root).
