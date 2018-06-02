Lesson 5: ARIA

Content 1: Intro to Semantics: ARIA

    DOM Order
    Focus
    Keyboard
    Semantics
    
Content 2: Why ARIA

    ARIA 1.0 spec: https://www.w3.org/TR/wai-aria/
    
    ARIA 1.1 spec: https://www.w3.org/TR/wai-aria-1.1/
    
    You can play with this example yourself, if you want!
    
    To use a div as a checkbox item add role and aria-checked attribute
    Aria attributes always need to have explicity values.
        
        HTML        
            <div role="checkbox" aria-checked="true">
        
        JavaScript
            
            (function() {
              'use strict';
            
              /** Define values for keycodes */
              var VK_ENTER      = 13;
              var VK_SPACE      = 32;
              var VK_LEFT       = 37;
              var VK_UP         = 38;
              var VK_RIGHT      = 39;
              var VK_DOWN       = 40;
            
              /** Helper function to convert NodeLists to Arrays */
              function slice(nodes) {
                return Array.prototype.slice.call(nodes);
              }
            
              function Checkbox(el) {
                this.el = el;
            
                this.el.addEventListener('keydown', this.handleKeyDown.bind(this));
                this.el.addEventListener('click', this.toggle.bind(this));
            
                // Initialize role and aria-checked state.
                this.el.setAttribute('role', 'checkbox');
                if (this.el.hasAttribute('checked')) {
                  this.el.setAttribute('aria-checked', 'true');
                } else {
                  this.el.setAttribute('aria-checked', 'false');
                }
              }
            
              Checkbox.prototype.handleKeyDown = function(e) {
                switch(e.keyCode) {
                  case VK_ENTER:
                  case VK_SPACE: {
                    this.toggle();
                    break;
                  }
                }
              };
            
              Checkbox.prototype.toggle = function() {
                if (this.el.hasAttribute('checked')) {
                  this.el.removeAttribute('checked');
            
                  // Keep checked attribute and aria-checked in sync.
                  this.el.setAttribute('aria-checked', 'false');
                } else {
                  this.el.setAttribute('checked', '');
            
                  // Keep checked attribute and aria-checked in sync.
                  this.el.setAttribute('aria-checked', 'true');
                }
              };
            
              var checkboxes = slice(document.querySelectorAll('.checkbox'));
              for (var checkbox of checkboxes)
                checkbox.logic = new Checkbox(checkbox);
            
            }());



Content 4: What can ARIA do for you?

    Add semantics
        <div role="checkbox" aria-checked="true">
            Receive promotional offers
        </div>
    
    
    Modify semantics
        Convert buttont to on/off switch
            <button role="switch" aria-checked="true"
                class="toggle">Enable</button>
                
                
        Tree UI pattern
            <ul role="tree">
                <li role="treeitem" aria-expanded="true">
                    Accessibility course
                </li>
                <ul role="group">
                    <li role="treeitem" aria-expanded="false">
                        Introduction
                    </li>
                    <li role="treeitem" aria-expanded="false">
                        Focus
                    </li>
                </ul>
            </ul>
            
        
        Extra labels and description
            <button class="glyph"
                aria-label="Filter"
                <div class="menu-glyph"></div>
            </button>
            
        
        Relationships
            <button aria-expanded="false"
                    aria-controls="advanced-settings">
                <h2>Advanced settings</h2>
            </button>
            <div id="advanced-settings">
                <label><input type="checkbox" Offer to...</label>
                <label><input type="checkbox" Send usage... </label>
            </div>
            
            
        Alerts
            Voice comand may interupt the user from what ever they are doing
            
            <div role="alert">Display text</div>
            
            
Content 5: Roleplaying

    ARIA 1.0 roles: https://www.w3.org/TR/wai-aria-1.0/#roles
    
    ARIA 1.1 roles (draft): https://www.w3.org/TR/wai-aria-1.1/#roles
    
    ARIA 1.1 practices guide (draft): https://www.w3.org/TR/wai-aria-practices-1.1/

    always add role and tabindex on same element
        <div tabindex="0"
            class="checkbox" checked
            role="checkbox" aria-checked="true">
            Tim-Tams
        </div>
        
        
