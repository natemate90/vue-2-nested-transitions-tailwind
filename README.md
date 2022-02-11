# Nested Transitions with Vue 2 and Tailwind CSS
Example how orchestrated (nested) transitions can be used without any external libraries in Vue 2. 
Headless UI is only available for Vue 3 but we want this now ;-) 

## enter-active-class
- class that is used as long as the transition is active
- the transition property, i.e. `transition-all`, `transition-colors` etc. 
- `transform` class when necessary, i.e. when a scale or translate class is used.
- duration class, i.e. `duration-300` = 300ms
- easing class, i.e. `ease-out`

## enter-class (will be "enter-from-class" in Vue 3)
- specific properties to start the transition from, i.e. color, scale, translate, opacity etc.

## enter-to-class
- specific properties to end the transition with, i.e. color, scale, translate, opacity etc.

same logic as above counts for appear, leave

## @before-enter

This makes orchestrating the second (nested) transition possible (without any external helpers such as Headless UI).
When before-enter is used, both transitions start at the same time.
You could add a delay class to the nested transition or alternatively, use the `@after-enter` hook


# Resources

1. https://v2.vuejs.org/v2/guide/transitions.html
2. https://vuejs.org/guide/built-ins/transition.html
3. https://medium.com/@Taha_Shashtari/how-to-apply-nested-transitions-in-vue-d3a9fe1e1c98
