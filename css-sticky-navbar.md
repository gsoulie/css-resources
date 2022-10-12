

*html*

````html
<section id="header">
  <article>
    <h2>Let's read some jokes!</h2>
  </article>
</section>
<nav>
  <a href="#header">Home</a>
  <a href="#tim-vine">Tim Vine</a>
  <a href="#bill-hicks">Bill Hicks</a>
  <a href="#stewart-francis">Stewart Francis</a>
</nav>
<section>
  <article>
    <h2>Tim Vine</h2>
    <p>I said to the gym instructor: ‘Can you teach me to do the splits?’ He said: ‘How flexible are you?’ I said: ‘I can’t make Tuesdays.'</p>
    <p>I’ve decided to sell my Hoover – it was just collecting dust.</p>
    <p>I saw Arnold Schwarzenegger eating a chocolate egg. I said: ‘I bet I know what your favourite Christian festival is.’ He said: ‘You have to love Easter, baby.'</p>
    <p>I was reading a book – ‘The History of Glue’ – I couldn’t put it down.</p>
  </article>
</section>
<section>
  <article>
    <h2>Bill Hicks</h2>
    <p>I need my sleep. I need about eight hours a day, and about ten at night.</p>
    <p>I don't mean to sound bitter, cold, or cruel, but I am, so that's how it comes out.</p>
    <p>I never got along with my dad. Kids used to come up to me and say, "My dad can beat up your dad." I'd say "Yeah? When?"</p>
  </article>
</section>
<section>
  <article>
    <h2>Stewart Francis</h2>
    <p>There’s a fine line between hyphenated words.</p>
    <p>I used to be in a band called ‘Missing Cat’… you probably saw our posters.</p>
    <p>Have you ever imagined a world with no hypothetical situations?</p>
    <p>I was going to join the debating team, but somebody talked me out of it.</p>
  </article>
</section>
````

*css*

````css
nav {
  background-color: #3a24f0;
  padding: 10px;
  text-align: center;
  width: 100%;
  position: sticky; // <-- 
  top: 0px;
}

section {
  min-height: 100vh;
}

@media
(prefers-reduced-motion: no-preference) {
  html {
    scroll-behavior: smooth;
  }
}
````
