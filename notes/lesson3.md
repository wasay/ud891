Lesson 3: Semantics Basics

Content 1: Semantics Introduction

Content 2: Assistive Technology

    Assistive technology is a umbrella term for
        devices
        software
        tools
        
        that helps any person with disability complete a task
        
    People may interact with your website using
        Screen reader
        braille display
        magnification
        voice control
        switch access
        sip and puff
        eye tracking
        
        may also be express as "Programmatically expressed semantics"

Content 3: Affordances
    
    Well design affordances enable people to do something with
    as little training as possible.
    
Content 5: Semantics and Assistive Technology

    Web AIM WCAG 2.0 Checklist 4.1.2:
        Name, Role, Value: markup is used in a way that facilitates accessibility.
        
        Name, Role, Value: For all user interface components, the name and role
        can be programmatically determined; states, properties, and values
        that can be set by the user can be programmatically set.
        
Content 6:
    Try out the flight booking form, then come back here once you've successfully filled it out.
    http://udacity.github.io/ud891/lesson3-semantics-built-in/02-chromevox-lite/
    
Content 10:
    Considering the Ally tree when writing your HTML will help in making
    your sites more accessible.
    
    
Content 13: Writing semantic HTML
    WebAIM Guideline 1.1: http://webaim.org/standards/wcag/checklist#g1.1
        Provide text alternatives for any non-text content
    
    The MDN page on <label> demonstrates the two options for associating a <label> with the thing it's labelling.
    
    The W3C spec has a list of what types of elements work with a <label> tag.
    
    
Content 15: Text Alternatives
    WebAIM checklist items:
    
    1.3.2: http://webaim.org/standards/wcag/checklist#sc1.3.2
    2.4.10: http://webaim.org/standards/wcag/checklist#sc2.4.10
    1.3.1: http://webaim.org/standards/wcag/checklist#sc1.3.1
    2.4.1: http://webaim.org/standards/wcag/checklist#sc2.4.1
    2.4.6: http://webaim.org/standards/wcag/checklist#sc2.4.6
    
    
    JavaScript headings snippet:
    
        var hs = document.querySelectorAll('h1,h2,h3,h4,h5,h6');
        for (var i = 0; i < hs.length; i++) {
           console.log(hs[i].textContent.trim() + " " +  
                       hs[i].tagName,
                       hs[i]);
        }