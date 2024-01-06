<script>
  let frameSelection = "element";
  let directionSelection = "vertical";
  let arrangeSelection = "between";
  let alignSelection = "left";
  let colorSelection = "highlight";
  let compElement;
  let compFrame;
  let ctaSelection = "";
  let textSelection = "";
  let widthSelection = "w-md";
  let heightSelection = "h-md";
  let fillSelection = "";
  let growSelection = "";
  let stickSelection = "stick";
  let scrollSelection = "scroll";
  $: themeSelection = "a";
  // $: themeImage = themes[themeSelection].image;

  //Toggle classes on and off
  function toggleClass(element, className) {
    for (let i = 0; element.length; i++) {
      if (element[i].classList.contains(className)) {
        element[i].classList.remove(className);
      } else {
        element[i].classList.add(className);
      }
    }
  }

  $: setTheme = (preferredTheme, themes) => {
    let themeString = "";
    for (let [key, value] of Object.entries(themes[preferredTheme].styles)) {
      themeString += `--${key}: ${value}; `;
    }
    themeSelection = themeString;
  };

  let themes = {
    a: {
      styles: {
        "action-surface-color": "#ff0000",
        "action-border-color": "#ff0000",
        "action-hover-color": "#ff4444",
        "accent-surface-color": "#ffffff",
        "accent-heading-color": "#222",
        "accent-text-color": "#555",
        "element-radius": "var(--sm)",
        "frame-radius": "var(--xl)",
        "action-base-position": "translate(0, -0.25rem)",
        "action-hover-position": "translate(0, -0.25rem)",
        "action-base-shadow": "0 0.25em 0 0 #cc0000",
        "action-hover-shadow": "0 0.25em 0 0 #dd0000",
        "action-active-shadow": "0 0.05em 0 0 #cc0000",
        "base-font-family": "'Helvetica Neue', sans-serif",
        "heading-font-family": "'Helvetica Neue', sans-serif",
      },
      image: "https://placehold.co/1920x1080",
    },
    b: {
      styles: {
        "action-surface-color": "#00ff00",
        "action-border-color": "#00ff00",
        "action-hover-color": "#00dd00",
        "action-text-color": "#000",
        "accent-surface-color": "#222222",
        "accent-heading-color": "#fff",
        "accent-text-color": "#ffffff",
        "element-radius": "0",
        "frame-radius": "0",
        "action-base-position": "translate(-0.25em, -0.25rem)",
        "action-hover-position": "translate(-0.35em, -0.35rem)",
        "action-base-shadow": "0.25em 0.25em 0 0 #00ffff",
        "action-hover-shadow": "0.35em 0.35em 0 0 #00ddff",
        "action-active-shadow": "0 0 0 0 #00aaff",
        "base-font-family": "'Verdana', sans-serif",
        "heading-font-family": "monospace",
      },
      image: "https://placehold.co/1921x1080",
    },
    c: {
      styles: {
        "action-surface-color": "#3333ff",
        "action-border-color": "#3333ff",
        "action-hover-color": "#4444ff",
        "accent-surface-color": "#000033",
        "accent-text-color": "#aaaaff",
        "accent-heading-color": "#fff",
        "element-radius": "var(--xxs)",
        "frame-radius": "var(--sm)",
        "action-base-position": "translate(0, -0.1rem)",
        "action-hover-position": "translate(0, -0.1rem)",
        "action-base-shadow": "0 0.1em 0 0 #5555ff",
        "action-hover-shadow": "0 0.1em 0 0 #6666ff",
        "action-active-shadow": "0 0 0 0 #5555ff",
        "base-font-family": "'Georgia', serif",
        "heading-font-family": "'Georgia', serif",
      },
      image: "https://placehold.co/1922x1080",
    },
  };
</script>

