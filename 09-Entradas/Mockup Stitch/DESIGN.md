---
name: PaseoYa Premium Marketplace
colors:
  surface: '#faf8ff'
  surface-dim: '#d2d9f4'
  surface-bright: '#faf8ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f2f3ff'
  surface-container: '#eaedff'
  surface-container-high: '#e2e7ff'
  surface-container-highest: '#dae2fd'
  on-surface: '#131b2e'
  on-surface-variant: '#444651'
  inverse-surface: '#283044'
  inverse-on-surface: '#eef0ff'
  outline: '#757682'
  outline-variant: '#c5c5d3'
  surface-tint: '#4059aa'
  primary: '#00236f'
  on-primary: '#ffffff'
  primary-container: '#1e3a8a'
  on-primary-container: '#90a8ff'
  inverse-primary: '#b6c4ff'
  secondary: '#006a61'
  on-secondary: '#ffffff'
  secondary-container: '#86f2e4'
  on-secondary-container: '#006f66'
  tertiary: '#3e2400'
  on-tertiary: '#ffffff'
  tertiary-container: '#5c3800'
  on-tertiary-container: '#ef9900'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#dce1ff'
  primary-fixed-dim: '#b6c4ff'
  on-primary-fixed: '#00164e'
  on-primary-fixed-variant: '#264191'
  secondary-fixed: '#89f5e7'
  secondary-fixed-dim: '#6bd8cb'
  on-secondary-fixed: '#00201d'
  on-secondary-fixed-variant: '#005049'
  tertiary-fixed: '#ffddb8'
  tertiary-fixed-dim: '#ffb95f'
  on-tertiary-fixed: '#2a1700'
  on-tertiary-fixed-variant: '#653e00'
  background: '#faf8ff'
  on-background: '#131b2e'
  surface-variant: '#dae2fd'
typography:
  display-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 36px
    fontWeight: '800'
    lineHeight: 44px
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 28px
    fontWeight: '700'
    lineHeight: 36px
    letterSpacing: -0.02em
  headline-lg-mobile:
    fontFamily: Plus Jakarta Sans
    fontSize: 24px
    fontWeight: '700'
    lineHeight: 32px
    letterSpacing: -0.01em
  headline-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 20px
    fontWeight: '600'
    lineHeight: 28px
    letterSpacing: -0.01em
  headline-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 24px
  body-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  body-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
  label-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 20px
    letterSpacing: 0.01em
  label-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 12px
    fontWeight: '600'
    lineHeight: 16px
    letterSpacing: 0.02em
  label-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 11px
    fontWeight: '700'
    lineHeight: 14px
    letterSpacing: 0.03em
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1rem
  gutter-mobile: 0.75rem
  margin: 1.5rem
  margin-mobile: 1rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2rem
---

## Brand & Style
The design system articulates an upscale, effortless urban marketplace experience tailored to the iconic architectural and commercial atmosphere of Paseo Aranjuez in Cochabamba. Balancing commercial efficiency with boutique prestige, it bridges high-end lifestyle retail, specialty gastronomy, and real-time ordering.

The visual style blends **Modern Clean Editorial** with **Tactile Softness**. The interface evokes architectural permanence, trust, and culinary indulgence through deep navy surfaces, luminous teal accents, and generous whitespace. Typography is structured and clear, while card surfaces and interactive elements prioritize touch ergonomics, subtle elevation, and clarity under direct sunlight or low-light indoor environments.

## Colors
The palette balances structure, brand identity, and status clarity:
- **Primary Navy (`#1E3A8A`)**: Represents structural trust, prestige, and administrative authority. Used for active navigation tabs, primary calls-to-action, high-emphasis text, and headers.
- **Secondary Teal (`#0D9488`)**: Reflects the lush, open-air garden architecture of Paseo Aranjuez. Used for lifestyle highlights, live store statuses, interactive badges, discount tags, and active filters.
- **Warm Amber (`#F59E0B`)**: Dedicated to dining table reservations, scheduled pickups, loyalty rewards, and pending order flows.
- **Status Coral / Error (`#EF4444`)**: High-contrast indicator for canceled orders, closed shops, expired vouchers, and critical errors.
- **Status Emerald / Success (`#10B981`)**: Signals approved transactions, ready-to-pickup notices, and confirmed orders.
- **Neutral Canvas (`#F8FAFC` to `#0F172A`)**: High-fidelity grays tuned to eliminate glare on mobile displays, using soft slates for borders (`#E2E8F0`) and secondary meta-text (`#64748B`).

## Typography
Plus Jakarta Sans was chosen for its contemporary geometric balance, subtle humanist touches, and legibility at compact mobile scale. 

