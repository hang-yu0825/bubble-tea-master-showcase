# Representative Technical Snippets

These examples are rewritten pseudocode. They communicate engineering decisions without copying production scripts.

## 1. Composable rule evaluation

```text
active_rules = parse_rule_list(level.rule)

on_customer_started(customer):
    if MEMORY in active_rules:
        schedule_order_hide(customer, delay)
    if RUSH in active_rules:
        customer.patience *= rush_factor

on_pause():
    cancel_pending_hide()
    remember_hide_time_remaining()
```

**Problem:** multiple level modifiers need to work alone or together without duplicating the gameplay scene.  
**Why it is useful:** it demonstrates composition, lifecycle handling, and protection against stale asynchronous timers.  
**Concepts:** rule sets, state isolation, cancellation tokens/generations, pause/resume logic.

## 2. Data-driven validation and scoring

```text
result = compare(expected_order, player_drink, enabled_components)

if result == PERFECT:
    score = base + speed_bonus
    score *= combo_multiplier
elif result == PARTIAL:
    score = apply_attempt_penalty(base, attempts)
else:
    reset_combo_and_apply_rule_consequence()
```

**Problem:** correctness changes as components unlock, and score must reflect speed, attempts, combos, and special rules.  
**Why it is useful:** it shows separation between validation and reward policy.  
**Concepts:** domain modelling, pure comparison logic, progressive feature flags, scoring policy.

## 3. Separate persistent and session saves

```text
profile_save = progression + inventory + settings + achievements
run_save = endless_level + current_score + lives + temporary_boosts

save_profile_when_progress_changes()
save_run_only_for_resumable_endless_play()
clear_run_save_after_completion()
```

**Problem:** durable progression and an interrupted run have different lifetimes.  
**Why it is useful:** it prevents transient state from corrupting long-term data and makes resume behaviour explicit.  
**Concepts:** persistence boundaries, schema ownership, lifecycle-based cleanup.

