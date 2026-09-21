# Gameplay Flow

## Player loop

1. Choose level mode or an unlocked endless variant.
2. In level mode, choose a chapter and level; optionally allocate consumable items.
3. Read the customer's required cup, tea, sweetness, ice, and toppings.
4. Assemble the drink through touch controls and submit it.
5. The validator classifies the result and the game applies score, combo, attempt, life, and rule effects.
6. Continue until the level goal is met or the run ends through time/life conditions.
7. Show stars, score, rewards, unlocks, or endless results, then persist relevant progress.

## Rule effects confirmed in source

| Rule | Behaviour |
|---|---|
| Memory | Hides the order after a delay and supports a controlled reveal interaction |
| Rush | Reduces patience and increases scoring pressure/reward |
| Reverse | Reverses relevant option ordering |
| No reset | Prevents rebuilding the current drink from scratch |
| VIP | Treats partially correct submissions more strictly and applies life consequences |
| Timed | Uses an overall level timer while customer patience is paused |

## Progression

The production data defines 20 chapters with five levels each. New ingredients and complexity enter over time. Stars unlock chapters, while specific progress gates endless content and variants. Separate achievement, milestone, daily-reward, shop, and customisation loops provide longer-term goals.

