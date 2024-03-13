## Basics of Hotwire and Turbo for Ruby on Rails

### Hotwire and Turbo
  - Hotwire lets developers dynamically update parts of a page in response to user interactions without writing JavaScript. Hotwire is made of Turbo and Stimulus. Turbo will dynamically update views without JavaScript, including(Turbo Drive, Frames, Streams).
  If JavaScript is necessary, Stimulus can be used. 

 ### With "vanilla Ruby on Rails"
  - A user clicks a button/link, this sends an HTTP request to a controller action and a new page of HTML is
    sent back as the response. The whole page gets reloaded even if only one part needed updating.

### 4 Parts of Turbo
  - Turbo Links: Uses async JavaScript to fetch pages. It automatically merges the HTML document head and replaces the body. With this there is no fullpage reload.

  - Turbo Drive: Can be used for form submissions.

  - Turbo Frames: Will only update part of the body(the frame), making responsiveness even faster.

  - Turbo Streams: Will update more than one part of a page. Also Turbo Streams can have partial page updates over different browser sessions using Action Cable asynchronously. 

  - Stimulus - When you need some JavaScript. Can use a JS library, for animations etc. Will update DOM not accessing server data. 




## The goal here... 
is to create two buttons, one will add apples to our count and another will remove them.
I also added TailwindCSS for a little styling, but the interest here is for setting a foundational understanding of Hotwire and Turbo.



Some notes


In add/remove.turbo_stream.erb

```
  <%= turbo_stream.update('count', pluralize(@count, 'apple')) %>
```
Count is the Id of the element that will be updated, 
pluralize(@count, 'apple') is what will be updating the count


```
  <%= turbo_stream.append('log', partial: 'count', locals: {operation: :add}) %>
```
