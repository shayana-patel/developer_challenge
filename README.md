# developer_challenge
Coding a well-structured, user-friendly UI for scale, with  minimal help from UI libraries/frameworks

# Getting started
<code>npm i</code>
<code>npm run dev</code>

# The Process
The layout was created on a single HTML page using semantic HTML. Styling was done using SCSS. I used node-sass (npm package) to complie SCSS to CSS.

I created wire-frames to plan the layout and figure out the elements I would need.

I used a mixture of grid and flex display for various elements. For the header I used flex display to make it easier for changing flex direction at different viewpoints. For the section element I used grid display. This design decision was made to make it easier to design the page layout without having to use floats and positioning to get elements into the desired layout.

I then used flex display on the section (grid-container) element to make the layout responsive at different viewports. By doing so it meant the content of the grid-container was not squished or cut off on various screen sizes.
