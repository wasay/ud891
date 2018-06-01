Lesson 4: Navigating Content

Content 1: Semantics - Navigating Content

Content 2: Navigating with a screen reader
    Shortcuts mentioned:
    
    CMD+F5 to turn on VoiceOver on OS X
    Normal keyboard operation (TAB, Shift+TAB, arrow keys etc.) work as normal with VoiceOver running
    CMD+L to jump to address bar
    CTRL+Option+U to open Web Rotor
    Type search term with Web Rotor open to search within Web Rotor
    CTRL + Option + ← ↑ ↓ → to explore content
    CTRL + Option + CMD + H to move forward by heading
    CTRL + Option + CMD + Shift + H to move backward by heading
    WebAIM's article on Using VoiceOver to evaluate Web Accessibility has a full introduction to VoiceOver 
    from the point of view of evaluating accessibility, including most keyboard commands available.
    
    If you don't have a Mac device, NVDA is a free, open source screen reader available for Windows. 
    WebAIM's introduction to NVDA covers the basics of using NVDA to check accessibility.
    
    If you only use Linux, Orca is available in the Gnome desktop manager, although this screen reader 
    is much more rarely used and suffers from poor support by web browsers.


Content 4: Using Headings
    WebAIM checklist items:
    
    1.3.2: http://webaim.org/standards/wcag/checklist#sc1.3.2
    2.4.10: http://webaim.org/standards/wcag/checklist#sc2.4.10
    1.3.1: http://webaim.org/standards/wcag/checklist#sc1.3.1
    2.4.1: http://webaim.org/standards/wcag/checklist#sc2.4.1
    2.4.6: http://webaim.org/standards/wcag/checklist#sc2.4.6
    
    
    JavaScript headings snippet:
    
        for (var i = 0, headings = $$('h1,h2,h3,h4,h5,h6');
             i < headings.length; i++) {
           console.log(headings[i].textContent.trim() + " " +  
                       headings[i].tagName,
                       headings[i]);
        }
        
Content 7: Other navigational options example

    Shortcuts mentioned:
    
        CTRL+Option+U to open Web Rotor
        ← and → to change panes within Web Rotor
        Type search term with Web Rotor open to search within Web Rotor
        Enter to move VoiceOver focus to item from Web Rotor
        CTRL + Option + Spacebar to activate link/button/other element
        CTRL + Option + ← ↑ ↓ → to explore content
        CTRL + Option + CMD + H to move forward by heading
        CTRL + Option + CMD + Shift + H to move backward by heading
        CTRL + Option + W to have a word spelled out
        
    WebAIM's article on accesskey: http://webaim.org/techniques/keyboard/accesskey
    
    WebAIM's articles on VoiceOver and NVDA:
    
    http://webaim.org/articles/voiceover/
    http://webaim.org/articles/nvda

Content 8: Link Text
    
    WebAIM checklist item 2.4.9: http://webaim.org/standards/wcag/checklist#sc2.4.9
    
Content 9: Quiz: Link Text
    
    Visit the delicious Bondi Brunch page and inspect the links indicated. If you find an issue with a link, come back and check the box.
    http://udacity.github.io/ud891/lesson4-semantics-navigating/08-link-text/index.html
    
Content 10: Landmarks

    Page
        Header
            Nav
        Main
            Section
                Article
                    Side
            Section
                Weather
        Footer
            Links
    

    name classes
        .header{}
        .nav{}
        .article{}
        .aside{}
        .footer{}