<div>
  <div class="frame padding fix bottom center w-full">
    <nav class="accent background padding round shadow">
      <a href="#theme">Theme</a>
      <a href="#layout">Layout</a>
      <a href="#style">Style</a>
      <a href="#scale">Scale</a>
      <a href="#refine">Refine</a>
      <a href="https://github.com/designlift">
        <svg role="img" viewBox="0 0 24 24" class="h-sm w-sm" xmlns="http://www.w3.org/2000/svg"><title>GitHub</title><path fill="currentColor" d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12" /></svg>
      </a>
    </nav>
  </div>

  <!-- Make the descriptions interactive -->
  <main>
    <header class="frame padding around vertical center accent background">
      <hgroup>
        <h1>Designlift Docs</h1>
        <p class="xl">🚀</p>
      </hgroup>
      <hgroup>
        <h2 class="xxl">Designlift-off.</h2>
        <p>Your guide to simpler web design—in one page.</p>
      </hgroup>
    </header>

    <article class="vertical gap frame padding">
      <header>
        <hgroup class="vertical center">
          <p class="xl">🎨</p>
          <h2 class="xl" id="theme">Theme</h2>
          <p class="lg">Refine the theme settings to establish strong consistent design system.</p>
        </hgroup>
      </header>
      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Variables</h3>
          <p>Define the visual qualities using color palette, typography, and scale in <code>theme.css</code> and watch the magic happen.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={setTheme("a", themes)}>Theme A</button>
              <button on:click={setTheme("b", themes)}>Theme B</button>
              <button on:click={setTheme("c", themes)}>Theme C</button>
            </menu>
            <section class="padding border frame radius">
              <div class="vertical background accent radius frame animation" style={themeSelection}>
                <div>
                  <!-- <figure>
                    <img src="https://placehold.co/1920x1080" alt="David Schofield" class="h-xl cover" />
                  </figure> -->
                  <section class="padding vertical gap frame">
                    <hgroup class="vertical">
                      <h2 class="xl">John Smith</h2>
                      <p>Chief Executive Officer</p>
                    </hgroup>
                    <a class="primary horizontal center"> Message </a>
                  </section>
                </div>
              </div>
            </section>
          </div>
        </section>
      </section>
    </article>

    <article class="vertical gap frame padding">
      <header>
        <hgroup class="vertical center">
          <p class="xl">🛠️</p>
          <h2 class="xl" id="layout">Layout</h2>
          <p class="lg">Start with a semantic HTML structure to improve accessibility and SEO. Structure your content. Wrap related elements with parent elements.</p>
        </hgroup>
      </header>

      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Frames</h3>
          <p>Your HTML should provide some natural groups of content. Designate the most important groups with the <code>frame</code> class.</p>
        </hgroup>

        <section>
          <div class="vertical gap">
            <menu>
              <button on:click={() => (frameSelection = "element")}>&lt;element&gt;</button>
              <button on:click={() => (frameSelection = "frame")}>.frame</button>
            </menu>
            <section class="padding background center radius h-xxl vertical center accent">
              <div class="{frameSelection} border padding center radius">
                I’m the {frameSelection}
              </div>
            </section>
          </div>
        </section>

        <section class="split gap divider">
          <hgroup>
            <h3 class="lg">Direction</h3>
            <p>To have elements flow in a particular direction, use the <code>vertical</code>, <code>horizontal</code>, <code>stack</code>, <code>split</code>, or <code>grid</code> class.</p>
          </hgroup>

          <section class="vertical gap">
            <div class="vertical gap">
              <menu>
                <button on:click={() => (directionSelection = "horizontal")}>.horizontal</button>
                <button on:click={() => (directionSelection = "vertical")}>.vertical</button>
                <button on:click={() => (directionSelection = "grid")}>.grid</button>
                <button on:click={() => (directionSelection = "split")}>.split</button>
                <button on:click={() => (directionSelection = "stack")}>.stack</button>
              </menu>
              <section class="{directionSelection} gap padding background accent frame center radius h-xxl" style="--grid-min-size: var(--w-md)">
                <div class="w-md h-md frame highlight background"></div>
                <div class="w-md h-md frame highlight background"></div>
                <div class="w-md h-md frame highlight background"></div>
                <div class="w-md h-md frame highlight background"></div>
              </section>
            </div>
          </section>
        </section>
      </section>
      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Arrange</h3>
          <p>To arrange elements within an element, use the <code>around</code>, <code>between</code>, <code>start</code>, <code>center</code>, or <code>end</code> class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={() => (arrangeSelection = "around")}>.around</button>
              <button on:click={() => (arrangeSelection = "between")}>.between</button>
              <button on:click={() => (arrangeSelection = "start")}>.start</button>
              <button on:click={() => (arrangeSelection = "center")}>.center</button>
              <button on:click={() => (arrangeSelection = "end")}>.end</button>
            </menu>
            <section class="{arrangeSelection} horizontal gap padding background accent frame radius">
              <div class="w-md h-md frame highlight background"></div>
              <div class="w-md h-md frame highlight background"></div>
            </section>
          </div>
        </section>
      </section>
      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Alignment</h3>
          <p>To set text alignment, use the <code>left</code>, <code>center</code>, or <code>right</code> class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={() => (alignSelection = "left")}>.left</button>
              <button on:click={() => (alignSelection = "center")}>.center</button>
              <button on:click={() => (alignSelection = "right")}>.right</button>
            </menu>
            <section class="{alignSelection} gap padding background accent frame radius">
              <div>I am set {alignSelection}.</div>
            </section>
          </div>
        </section>
      </section>
    </article>

    <article class="vertical gap frame padding">
      <header>
        <hgroup class="vertical center">
          <p class="xl">😎</p>
          <h2 class="xl" id="style">Style</h2>
          <p class="lg">Now style your content to tell a story. Use composition and color to call attention to important elements and create a visual hierarchy.</p>
        </hgroup>
      </header>
      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Color</h3>
          <p>Use color to emphasize text or frames with <code>accent</code>, <code>action</code>, or <code>highlight</code> class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={(e) => (colorSelection = "accent")}>.accent</button>
              <button on:click={(e) => (colorSelection = "action")}>.action</button>
              <button on:click={(e) => (colorSelection = "highlight")}>.highlight</button>
              <button on:click={(e) => (colorSelection = "none")}><s>none</s></button>
            </menu>
            <section class="gap padding border vertical accent frame radius">
              <div class="{colorSelection} padding center">I am a text using {colorSelection}.</div>
              <div class="{colorSelection} padding border center">I am a border using {colorSelection}.</div>
              <div class="{colorSelection} padding background center">I am a background using {colorSelection}.</div>
            </section>
          </div>
        </section>
      </section>

      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Composition</h3>
          <p>Use color to emphasize text or frames with <code>accent</code>, <code>action</code>, or <code>highlight</code> class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={toggleClass([compFrame, compElement], "background")}>.background</button>
              <button on:click={toggleClass([compFrame, compElement], "border")}>.border</button>
              <button on:click={toggleClass([compFrame, compElement], "gap")}>.gap</button>
              <button on:click={toggleClass([compFrame, compElement], "padding")}>.padding</button>
              <button on:click={toggleClass([compFrame, compElement], "radius")}>.radius</button>
              <button on:click={toggleClass([compFrame, compElement], "round")}>.round</button>
              <button on:click={toggleClass([compFrame, compElement], "shadow")}>.shadow</button>
            </menu>
            <section class="padding background accent vertical gap frame radius">
              <div bind:this={compElement} class="horizontal center">
                <div class="w-md h-md frame highlight background"></div>
                I’m an element
                <div class="w-md h-md frame highlight background"></div>
              </div>
              <div bind:this={compFrame} class="horizontal frame center">
                <div class="w-md h-md frame highlight background"></div>
                I’m a frame
                <div class="w-md h-md frame highlight background"></div>
              </div>
            </section>
          </div>
        </section>
      </section>

      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Call to Action</h3>
          <p>Emphasize primary calls to action with <code>primary</code> or <code>secondary</code> class on button and link elements.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={(e) => (ctaSelection = "primary")}>.primary</button>
              <button on:click={(e) => (ctaSelection = "secondary")}>.secondary</button>
              <button on:click={(e) => (ctaSelection = "none")}><s>none</s></button>
            </menu>
            <section class="gap padding background accent vertical frame radius horizontal">
              <div class="horizontal gap">
                <button class={ctaSelection}>Button</button>
                <a class={ctaSelection}>Link</a>
              </div>
              <div>
                <p>This link is <a class={ctaSelection}>inline</a>.</p>
              </div>
            </section>
          </div>
        </section>
      </section>
    </article>

    <article class="vertical gap frame padding">
      <header>
        <hgroup class="vertical center">
          <p class="xl">↕️</p>
          <h2 class="xl" id="scale">Scale</h2>
          <p class="lg">Set the size and scale of elements to reinforce the visual heirarchy.</p>
        </hgroup>
      </header>
      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Text</h3>
          <p>Set the size of text to say something big or small with <code>xxs</code>, <code>xs</code>, <code>sm</code>, class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={(e) => (textSelection = "xxs")}>.xxs</button>
              <button on:click={(e) => (textSelection = "xs")}>.xs</button>
              <button on:click={(e) => (textSelection = "sm")}>.sm</button>
              <button on:click={(e) => (textSelection = "md")}>.md</button>
              <button on:click={(e) => (textSelection = "lg")}>.lg</button>
              <button on:click={(e) => (textSelection = "xl")}>.xl</button>
              <button on:click={(e) => (textSelection = "xxl")}>.xxl</button>
              <button on:click={(e) => (textSelection = "xxxl")}>.xxxl</button>
            </menu>
            <section class="padding background vertical h-xxl center accent frame radius">
              <p class={textSelection}>Text</p>
            </section>
          </div>
        </section>
      </section>

      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Width</h3>
          <p>Set the element width using <code>w-xxs</code>, <code>w-xs</code>, <code>w-sm</code>, <code>w-md</code>, <code>w-lg</code>, <code>w-xl</code>, <code>w-xxl</code>, or <code>w-xxxl</code> class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={(e) => (widthSelection = "w-xxs")}>.w-xxs</button>
              <button on:click={(e) => (widthSelection = "w-xs")}>.w-xs</button>
              <button on:click={(e) => (widthSelection = "w-sm")}>.w-sm</button>
              <button on:click={(e) => (widthSelection = "w-md")}>.w-md</button>
              <button on:click={(e) => (widthSelection = "w-lg")}>.w-lg</button>
              <button on:click={(e) => (widthSelection = "w-xl")}>.w-xl</button>
              <button on:click={(e) => (widthSelection = "w-xxl")}>.w-xxl</button>
              <button on:click={(e) => (widthSelection = "w-xxxl")}>.w-xxxl</button>
              <button on:click={(e) => (widthSelection = "w-full")}>.w-full</button>
            </menu>
            <section class="padding background vertical h-xxl center accent frame radius">
              <div class="horizontal accent center">
                <div class="{widthSelection} h-md frame highlight background"></div>
              </div>
            </section>
          </div>
        </section>
      </section>

      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Height</h3>
          <p>Set an element height using <code>h-xxs</code>, <code>h-xs</code>, <code>h-sm</code>, <code>h-md</code>, <code>h-lg</code>, <code>h-xl</code>, <code>h-xxl</code>, or <code>h-xxxl</code>, class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={(e) => (heightSelection = "h-xxs")}>.h-xxs</button>
              <button on:click={(e) => (heightSelection = "h-xs")}>.h-xs</button>
              <button on:click={(e) => (heightSelection = "h-sm")}>.h-sm</button>
              <button on:click={(e) => (heightSelection = "h-md")}>.h-md</button>
              <button on:click={(e) => (heightSelection = "h-lg")}>.h-lg</button>
              <button on:click={(e) => (heightSelection = "h-xl")}>.h-xl</button>
              <button on:click={(e) => (heightSelection = "h-xxl")}>.h-xxl</button>
              <button on:click={(e) => (heightSelection = "h-xxxl")}>.h-xxxl</button>
              <button on:click={(e) => (heightSelection = "h-full")}>.h-full</button>
            </menu>
            <section class="padding background vertical h-xxl center accent frame radius">
              <div class="horizontal accent center">
                <div class="{heightSelection} w-md frame highlight background"></div>
              </div>
            </section>
          </div>
        </section>
      </section>
    </article>

    <article class="vertical gap frame padding">
      <header>
        <hgroup class="vertical center">
          <p class="xl">🧠</p>
          <h2 class="xl" id="refine">Refine</h2>
          <p class="lg">Take design to the next level.</p>
        </hgroup>
      </header>
      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Fill</h3>
          <p>Scale to the available screen size with <code>fill</code> class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={(e) => (fillSelection = "fill")}>.fill</button>
              <button on:click={(e) => (fillSelection = "none")}><s>none</s></button>
            </menu>
            <section class="padding background vertical h-xxl center accent frame radius">
              <div class="h-full w-full {fillSelection} background highlight"></div>
            </section>
          </div>
        </section>
      </section>
      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Grow</h3>
          <p>Occupy the available screen space between elements with <code>grow</code> class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={(e) => (growSelection = "grow")}>.grow</button>
              <button on:click={(e) => (growSelection = "none")}><s>none</s></button>
            </menu>
            <section class="padding background vertical h-xxl center accent frame radius">
              <div class="h-sm w-full background"></div>
              <div class="h-sm w-full {growSelection} background highlight"></div>
              <div class="h-sm w-full background"></div>
            </section>
          </div>
        </section>
      </section>

      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Scroll</h3>
          <p>Make a frame or element scroll by setting a size and the <code>scroll</code> class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={(e) => (scrollSelection = "scroll")}>.scroll</button>
              <button on:click={(e) => (scrollSelection = "none")}><s>none</s></button>
            </menu>
            <section class="padding background vertical h-xxl center accent frame radius">
              <p class="h-xxl w-full border padding highlight {scrollSelection}">Overflow scroll is particularly valuable when designing responsive websites, as it allows for a consistent and intuitive user experience across various devices. Whether users are accessing the site on a desktop, tablet, or mobile device, the scroll functionality ensures that content remains accessible and easy to navigate. This adaptability contributes to a more inclusive design, catering to a broad audience with different screen sizes and resolutions. Furthermore, the careful implementation of overflow scroll aligns with modern design principles, promoting a sleek and user-centric interface that prioritizes readability and engagement.</p>
            </section>
          </div>
        </section>
      </section>

      <section class="split gap divider">
        <hgroup>
          <h3 class="lg">Position</h3>
          <p>Position elements on the page with <code>stick</code> or <code>fix</code>, and add a position <code>top</code>, <code>left</code>, <code>bottom</code>, <code>right</code> class.</p>
        </hgroup>

        <section class="vertical gap">
          <div class="vertical gap">
            <menu>
              <button on:click={(e) => (stickSelection = "stick")}>.stick</button>
              <button on:click={(e) => (stickSelection = "none")}><s>none</s></button>
            </menu>
            <section class="padding background vertical h-xxl center accent frame radius">
              <div class="w-full border scroll h-xxl">
                <p class="w-full {stickSelection} top background padding">Overflow Scroll</p>
                <p class="padding">Overflow scroll enhances web user experience by enabling seamless navigation through content that exceeds the available space within a designated container. This feature ensures that users can effortlessly explore lengthy information or images by introducing a scroll bar for convenient access. Its application is vital for maintaining clean and organized web layouts while accommodating diverse content lengths.</p>
                <p class="w-full {stickSelection} top background highlight padding">Sticky Position</p>
                <p class="padding">This functionality enhances user interaction by keeping specific content, such as navigation menus or headers, consistently visible. Implementing sticky elements contributes to a more intuitive and accessible browsing experience, allowing users to access crucial information without interruption as they navigate through web content.</p>
              </div>
            </section>
          </div>
        </section>
      </section>
    </article>
  </main>
</div>
