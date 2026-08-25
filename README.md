### Personalized Meal & Diet Subscription Manager

A clinical dietary subscription service that generates weekly menus based on patient metabolic constraints such as allergies, diabetic limits, and calorie goals, and tracks daily delivery fulfillment.

**Target Stakeholders / Actors:** Subscriber, Dietitian.

## 2. Functional Requirements

The project contains exactly five functional requirements:

1. **FR-001:** Generate weekly meal plans according to macro-nutrient constraints and allergen exclusions.
2. **FR-002:** Allow the subscriber to manage their dietary profile.
3. **FR-003:** Allow the dietitian to review and approve generated meal plans.
4. **FR-004:** Allow the subscriber to pause, skip, or reschedule the subscription.
5. **FR-005:** Record and display daily meal delivery fulfillment status.



## 3. Non-Functional Requirements

The project contains exactly two non-functional requirements:

1. **NFR-001:** Support subscription schedule modifications up to 12 hours before dispatch.
2. **NFR-002:** Protect subscriber dietary information using authenticated access and role-based authorization.


## 4. Actors

### Subscriber
Manages the dietary profile, views meal plans, manages the subscription, and checks delivery status.

### Dietitian
Reviews and approves generated meal plans.


## 5. Primary Use Cases

The UML model contains five primary use cases:

- **UC-01:** Manage Dietary Profile
- **UC-02:** Generate Weekly Meal Plan
- **UC-03:** Review & Approve Meal Plan
- **UC-04:** Manage Subscription
- **UC-05:** Track Delivery Fulfillment

The UML diagram also shows the required `«include»` and `«extend»` relationships.



## 6. Use-Case Flow

### UC-02 – Generate Weekly Meal Plan

**Primary Actor:** Subscriber  
**Supporting Actor:** Dietitian

### Preconditions

- Subscriber is authenticated.
- Subscriber has a saved dietary profile.
- The subscription is active for the requested week.

### Postconditions

- A weekly meal plan is generated according to the subscriber's constraints.
- The plan is saved for dietitian review.
- No excluded allergen is included in the generated menu.

### Main Success Scenario

1. Subscriber selects Generate Weekly Meal Plan.
2. System retrieves the dietary profile and subscription details.
3. System validates dietary constraints and allergen exclusions.
4. System generates a weekly menu within the configured calorie and macro-nutrient limits.
5. System checks the menu for excluded allergens and constraint violations.
6. System saves the meal plan as Pending Dietitian Review.
7. System notifies the dietitian.
8. Dietitian reviews and approves the plan.
9. System changes the plan status to Approved and makes it available for the subscription.

### Alternate Flow

**Constraint Violation**

If the generated menu violates a dietary constraint or contains an excluded ingredient:

1. System rejects the generated menu.
2. System identifies the violated constraint or excluded ingredient.
3. System regenerates the menu using valid constraints.
4. If no compliant plan can be generated, the system flags the case for dietitian intervention.
