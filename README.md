# Scripting Lesson 7 Demo Starter

Run local development using the following:

```
npm install
npm start
```

## Instructions

### Basic Event Listeners

Practice creating event listeners that simply log a message when the event occurs:

1. Listen for click event on `#intro`.
2. Listen for click event on `li`.
3. Listen for click event on `.btn-add`. 

### Responding to Events

Now let's do a little more in response to click events:

1. Listen for a click even on `#info p`. When such an event occurs call `.hide()` on that element.
2. Listen for a click event on `.list-group-item`. When such an event occurs, toggle its class `active` on or off.
3. Listen for a click event on `.btn-add`. When such an event occurs traverse to the closest `.panel` and add a class of `panel-info` to it. Also remove the class of `panel-primary`.

### Making it Practical

Let's combine a few other skills to build something more practical. Let's set up some event listeners that allow us to remove items from the lists here. 

First, let's use jQuery to add the delete buttons to each of our list group items. 

1. Enter the following code inside the DRE:

    ```js
    $(".list-group-item").each(function(i,o){
        var $btn = $("<i>")
            .addClass("glyphicon")
            .addClass("glyphicon-trash")
            .addClass("pull-right");
        $(o).append($btn);
    });
    ```

    This is a loop that we'll learn about later in the course. We select all the `.list-group-items` and then add a button inside each one.
  
Check out the results in the browser. You should see "trash" icons inside and on the right of each list item. Now we'll add listeners and handlers to remove an item after it has been clicked.

2. After this code add a new listener that listens for clicks on `.glyphicon-trash` inside of `.list-group-item`s. Log a confirmation message in response.

3. Replace the logged message with a new variable `$btn` that is assigned the current event's target as a jQuery object.

4. Traverse form `$btn` to the closest `.list-group-item` and store it in a new variable called `$item`. 

5. Use `.remove()` to delete `$item` from the DOM.

Test the results and you should see each button you click instantly disappear. Mission accomplished.

On the other hand, this is kind of drastic. Uses might accidentally click the trash button and end up instantly deleting the item. We can help them out by double-checking that they really do want to delete before actually removing the item. 

To do this, we'll make use of the Bootstrap Modal that we have set up in this document ,the `#modal-confirm-delete`. Find it in the source code and note that it is hidden by default. with Bootstrap's JavaScript library, we can turn on a modal by called `.modal("show")`.

6. Comment out the line you added in step 5 above for now. Right above it select `#modal-confirm-delete` and assign it to a new variable called `$modal`. 

7. Directly below this enter `$modal.modal("show");`

Check the results in the browser. This should lead to a modal window appearing. YOu can click on either button and the modal will then disappear. But the item will not be removed because we commented out the code that would remove it. Let's get that back in, but only after the user confirms to delete the item.

8. Directly below this add a new event listener that listens for click events on `.btn-confirm`, which is the button inside the modal that the user will click if they indeed want to delete the item.

9. Inside this event listener enter `$modal.modal("hide");` to ensure the modal disappears after this button is pressed.

10. Finally, move your remove item code you created in step 5 inside this listener, right below the last code you entered in step 9.

THere you have it. We used events to intelligently help the user delete an item and guarded them from accidentally deleting it.