Content 6: Quiz Custom radio button group

    HTML:
        <h3>Drink Options</h3>
        
        <ul id="group1" class="radiogroup">
            <li class="radio">
              Water
            </li>
            <li class="radio">
              Tea
            </li>
            <li class="radio">
              Coffee
            </li>
            <li class="radio">
              Cola
            </li>
            <li class="radio">
              Ginger Ale
            </li>
        </ul>
    
    
    Javascript:
        (function() {
          'use strict';
        
          // Define values for keycodes
          var VK_ENTER      = 13;
          var VK_SPACE      = 32;
          var VK_LEFT       = 37;
          var VK_UP         = 38;
          var VK_RIGHT      = 39;
          var VK_DOWN       = 40;
        
          // Helper function to convert NodeLists to Arrays
          function slice(nodes) {
            return Array.prototype.slice.call(nodes);
          }
        
          function RadioGroup(id) {
            this.el = document.querySelector(id);
            this.buttons = slice(this.el.querySelectorAll('.radio'));
            this.focusedIdx = 0;
            this.focusedButton = this.buttons[this.focusedIdx];
        
            this.el.addEventListener('keydown', this.handleKeyDown.bind(this));
            this.el.addEventListener('click', this.handleClick.bind(this));
        
            // Set ARIA role for the radio group.
            this.el.setAttribute('role', 'radiogroup');
        
            var firstButton = true;
            for (var button of this.buttons) {
              if (firstButton) {
                button.tabIndex = "0";
                firstButton = false;
              } else {
                button.tabIndex = "-1";
              }
        
              button.setAttribute('role', 'radio');
            }
          }
        
          RadioGroup.prototype.handleKeyDown = function(e) {
            switch(e.keyCode) {
        
              case VK_UP:
              case VK_LEFT: {
        
                e.preventDefault();
        
                this.focusedIdx--;
                if (this.focusedIdx < 0)
                  this.focusedIdx = this.focusedIdx + this.buttons.length;
        
                break;
              }
        
              case VK_DOWN:
              case VK_RIGHT: {
        
                e.preventDefault();
        
                this.focusedIdx = (this.focusedIdx + 1) % this.buttons.length;
        
                break;
              }
        
            case VK_SPACE:
                var focusedButton = e.target;
                var idx = this.buttons.indexOf(focusedButton);
                if (idx < 0)
                  return;
                this.focusedIdx = idx;
                break;
        
              default:
                return;
            }
        
            this.changeFocus();
          };
        
          RadioGroup.prototype.handleClick = function(e) {
            var button = e.target;
            var idx = this.buttons.indexOf(button);
            if (idx < 0)
              return;
            this.focusedIdx = idx;
            this.changeFocus();
          };
        
          RadioGroup.prototype.changeFocus = function() {
            // Set the old button to tabindex -1
            this.focusedButton.tabIndex = -1;
            this.focusedButton.removeAttribute('checked');
            this.focusedButton.setAttribute('aria-checked', 'false');
        
            // Set the new button to tabindex 0 and focus it
            this.focusedButton = this.buttons[this.focusedIdx];
            this.focusedButton.tabIndex = 0;
            this.focusedButton.focus();
            this.focusedButton.setAttribute('checked', '');
            this.focusedButton.setAttribute('aria-checked', 'true');
          };
        
          var group1 = new RadioGroup('#group1');
        
        }());

Content 7: More ways to Label

    aria-label
    
        <button aria-label="menu"
                class="hamburger">
        </button>
    
    aria-labelledby
    
        <span id="rg-label">
            Drink Options
        </span>
        <div role="radiogroup"
                aria-labelledby="rg-label">
             ...
        </div>
        
        1.
        <div role="radio" aria-labelledby="lb01"></div>
        <span id="lb01">Coffee</span>
        
        2.
        <input type="radio" id="rb01">
        <label for="rb01">Coffee</label>
        
    
    aria-describedby

    Hints:
    
    In each case, provide the label for the first, or outermost, element.
    If the element would be hidden from the accessibility tree, choose "No label".
    HTML labelling techniques, and ARIA roles and attributes, must be used 
    correctly in order to be effective.
    
