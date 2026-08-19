# HawkerGo prototype

Open `index.html` in a browser, or serve this folder with any static web server.

## QR destinations

- A **table QR** points to `index.html?table=T12`. This opens the stall selector and preserves the table number in the order.
- A **stall QR** points to `index.html?table=T12&stall=nasi-lemak`. This opens the named stall directly. Available stall IDs: `nasi-lemak`, `wok-hey`, `satay-brothers`, and `dessert-lab`.

This is a front-end prototype: food, cart, order, and payment completion are simulated in the browser. It is designed around a 500px maximum mobile layout and works without a framework or installation.

## Production architecture

You do need a backend for a real business:

1. **Seller dashboard/API** — secure logins, stalls, menus, stock availability, prices, and QR/table mapping.
2. **Order service** — saves the cart, assigns an order number, sends an instant notification to the correct stall, and tracks status.
3. **Payments** — use a payment provider such as Stripe, Adyen, or a local PSP. The browser must never collect or store raw card details; the provider handles payment confirmation through webhooks.
4. **Database** — customers/orders/payments/menu data (e.g. PostgreSQL), plus an admin portal for the hawker-centre operator.

Suggested production stack: Next.js + TypeScript for the web/customer and seller portal, PostgreSQL + Prisma for data, and Stripe/local payment provider APIs for payments. It retains the simple mobile experience while adding secure server-side operations.
