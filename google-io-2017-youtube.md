# Google I/O '17

## Production Progressive Web Apps With JavaScript Frameworks 

* Video: https://www.youtube.com/watch?v=aCMbSyngXB4

* Lecturer: Addy Osmani

* > Learn how the world’s largest brands ship Progressive Web Apps that instantly load on mobile hardware. We’ll look at how apps built using React, Preact, Vue, Angular & Polymer can be used to build instantly interactive, engaging & data-plan sensitive user experiences. We'll also look at how this investment paid off on core business metrics. You’ll leave this session learning PWA best practices, patterns for efficiently loading websites and the latest tools for getting fast and staying fast. You won’t want to miss it.

* Lightweight Framework for developing mobile web apps: Polymer, Preact, Vue.js, [Svelte.js](https://svelte.technology/)
![lightweight-framework-for-mobile-apps](https://user-images.githubusercontent.com/4011348/39191792-50459246-480a-11e8-8d80-411fbd450d3f.png)

* a successor TodoMVC - [HNPWA](https://hnpwa.com/) 
![hwpwa](https://user-images.githubusercontent.com/4011348/39191789-4ef703c0-480a-11e8-8510-2756853a57f3.png)

* Firebase H2 Server push: [Firebase Blog - HTTP2 comes to Firebase Hosting](https://firebase.googleblog.com/2016/09/http2-comes-to-firebase-hosting.html)

* [LightHouse](https://developers.google.com/web/tools/lighthouse/): Lighthouse is an [open-source](https://github.com/GoogleChrome/lighthouse), automated tool for improving the quality of web pages. You can run it against any web page, public or requiring authentication. It has audits for performance, accessibility, progressive web apps, and more.

* [WebPagetest](https://www.webpagetest.org): Website Performance and Optimization Test -- Run a free website speed test from around the globe using real browsers at consumer connection speeds with detailed optimization recommendations.

* Twitter Lite

  * React

  * ``<link rel="dns-prefetch“ href="//api.twitter.com">``

  * ``<link rel="preload" as="script" crossorigin="anonymous" href=https://foo.com/bar.js"">``
  ![script-preload](https://user-images.githubusercontent.com/4011348/39191799-528ed382-480a-11e8-973c-84b22d2159e4.png)

  * > 4x improvement to render perf by using ``requestIdleCallback()`` to defer JS loading of images. -- Nicolas Gallagher, Technical leader for Twitter Lite

  * Defer rendering when mounting/unmounting components (esp. large trees of components, like timeline of Tweets), by creating a small higher order component on top of that to improve the perceived performance
  ![defer-rendering-complex-react-compoenent](https://user-images.githubusercontent.com/4011348/39191772-4630c334-480a-11e8-99b5-2a22cff03d72.png)

  * Prevent unnecessary updates using ``shouldComponentUpdate()``

  * Precache using ``serviceWorker``

  * Lazy-load using Webpack code-splitting
  ![webpack-code-splitting](https://user-images.githubusercontent.com/4011348/39191802-541c391a-480a-11e8-9963-448f9db6218b.png)

  * More on: http://bit.ly/twitterlite-perf ; http://bit.ly/twitter-casestudy

* Tinder:
  * React, React Router, Webpack

* [PRPL Pattern](https://developers.google.com/web/fundamentals/performance/prpl-pattern/): PRPL is a pattern for structuring and serving Progressive Web Apps (PWAs), with an emphasis on the performance of app delivery and launch.
![prpl-pattern](https://user-images.githubusercontent.com/4011348/39191794-519962bc-480a-11e8-925b-16357259f433.png)