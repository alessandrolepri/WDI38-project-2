# General Assembly Project 2 : 1 day Hackathon

Live Version: https://hackathon-react-one-day.herokuapp.com/

### Timeframe
1 day

# Selection

Build an Express App based on your idea using at least one API (pair coding)

## Technologies used

* React.js
* JavaScript (ES6)
* HTML5
* CSS
* SCSS
* GitHub / Git
* Heroku
* Express

## APIs:

* Mapbox
* Skiddle


## Installation

1. Clone or download the repo
2. Open the `index.html` in your browser of choice, leave your feedback and possibly improvement



# React Hackathon - Eventify


You can find a hosted version here:
[alessandrolepri/WDI38-project-2]
(https://github.com/alessandrolepri/WDI38-project-2)



## App overview
Eventify is a London base Express App that will show you the daily events depending on your geolocation within 10 radius miles.
All the events are classified with a different coloured pinpoint in order to let the users choose what they most like.
By clicking to the pinpoint the users can also check what kind of event is live and have the option to be redirect to an external web site where they van buy tickets or having the direction to the place from their current position by Google Maps web site.  


# Process

An Express App which helps the user to find daily events in London based on your geolocation. Filtering ‘today date’ and passing to Mapbox your geolocation we were able to filter by API provided only the events live the same day in 10 miles radius from your location. We have then created a div to create all the markers in order  to have display the pinpoint in the map.
```
getEvents(latitude, longitude) {
    const today = new Date(),
      date = today.getFullYear() + '-' + ((today.getMonth()+1) < 9 ? '0'+ (today.getMonth()+1) : today.getMonth()) + '-' + (today.getDate() < 9 ? '0' + (today.getDate()) : today.getDate())
    axios.get(`https://cors-anywhere.herokuapp.com/https://www.skiddle.com/api/v1/events/search/?api_key=4bf27d4db7486be5b02c0d7dd0fa06af&latitude=${latitude}&longitude=${longitude}&radius=3&order=distance&description=1&minDate=${date}&maxDate=${date}&limit=100`)
      .then(res => this.setState({ events: res.data, userLat: latitude, userLng: longitude}))
  }
  ```
  ```
  componentDidMount() {
    //test for presence of geolocation
    if ('geolocation' in navigator) {
      navigator.geolocation.getCurrentPosition((pos) => {
        const {latitude, longitude}  = pos.coords
        this.getEvents(latitude, longitude)
        //this.setState({ userLat: latitude, userLng: longitude })
```
```
const markerElement = document.createElement('DIV')
markerElement.className = `${type}`
return new mapboxgl.Marker(markerElement)
  .setLngLat({ lat: latitude, lng: longitude })
  .addTo(this.map)
  .setPopup(popup)
  ```
  ![screenshot 2019-02-23 at 10 32 53](https://user-images.githubusercontent.com/42512889/53285247-699b2080-3756-11e9-80c2-620c8dc04ea7.png)

 Clicking to the pinpoint the user is able to check what kind of event is it and also can be redirect to ‘buy ticket’ website and ‘get direction’ to google maps as external link.
![screenshot 2019-02-23 at 10 47 56](https://user-images.githubusercontent.com/42512889/53285453-7f114a00-3758-11e9-8e9b-35d8e9895e5a.png)
![screenshot 2019-02-23 at 10 49 06](https://user-images.githubusercontent.com/42512889/53285471-ae27bb80-3758-11e9-8e5b-d7d83067b5dc.png)
![screenshot 2019-02-23 at 10 50 38](https://user-images.githubusercontent.com/42512889/53285483-e0391d80-3758-11e9-8a05-3e1b970f78aa.png)
```
const popup = new mapboxgl.Popup({offset: 20})
  .setHTML(`
    <div class="event-image">
      <img src="${image}" alt="${name}" />
    </div>
    <h4>${name}</h4>
    <i>${venue}</i>
    <p>${desc}</p>
    <a href="${link}" target="_blank">Get Ticket</a>
    <a href="https://www.google.com/maps/dir/?api=1&origin=${this.props.userLat},${this.props.userLng}&destination=${latitude},${longitude}" target="_blank" > Directions </a>
    `)
```

 Every events has been then categorised by different colour depending on ‘type of’ event.
![screenshot 2019-02-23 at 10 51 43](https://user-images.githubusercontent.com/42512889/53285499-065ebd80-3759-11e9-89ee-3fb71a0e2bae.png)


## Challenges




### Wins





# Future features
