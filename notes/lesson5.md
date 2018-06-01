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
        