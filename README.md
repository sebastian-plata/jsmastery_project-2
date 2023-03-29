# jsmastery_project-2

Second Project: Fully responsive Modern Restaurant Application

# What I learned from Navbar

**Using JSX dynamic code blocks to manipulate DOM**

It is possible to implement dynamic blocks "({<'code'>})" in order to show, hide and in general manipulate HTML elements in your design. This are simple sentences that use simple JS instructions. In example:

    {toggleMenu && (
        <div className="app__navbar-smallscreen_overlay flex__center slide-bottom">
            <MdOutlineRestaurantMenu
            fontSize={27}
            className="overlay**close"
            onClick={() => setToggleMenu(false)}
            />
                <ul className="app**navbar-smallscreen_links">
                    <li className="p__opensans">
                    <a href="#home">Home</a>
                    </li>
                    <li className="p__opensans">
                    <a href="#about">About</a>
                    </li>
                    <li className="p__opensans">
                    <a href="#menu">Menu</a>
                    </li>
                    <li className="p__opensans">
                    <a href="#awards">Awards</a>
                    </li>
                    <li className="p__opensans">
                    <a href="#contact">Contact</a>
                    </li>
                </ul>
        </div>
    )}

toggleMenu's boolean value will determine if the elements within the parenthesis will be displayed on the browser.

toggleMenu value is determined using an array that contains of:

    const [toggleMenu, setToggleMenu] = useState(false);

By usign the *useState* hook we can use an *onClick={() => {}}* event that executes setToggleMenu function and, therefore, changes toggleMenu's value.

    <GiHamburgerMenu 
    color="#fff" 
    fontSize={27} 
    onClick={() => setToggleMenu(true)}
    />

and,

    <MdOutlineRestaurantMenu
    fontSize={27}
    className="overlay__close"
    onClick={() => setToggleMenu(false)}
    />
 
The former makes the HTML elements visible and the later hides them (which is the default value of the variable: toggleMenu).
    
**Time stamp: 4:02:00**

# What I learned from Header

**Props and components for containers**

Basically if you an element that will be repeated a bunch of times in the webpage/site you're very welcome to make it a *component*. Components cant take dynamic properties, also known as *props*, which then can take values for each of the component's instances.

This makes working very streamlined as well as brings consistency and cohesion to the design. Both, very important elements of a well designed product.

**Time stamp: 4:12:00**

# What I learned from About

**Pre-making classes to assing same properties to multiple elements**

When planning your layour it is important to think what properties are going to be shared across sections. For example: you want your containers to be ALL be centered or you want your paragraphs to all have the same text properties. One way to make things more comfortable for you is to create classes for this setups and then add them to the elements that you want to share them across. Like this: 

    
    .flex__center {
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .p__opensans {
        font-family: var(--font-alt);
        color: var(--color-white);
        font-weight: 400;
        letter-spacing: 0.04em;
        text-transform: capitalize;
        line-height: 28px;
        font-size: 16px;
    }

     <div className='app__aboutus-overlay flex__center'></div>

     <p className='p__opensans'></p>

This will *save time* by *not having to type the same style rules over and over and over again*. Also your code will look much nicer. 

*When working in React you may add this styles to App.css*

*Side note: Use index.css to set up your 'root' styles*

**Time stamp: 4:26:00**