- **Display & Headlines**: Bold, confident cuts establish clear visual anchors for mall directory zones, merchant names, and culinary categories.
- **Body & Product Content**: Strict line-height scales protect readability in multi-line dish descriptions, allergy warnings, and order receipt breakdowns.
- **Labels & Metas**: Sized and spaced specifically for high glanceability across real-time tracking badges, currency figures (BOB/Bs.), and ETA timestamps.

## Layout & Spacing
The layout model operates on an 8-point base grid system optimized for React Native touch targets and fluid responsive viewports:
- **Mobile Handheld (Primary)**: 16px horizontal margins (`margin-mobile`), 12px horizontal gutters (`gutter-mobile`) between columns in multi-column product grids, and a strict 44px minimum touch target size.
- **Tablet / Responsive Fold**: Extends to 24px margins (`margin`) and 16px gutters (`gutter`), reflowing single-column feeds into structured 2-column or 3-column discovery layouts.
- **Vertical Flow**: Micro rhythm relies on `space-xs` (4px) and `space-sm` (8px) for title-price clusters, `space-md` (16px) for item separation inside cards, and `space-xl` (32px) between merchant showcase blocks.

## Elevation & Depth
Depth conveys physical hierarchy without visual clutter, using multi-layered ambient drop shadows paired with soft borders:
- **Level 0 (Flat Canvas)**: Hex `#F8FAFC`. Background layer across screens.
- **Level 1 (Surface Cards & Merchant Tiles)**: Solid `#FFFFFF` fill with a crisp border (`1px solid #F1F5F9`) and a soft ambient shadow (`offset: 0px 2px, blur: 8px, opacity: 0.04, color: #0F172A`).
- **Level 2 (Interactive Floating Elements, Cart Bar, Sticky Headers)**: Elevated above lists with (`offset: 0px 4px, blur: 16px, opacity: 0.08, color: #1E3A8A`).
- **Level 3 (Modals, Bottom Sheets, Dine-In Floor Selector)**: Full focus overlay with (`offset: 0px 12px, blur: 32px, opacity: 0.16, color: #0F172A`) backed by a darkened scrim (`#0F172A` at 40% opacity).

## Shapes
A roundedness factor of `2` provides a polished, approachable mobile aesthetic:
- **Base Components (Inputs, Buttons, Badges)**: 12px corner radii (`rounded-md` equivalent to 0.75rem / 12px in native style sheets) to maintain structural solidity.
- **Product & Store Cards**: 16px corner radii (`rounded-lg` equivalent to 1rem / 16px) for imagery nesting and smooth container clipping.
- **Bottom Sheets & Modal Containers**: 24px top corner radii (`rounded-xl` equivalent to 1.5rem) to signify sheet pull interactions.
- **Action Pills & Status Chips**: Fully rounded pill shapes (`9999px`) for filter tags, status trackers, and floating counter bubbles.

## Components

### Buttons
- **Primary Action (Navy)**: Height 50px, background `#1E3A8A`, text `#FFFFFF`, border-radius 12px, typography `label-lg`. Pressed state scales down slightly (`transform: scale(0.98)`) and shifts background to `#172554`.
- **Secondary Action (Teal Accent)**: Height 50px, background `#0D9488`, text `#FFFFFF`, border-radius 12px, typography `label-lg`. Used for immediate order actions ("Pedir Ahora", "Reservar Mesa").
- **Ghost / Outlined**: Height 50px, border `1.5px solid #CBD5E1`, background transparent, text `#1E3A8A`.

### Cards (Merchants & Dishes)
- Encased in 16px rounded white containers (`#FFFFFF`) with 1px border (`#F1F5F9`).
- Image containers feature top-clipped 16px radii with an aspect ratio of 16:9 for restaurants and 1:1 for retail items.
- Incorporate subtle delivery/prep time badge pills floating over the top right of the media layer.

### Chips & Filter Tags
- **Default Chip**: Height 36px, background `#F1F5F9`, text `#475569`, border-radius 9999px, padding horizontal 16px.
- **Active Filter Chip**: Background `#0D9488`, text `#FFFFFF`, slight teal glow.
- **Status Chip (Reservas / En Proceso)**: Background `#FEF3C7`, text `#B45309`, border `1px solid #FDE68A`.
- **Status Chip (Listo para Retiro / Confirmado)**: Background `#D1FAE5`, text `#065F46`, border `1px solid #A7F3D0`.

### Form Inputs & Selectors
- Height 48px, background `#FFFFFF`, border `1px solid #E2E8F0`, border-radius 12px, typography `body-md`.
- Focus state activates an outline of `1.5px solid #1E3A8A` and a soft focus ring (`rgba(30, 58, 138, 0.1)`).
- Error state switches border to `#EF4444`.

### Bottom Sheets & Cart Drawers
- Anchored to the bottom screen edge with 24px top radii, featuring a centered pull handle (`36px x 4px`, color `#CBD5E1`, margin top 8px).
- Sticky bottom action container containing order subtotal breakdown and high-contrast checkout trigger.