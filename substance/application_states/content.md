# Application State Analysis

- an application is controlled by a hierarchy of controllers
- each controller has a specific state


## Application state

- the states of all controllers in the hierarchy define the application state
- each application state is represented by a unique URL

## Controller state

- each controller has a denoted *START* state
- *START* is vanilla, i.e., no initialization has been done; it has no dependencies
- a transition matrix defines functions that are executed on a transition between two states
- the minimal transition matrix defines transitions from *START* to each state and vice versa.
    - e.g., a transition `A->B` can be achieved by `A->START->B`
- state transition should be safe. I.e., prepare a new state first and switch only if this has been successful.

## Hierarchical states

- a state on a higher level can have child controllers
- entering such a state at first leaves the child controller in *START* state
    - after that the transition is delegated to the child controller (initialize)
- leaving a higher level state implicates a transition to *START* state of all child controllers (cleanup)


# How to evolve an Application State Machine

## State identification

- a state is defined by a set of state variables
- a different set of variables form a different state
- find simple string identifiers for each state
- specify pre-conditions (requirements)
- specify the transition (post-conditions = state variables)

## Primitive transitions

For each state `S` define:

- a transition `START->S` (initialization)
- and a transition `S->START` (clean up)

## Optimization

- Find common functions and extract them as helpers
- Add shortcut transitions between states.
  It might not be necessary to do a full clean up (as done with the canonical transition passing *START*).
  Instead a reparametrization might be enough.
