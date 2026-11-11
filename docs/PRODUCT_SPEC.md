# Shoppit — Initial Product Specification

## 1. Purpose

Build a shared online shopping network for independent sellers. Each seller gets a storefront and dashboard within one platform. The platform operates the network and acts as an impartial referee; it is not itself a retailer.

## 2. Store types

- **Physical store:** lists products it supplies and manages its own stock.
- **Virtual store:** curates products supplied by other participating sellers; it does not claim to own that stock.
- **Hybrid store:** lists its own products and products supplied by others.

A product's supplier identity must remain visible and must not be replaced by the identity of the store displaying it.

## 3. Main interfaces

1. **Public website:** browse stores and products, discover offers, and contact sellers.
2. **Mobile experience:** the same service in a mobile-friendly PWA. Avoid building a separate native app initially.
3. **Seller dashboard:** manage store profile, listings, own stock information, enquiries/orders, settings, and referral records.
4. **Referee dashboard:** manage stores, review attribution, inspect records, handle disputes, and manage advertising rules.

## 4. Product and listing model

Separate the shared identity of a product from each seller's listing or offer.

Each listing should identify:
- The store displaying the product.
- The actual supplier store.
- The shared product identity.
- Seller-specific price and availability information, where applicable.
- Whether the listing is the seller's own product or a curated supplier product.

The platform records seller-provided availability; it does not own or physically manage inventory.

## 5. Customer discovery and referral attribution

The store that first introduces a customer to the network may receive a referral benefit when that customer later buys from another participating supplier.

Proposed initial rule:
- Attribute a customer to the store where a shopping journey begins.
- Attribution lasts 90 days.
- A new shopping journey started at the same originating store renews that period.
- When attribution expires, a later journey at another store may establish a new origin.
- Keep an auditable history of attribution changes.

Reliable cross-device attribution requires a customer account or verified identifier and appropriate customer notice and consent. A browser cookie alone is not sufficient.

The exact attribution rules, exceptions, and referral rate must be agreed before referral earnings are activated.

## 6. Enquiries, orders, and financial records

For the first pilot, route enquiries to the actual supplier and record their status. Do not process customer payments yet.

When transaction tracking is introduced:
- Supplier proceeds and originating-store referral benefits are separate records.
- Only completed, verified sales should generate referral earnings initially.
- Cancellations and refunds must reverse the relevant entries.
- Keep an append-only ledger: corrections use reversal or adjustment entries rather than silently changing history.
- Platform advertising revenue is accounted for separately from seller referral benefits.

## 7. Advertising

The platform may earn revenue by displaying advertising. Sponsored products, stores, and banners must be clearly labelled. Paid placement must not be presented as an organic ranking.

Advertising is not required for the first working pilot.

## 8. Roles and access control

- **Customer:** browses and makes enquiries.
- **Seller:** manages authorised store records and listings.
- **Referee/admin:** manages the network and reviews records.

The server must derive a seller's Store ID from the authenticated session. A seller must never gain access to another store's private data by changing a URL or request parameter.

## 9. First pilot — deliberately limited

Target:
- Three test stores: physical, virtual, and hybrid.
- Approximately 20 sample products.
- Storefront pages and product browsing.
- Clear supplier identity on every listing.
- Enquiry routing to the actual supplier.
- Basic customer-origin attribution with an audit trail.
- Basic seller and referee dashboards.

Out of scope for this pilot:
- Payment gateway and automated payouts.
- Delivery or logistics integration.
- Native Android/iOS applications.
- Automated advertising marketplace.
- Complex commission plans.
- Large-scale multi-region infrastructure.

## 10. Initial technical principles

- One codebase and one shared application.
- One central database.
- Strict role-based access and store-level data isolation.
- Mobile-first responsive interface; consider PWA installation.
- Keep the first deployment easy to operate and back up.

A lightweight Python web framework and PostgreSQL are candidate choices. Confirm the stack after reviewing suitable starter repositories.

## 11. Decisions to confirm later

- Final public product and platform names.
- Whether customer accounts are mandatory before referral attribution.
- Referral rate and any category-specific rules.
- What event counts as a new shopping journey.
- Whether the pilot records enquiries only or also manually verified completed sales.
- Applicable privacy, consumer-protection, tax, and advertising requirements for the operating market.

## 12. Development approach

Build in small, testable stages:
1. Create the basic application and database.
2. Add store registration and secure seller login.
3. Add product listings and public storefronts.
4. Add supplier-aware product display and enquiry routing.
5. Add basic referral attribution and the referee dashboard.
6. Test with the three pilot stores before adding payments or advertising.

Do not add features merely because they may be useful later. Keep the pilot understandable, deployable, and maintainable.
