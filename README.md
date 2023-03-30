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

# What I learned from About

**Practice on components**

Practiced passing props to component and then have the component be printed via dynamic JSX, like this:

    {ARRAY.map((item,id)=>(

        <Component key={id} prop-1={item.prop-1} prop-2={item.prop-2} prop-n={item.prop-n}/>

    ))}

If you type a parenthesis after the "arrow" in the arrow function, the element gets rendered inmediately.

**Time stamp: 4:54:00**

**Time stamp for Chef section: 5:05:00**

# What I learned from Intro

**Usign videos in React**

Simply by using the video self-closing tag you can include a video inside a webpage.

        <video
           src={meal}
           ref={vidRef} //hook
           type="video/mp4"
           loop
           controls={false}
           muted  
        />

For this to work you are required to:

1. Import the video file, in this case:

        import { meal } from '../../constants'

2. Import a couple of hooks from React. Namely: *useState* and *useRef*

3. Set both hooks, like:

        const [playVideo, setPlayVideo] = useState(false);
        const vidRef = useRef();

4. Create a handler for an *onClick* event:

        const handleVideo = () => {
        setPlayVideo((prevPlayVideo) => !prevPlayVideo);

        if (playVideo) {
          vidRef.current.pause();
        } else {
          vidRef.current.play();
        }
        };

  You need to pass a callback function on the state function of the model to be able to toggle the state from the previous state. Otherwise, you'd get stucked.

5. Finally create a div to build a control for play/pause and add the aforementioned *onClick* with the "handler" as an argument event:

        <div className="app__video-overlay_circle flex__center"
        onClick={handleVideo}>

          {playVideo 
                ? <BsPauseFill color="#fff" fontSize={30}/> 
                : <BsFillPlayFill color="#fff" fontSize={30}/> 
            }
        </div>

You can also import React icons to use for the video controls:

import { BsFillPlayFill, BsPauseFill } from "react-icons/bs";

... and style them at your will.

*et voila!*

**Time stamp: 5:16:00**

# What I learned from Laurels

**Destructuring the destructured data**

In this section I had to map an array of objects that had a variable value for one of its properties: 

    const awards = [
     {
       imgUrl: images.award02,
       title: 'Bib Gourmond',
       subtitle: 'Lorem ipsum dolor sit amet, consectetur.',
     },
     {
       imgUrl: images.award01,
       title: 'Rising Star',
       subtitle: 'Lorem ipsum dolor sit amet, consectetur.',
     },
     {
       imgUrl: images.award05,
       title: 'AA Hospitality',
       subtitle: 'Lorem ipsum dolor sit amet, consectetur.',
     },
     {
       imgUrl: images.award03,
       title: 'Outstanding Chef',
       subtitle: 'Lorem ipsum dolor sit amet, consectetur.',
     },
    ];

Each value of imgUrl, changes from one object to another. For the map function to return each of the objects correctly it needs to be destructured twice. Like this: 

    const AwardCard = ({ award: { imgUrl, title, subtitle } }) => (
      <div className="app__laurels_awards-card">
        <img src={imgUrl} alt="award" />
      </div>
    );

So, by passing "award" as an argument of the AwardCard component (which refers to each of object of the ARRAY data.awards) I could further destructure this argument into its properties: imgUrl, title, subtitle. 

Which then can be passed in dynamic bits of code inside HTML/JSX elements.

    <div className="app__laurels_awards">
        {data.awards.map((award) => (
          <AwardCard key={award.title} award={award} />
        ))}
    </div>

This was interesting to me because it highlights how planning your data structure, as well as your file structure, plays a major role in how you manage and write your code.

*Cool!*

**Time stamp: 5:29:00**