Content 10. Default Semantics and Landmarks
    
    ARIA in HTML spec, including guidance on what ARIA roles may and may not be 
    used with which HTML elements: 
    https://www.w3.org/TR/html-aria/
    
    
    roles
        role="banner"
        role="navigation"
        role="main" 
            [in case if it's not supported by browser] 
            <main role="main">
        role="complementary"
        role="search"
        role="dialog"
        role="contentinfo"
        
Content 11: ARIA Relationships

    ARIA 1.0 relationship attributes: 
    https://www.w3.org/TR/wai-aria/states_and_properties#attrs_relationships
    
    ARIA 1.1 relationship attributes: 
    https://www.w3.org/TR/wai-aria-1.1/#attrs_relationships

    aria-owns
        <div role="menu">
            <div role="menuitem"
                aria-haspopup="true">
               New
            </div>
            <div aria-owns="submenu">
            </div>
            <!-- more items... -->
        </div> <!-- menu -->
        <div role="menu" id="submenu">
            <div role="menuitem">
                Document
            </div>
            <!-- more items... -->
        </div> <!-- submenu -->

    
    aria-activedescendants
        <div role="listbox" tabindex="0"
            aria-activedescendant="i7">
            <!-- ... -->
            <div role="option" id="i5">Item 5</div>
            <div role="option" id="i6">Item 6</div>
            <div role="option" id="i7">Item 7</div>
            <div role="option" id="i8">Item 8</div>
            <!-- ... -->
        </div> <!-- listbox -->
            
    
    aria-describedby
        <label for="pw"Password:</label>
        <input type="password" id="pw"
            aria-describedby="pw-help">
        <div id="pw-help" hidden>
            Password must be at least 12 characters
        </div>
        
    
    aria-posinset and aria-setsize
        <div role="listbox">
            <div role="option"
                aria-posinet="857"
                aria-setsize="1000">Item 857</div>
            <div role="option"
                aria-posinset="858"
                aria-setsize="1000">Item 858</div>
            <!-- items 859-862 -->
        </div> <!-- listbox -->
        
        
Content 13. Hidden In Plain Sight

    For more information on screen reader-only text, check out WebAIM's article on "invisible content".
    
    <button style="visibility: hidden">
    
    <div style="display: none">
    
    <span hidden>
    
    
    .screenreader
    {
        position: absolute;
        left: 10000px;
        width: 1px;
        height: 1px;
        overflow: hidden;
    }
    
    <div class="slide"
        aria-hidden="true">
        Sales Targets
    </div>
    
    
Content 14: Quiz: Name that element round 2

    Hints:
    
    In each case, provide the label for the first, or outermost, element.
    If the element would be hidden from the accessibility tree, choose "No label".
    ARIA roles and attributes must be used correctly in order to be effective.
    
    Relevant information:
    
    aria-hidden definition
    HTML5 hidden definition
        Discussion of the difference between aria-hidden and hidden
    aria-labelledby definition
        Recall that aria-labelledby may refer to elements otherwise hidden from the accessibility tree.
    treeitem role
    button role
    checkbox role
    

Content 16: Introducing ARIA Live

    Check out the number input demo yourself, if you like.
    http://udacity.github.io/ud891/lesson5-semantics-aria/19-aria-live/

    <div class="alertbar"
        aria-live="assertive">
      Could not connect!
    </div>
    
    http://heydonworks.com/practical_aria_examples/
    
    1. Accessible input tooltips with no javascript
        <form action="">
          <fieldset>
            <legend>Login form</legend>
            <div>
              <label for="username">Your username</label>
              <input type="text" id="username" aria-describedby="username-tip" required />
              <div role="tooltip" id="username-tip">Your username is your email address</div>
            </div>
            <div>
              <label for="password">Your password</label>
              <input type="text" id="password" aria-describedby="password-tip" required />
              <div role="tooltip" id="password-tip">Was emailed to you when you signed up</div>
            </div>
          </fieldset>
        </form>
        
        input:focus + [role="tooltip"] {
            display: block;
            position: absolute;
            top: 100%;
        }
    
    
    2. Button controlled input with live feedback
        <form action="">
          <fieldset>
            <legend>Add or subtract ten</legend>
            <div>
              <label for="number">Current value</label>
              <input type="text" role="alert" aria-live="assertive" readonly value="0" id="number" />
              <button type="button" title="add 10" aria-controls="number">Add</button>
              <button type="button" title="subtract 10" aria-controls="number">Subtract</button>
            </div>
          </fieldset>
        </form>
    
    3. Progressive collapsibles
        <h3>
           <button aria-expanded="false" aria-controls="collapsible-0">What is this all about?</button>
        </h3>
        <div id="collapsible-0" aria-hidden="true">
           <p>Lorem ipsum with a <a href="http://example.com">link thrown in</a> etc.</p>
           <p>etc.</p>
        </div>
        
        
    aria-atomic
        <span aria-labelledby="birthdayLbl"
            aria-live="polite"
            aria-atomic="true">
            
            <input type="number" id="day" value="18">
            <input type="number" id="month" value="10">
            <input type="number" id="year" value="1983">
        </span>
        
        
    aria-relevant="additions"
    
        <div aria-live="polite"
            aria-relevant="additions"
            class="chat-history">
            
            <div class="chat-bubble left">
                <div class="offscreen">
                    Cathy says
                </div>
                Sure!
            </div>
        </div>
        
        
    aria-relevant="text"
    
        <div class="alertbar"
            aria-live="assertive"
            aria-atomic="true"
            aria-relevant="text">
            Could not connect!
        </div>
        
        
    aria-busy
    
        <div aria-live="polite"
            aria-busy="true"
            class="chat-history">
            
            <div class="chat-bubble left">
                <div class="offscreen">
                    Cathy says
                </div>
                Sure!
            </div>
        </div>