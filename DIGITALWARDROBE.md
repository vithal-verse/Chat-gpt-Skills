---
name: digital-wardrobe
description: Organize clothing photos into a private digital wardrobe and recommend outfits from the user's own items for weather, mood, occasion, place, dress code, comfort, and personal style.
---

# Digital Wardrobe

Use this skill when the user wants to create, maintain, search, or style outfits from a personal clothing catalog.

## Privacy and photo handling

- Work only with photos the user uploads or explicitly points you to. Never browse a photo library, camera roll, or unrelated folders to find clothing.
- Before keeping a photo beyond the current conversation, confirm the user wants it saved and agree on a local wardrobe folder. Explain the proposed folder if it has not been established. Do not upload wardrobe photos to external services.
- Keep originals intact. Copy approved photos into the chosen wardrobe folder; don't move, overwrite, or delete source images. For removal requests, confirm whether to remove the catalog entry, the stored copy, or both. Never delete the user's original upload.
- If permission to save is absent, analyze the provided photo for the current request only and do not create persistent files.
- Treat photos as private. Do not share them, publish them, or include them in unrelated outputs.

## Maintain the wardrobe

For a new wardrobe, establish the storage folder only after the user agrees. Keep approved image copies in that folder and a machine-readable `wardrobe.json` index alongside them. Use stable item IDs and relative photo paths so the folder can be moved. Follow [the catalog schema](references/catalog-schema.md).

When adding photos, inspect only the provided images, identify each distinct garment or accessory, and propose useful attributes. Record uncertain visual judgments as `unknown` or low confidence; ask only for details that affect usefulness, such as fit, comfort, season, or care constraints. Before saving, show a compact summary of the items and any uncertain labels for confirmation. Then copy only approved photos, append records without replacing existing entries, and update the index.

When the user edits an item, change the relevant catalog fields and preserve its ID and photo unless asked otherwise. When removing an item, make the scope clear before deleting stored files. Never infer that an item is clean, available, or suitable for a particular temperature from its photo alone.

## Recommend an outfit

Use the wardrobe index as the source of available clothing. Gather any missing details that materially affect the choice: destination or local weather, date/time, occasion or place, dress code, mood, comfort needs, and style preferences. The user can answer only what matters to them.

For current weather, use an available weather source only after obtaining the relevant location (or use one already provided for this request). If live weather is unavailable, ask for the forecast or clearly state that the recommendation is not weather-verified. Account for rain, wind, temperature range, and indoor/outdoor transitions where relevant.

Suggest a complete, wearable combination from catalog items: base/top, bottom or one-piece, suitable layer, footwear, and optional accessories. Include alternatives only when useful. Match dress code and comfort first, then mood and style; explain briefly how the pieces work together and how the outfit handles the conditions. Never claim an item is in the catalog unless it is indexed. If the wardrobe lacks a needed piece, say so and offer a practical substitute from available items; don't silently invent garments.

If details are missing, make a clearly labeled reasonable assumption or ask a concise follow-up. Do not infer body measurements, gender, identity, or personal attributes from photos. Respect stated fit, sensory, mobility, modesty, cultural, and accessibility preferences.

## Examples

- “Save these three clothing photos to my wardrobe.” → Confirm the local folder if needed, identify the items, confirm uncertain attributes, then copy and index them.
- “What should I wear in Mumbai tomorrow for a casual outdoor dinner? I want to feel relaxed.” → Check current conditions for Mumbai, then recommend a complete combination only from indexed items.
- “Remove the red jacket from my wardrobe.” → Clarify whether to remove the catalog record and stored copy; preserve the original upload.
- “Add this photo, but don't save it.” → Use it only for this conversation and leave the persistent catalog unchanged.
