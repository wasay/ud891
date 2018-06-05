Lesson 6: Style

Content 2: Working with focus styles

    WebAIM checklist items:
    
    2.4.7: http://webaim.org/standards/wcag/checklist#sc2.4.7
    
    :focus pseudo-class
    
    outline CSS property
    
    :hover pseudo-class
    
    ::before pseudo-element
    
    :focus {
        outline: 1px dotted #FFF;
    }
    
    // DO NOT implement such non-outline
    :focus {
        outline 0; 
    }
    
    button:hover {
        background: #E91E63;
        color: #FFFFFF;
        text-decoration: underline;
    }
    
    ////////////////////
    
    button:hover,
    button:focus {
        background: #E91E63;
        color: #FFFFFF;
        text-decoration: underline;
    }
    
    // box-shadow for focus is better implementation that the changing of color
    button:focus {
        outline: 0;
        box-shadow: 0 0 8px 3px rgba(255, 255, 255, 0.8);
    }
        
     ////////////////////
     
     .radio:focus {
        outline: 0;
     }
     
     .radio:focus::before {
        box-shadow: 0 0 1px 2px #5B9DD9;
     }
     
     ////////////////////
     
Content 3: Quiz: Write your own focus styles

    This exercise can be found in the folder lesson6-styling/01-focus-styles within 
    this course's GitHub Repository.
    
    The buttons on this page don’t currently have focus styles, making them pretty much 
    useless to a keyboard user. With your new CSS knowledge, try using the :focus 
    pseudo-class to give these buttons interesting focus states.
    

Content 4: Input Modality
    
    :moz-focusring pseudo-class
    https://developer.mozilla.org/en-US/docs/Web/CSS/:-moz-focusring
    
    Proposing CSS input modality article
    http://radar.oreilly.com/2015/08/proposing-css-input-modailty.html
    
    Input modality shim
    https://github.com/alice/modality
    
        @media (modality: keyboard) {
         :focus {
            outline: -webkit-focus-ring-color auto 5px; /* or default UA style of your choosing */
          }
        }
        
        @media not (modality: keyboard) {
         :focus {
            outline: none;
          }
        }
        
        ////////////////////////
    
        body([modality=keyboard]) :focus {
            outline: -webkit-focus-ring-color auto 5px; /* or default UA style of your choosing */
        }
        
        body:not([modality=keyboard]) :focus {
            outline: none;
        }
        
Content 5: Styling with aria

    https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors

    .toggle[aria-pressed="true"] {
        // transition to
        // pressed state
    }
    
Content 8: Responsive design for multi-device

    WebAIM checklist items:
    
    1.4.4: http://webaim.org/standards/wcag/checklist#sc1.4.4
    Udacity course on Responsive Web Design Fundamentals
    
    Responsive web design basics on Web Fundamentals
    
    Material Design Accessibility recommendations for touch targets
    
    Author's Note: On older browsers (particularly Mobile Safari) developers would 
    add user-scaleable=no because it would disable the 350ms click delay in that browser. 
    As of Safari 9.1 this is no longer the case, and using width=device-width in your 
    viewport will handle removing that click delay.
    
    
    tounch target
        
        48 db (device independent pixcels) minimum touch target
        
        if suppose image is 24 px, add additional padding to make it close to 48 pixcels
        
        32 px margin to avoid conflict with other touch items
        it should be both horizontal and verticlelly spaced
        
        
Content 14: Meeting Contrast Requirements

    WebAIM checklist items:
    
    1.4.3: http://webaim.org/standards/wcag/checklist#sc1.4.3
    1.4.6: http://webaim.org/standards/wcag/checklist#sc1.4.6
    Chrome Accessibility Developer Tools
    
    Text Contrast
    
        15.9:
        Color: #222222
        Background: #FFFFFF
        
        5.7:1
        Color: #666666
        Background: #FFFFFF
        
        3.5:1
        Color: #888888
        Background: #FFFFFF
        
        1.6:1
        Color: #CCCCCC
        Background: #FFFFFF
    
    Minimum contrast: 1.4.3
    
        4.5:1
        
    Chrome Dev Tools: Accessibility Audit
    
        Contrast ratio (suggestion)
            
            AA level (4.52)
            AAA level (7.04)
            
Content 16: Don't convey info with color alone

    WebAIM checklist items:
    
    1.4.1: http://webaim.org/standards/wcag/checklist#sc1.4.1
    
    NoCoffee Chrome extension
    https://chrome.google.com/webstore/detail/nocoffee/jjeeggmbnhckmgdhmgdckeigabjfbddl?hl=en-US
    
    For more information on color blindness, check out the Colour Blind Awareness site.
    http://www.colourblindawareness.org/colour-blindness/
    
    
Content 17: High Contrast Mode

You can follow this link to get the Chrome High Contrast extension. Try it out on one of your 
sites to verify that everything works well for low vision users.

Author's Note: The example that shows a "subtle background color" in the navbar really does have 
a background color, we promise! It doesn't show up very well on YouTube, which I guess proves 
the point that just because a subtle color might look good on your screen doesn't always mean 
it'll look good on someone else's monitor.


Knowing when to apply rules:

    How frequently is this piece of UI used?
    
    How badly does this accessibility issue affect your users?
    
    How expendisve is it going to be to fix?

