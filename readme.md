# workTips

## Here are my job tips where I will record some small tricks and work experiences. Currently, the main technologies I use are JavaScript, Vue, React, React Native, as well as some component libraries such as ElementUI and Ant Design, and some CSS tips.

## H5 Use background-image on input[type=range]::-webkit-slider-thumb for styling has whitespace problem

Scaling with transform can address the issue of background image causing whitespace on both sides of H5 input[type=range]::-webkit-slider-thumb. Avoid using margin-left and margin-right for input[type=range]::-webkit-slider-thumb as only margin-left is effective. 
![image](https://github.com/bituo123/workTips/assets/60815483/c58f3b4c-5920-4699-bdde-71918818cbb3)
![image](https://github.com/bituo123/workTips/assets/60815483/e5b3097a-f3f2-4b82-820e-987f75d9438b)

## Implementing the addition of rows and columns to Revogrid using Vue 2. Due to the lack of real-time updates in the data component in version 2, the array needs to be reassigned after each manipulation.

https://codesandbox.io/p/sandbox/revogrid-vuecomponent-forked-2ck9nh?file=%2Fsrc%2FApp.vue%3A13%2C32-13%2C37

In V2, when passing between parent and child components, directly bind the array in a for loop, and updating can be achieved through push.
