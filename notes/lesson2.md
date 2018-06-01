Lesson 2: Focus

Content 1. Introduction to Focus

    WebAIM checklist items:
    
    2.1.1: http://webaim.org/standards/wcag/checklist#sc2.1.1
    
    Focus means a control on the screen when it receives input
    from the clipboard or the keyboard when you paste
    
Content 2: What is Focus?
    Move focus around the page using your keyboard:
    
    TAB will move focus forward
    SHIFT - TAB will move focus backwards
    Arrow keys can be used to navigate inside of a component
    
    https://www.w3.org/TR/html5/editing.html#focus-management
    
Content 3: Quiz: Experiencing Focus
    Try out our flight booking form using only your keyboard. 
    You'll need to search for a ticket that matches the following criteria:
    http://udacity.github.io/ud891/lesson2-focus/01-basic-form/
    
    The ticket should...
    
    Be a round trip
    to Melbourne
    leaving on 10/12/2017
    returning on 10/23/2017
    window seat
    and you DO NOT want to receive promotional offers 😀
    If you've filled out the form correctly then pressing the Search button 
    should give you a notification that you've passed.
    
    Remember:
    
    TAB will move focus forward to the next element
    SHIFT - TAB will move focus backwards to the previous element
    Arrow Keys can be used to move focus within an element
    
Content 4: DOM Order Matters
    WebAIM checklist items:
    
    1.3.2: http://webaim.org/standards/wcag/checklist#sc1.3.2
    
    1.3.2 Meaningful Sequence
    The reading and navigation order (determined by code order) is logical and intuitive.
    
Content 5: Quiz: Fixing DOM Order
    This exercise can be found in the folder lesson2-focus/02-dom-order within this 
    course's GitHub Repository.
    
    Tabbing around the page should reveal a mixed up tab order. Read through the index.html 
    and see if there are any places where elements may be in the wrong order. If something 
    looks out of place see if you can fix it so the tab order works as expected. If you get 
    stuck you can refer to the solution directory.
    
Content 6: Using Tabindex
    tabindex on MDN
    https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex

    https://www.w3.org/TR/html5/editing.html#sequential-focus-navigation-and-the-tabindex-attribute
    
Content 10: Quiz: Manage Focus Yourself
    You can find this example in the lesson2-focus/03-managing-focus directory within this 
    course's GitHub Repository.
    
    To run this example you'll need to use a local server. The easiest way to do so is to 
    use the Web Server for Chrome extension.
    
    Make sure your settings look like this:
    
    Chrome 200 OK settings
    
    Under the heading that says "Web Server URL(s)" click the first link to preview the 
    app on your local server.
    
    Take a look at the scripts/main.js file to figure out how the route is updated and to 
    determine when you would need to step in and manage focus.
    
    
Content 11: Skip Links
    You can read more about skip links in this article on the Web AIM site.
    
    https://developers.google.com/web/updates/2016/03/focus-start-point?hl=en
    
Content 12: Focus
    The ARIA Authoring Practices doc (or "ARIA Design Patterns doc") is a great resource for 
    figuring out what kind of keyboard support your complex components should implement.
    
    There are currently two versions:
    
    WAI-ARIA Authoring Practices 1.0
    WAI-ARIA Authoring Practices 1.1 (Newer working draft)
    I personally prefer the 1.1 version because the layout is a bit easier to navigate and it 
    includes a few fixes currently missing from the 1.0 version.
    
    Roving Focus:
        Set tab index for all the children to -1 and setting the tabindex of first element 0
    
Content 13:
    Take a look at the ARIA Authoring Best Practices guide to read more about the Radio pattern. 
    I've linked to both versions so you can choose whichever one you prefer. Both patterns are 
    nearly identical but do note that the 1.0 version is called "Radio Button" and the 1.1 
    version is called "Radio Group".
    
    ARIA Authoring Best Practices 1.0 (Radio Button)
    ARIA Authoring Best Practices 1.1 (Radio Group)
    https://www.w3.org/TR/wai-aria-practices/#aria_ex

Content 14: Quiz: Implementing Keyboard Event Listener
    You can find the files for this example in the lesson2-focus/05-radio-group directory within 
    this course's GitHub Repository.
    
    Using the ARIA Authoring Best Practices doc (either version 1.0 or version 1.1) find the radio 
    pattern and implement support for the Down Arrow and Right Arrow pattern using the 
    "roving focus" technique. I should point out that you'll also sometimes see this referred to 
    as "roving tabindex."
    
    Note: The 1.0 version of the doc refers to this as a "Radio Button" whereas the 1.1 version 
    of the doc refers to this as a "Radio Group".
    
    You'll want to work in the radiogroup.js file to implement your keyboarding support.
    
Content 15: Offscreen content
    To find your missing focus you can type the following into your console:
    
    document.activeElement
    
    Read more about Document.activeElement on MDN
    
    Another tool you can use is the Chrome Accessibility Developer Tools Extension. This extension 
    will not only add an Accessibility Properties panel to your Elements inspector, but it also adds 
    an Accessibility option to the audits panel. Using this option you can quickly find accessibility 
    issues in your page which you might have otherwise missed.
    
    https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?hl=en
    
Content 17: Modals and Keyboard Traps

    WebAIM checklist items:    
    2.1.2: http://webaim.org/standards/wcag/checklist#sc2.1.2
    
    <dialog> on MDN
    https://github.com/GoogleChrome/dialog-polyfill