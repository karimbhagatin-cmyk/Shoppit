# Shoppit

A simple network of independent online stores.

Shoppit gives each seller a storefront and dashboard within one platform. Sellers can list their own products, display products supplied by other participating sellers, or do both.

The platform acts as a **referee and service operator**. It records customer discovery and referral attribution, routes enquiries to the actual supplier, and keeps records transparent. It does not own stock or sell products.

## First milestone

Build a small working pilot with:

- One shared website and mobile-friendly application (PWA).
- A storefront and dashboard for each seller.
- A platform/referee dashboard.
- Product discovery across participating stores.
- Enquiry routing to the actual supplier.
- Basic, auditable store-referral attribution.

Start with three test stores: one physical-inventory store, one virtual store, and one hybrid store, with approximately 20 sample products.

## Guiding rules

1. Sellers manage their own products, prices, and stock information.
2. Every product listing identifies its actual supplier.
3. A store displaying another seller's product does not become its supplier.
4. Supplier proceeds and store-referral benefits are separate entitlements.
5. Sellers can access only their own store's private data.
6. Sponsored placements must be clearly labelled.
7. Referral and transaction adjustments must be auditable.

## Keep the first version small

The first pilot focuses on product discovery and enquiries. Payment processing, delivery integration, automated payouts, and a full advertising marketplace are later stages.

## Initial technical direction

Use one application and one shared database, with strict store-level data isolation. A lightweight Python web application is a candidate starting point; the final stack will be confirmed after reviewing suitable starter projects.

See [docs/PRODUCT_SPEC.md](docs/PRODUCT_SPEC.md) for the initial requirements.

## Status

**Stage: Project definition.** Application code has not yet been added.
