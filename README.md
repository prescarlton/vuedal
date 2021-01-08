# vuedal
A simple, lightweight modal for Vue.js 2.x

## Installation
This package isn't on npm, so installation can be done by installing directly from this repo:

```bash
npm install git+https://github.com/prescarlton/vuedal.git
# or if you're using yarn,
yarn install git+https://github.com/prescarlton/vuedal.git
```

Next, import the component and register it w/ Vue (usually in main.js/index.js):
```javascript
import Vue from "vue";
import VueModal from "vuedal";

Vue.component("VueModal", VueModal);
```
Just like that, you're ready to roll. Check out the props list for more details.

## Using the modal
The modal is pretty simple by design, offering only a few props:

    isOpen: {
        type: Boolean,
        required: true,
    },
    onRequestClose: {
        type: Function,
        required: true
    },
    showDefaultCloseBtn: {
        type: Boolean,
        default: true
    }

- `isOpen` (required): State that signifies whether or not the modal should be shown
- `onRequestClose` (required): Method that should typically set isOpen to false; called whenever the user clicks the default close button or un-focuses the modal.
- `showDefaultCloseBtn` (optional): Determines whether or not the close button will be shown. Useful if you want to create a confirm dialog where a close button is not needed/desired.

## Styling
The modal includes styling by default, but you can customize it by accessing the modal's classes:
- `.close-btn`: default close button styling
- `.modal-overlay`: the translucent gray background that gets overlayed on all elements behind the open modal
- `.modal`: The actual modal itself
- `.modal-body`: The content of the modal


## Demo
For a full set-up of a modal, checkout `src/Demo.vue`. There's a simple button that opens a modal when clicked.