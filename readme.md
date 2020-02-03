# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2: Art Journey

This is a website on which you can search for art, using any keyword you like (such as "blue", "beach" or "Rembrandt"). The time frame of this project was 48 hours.

## Built with
* React
* Sass
* Axios
* Bulma
* Express
* Node.js
* Git
* GitHub

## Deployment
The website is deployed on Heroku and can be found [here](https://your-art-journey.herokuapp.com/).

## Getting started
Clone or download the repo. Run 'npm i' from the root directory to download all of the needed packages and then type 'npm run start'. The project will run on localhost:8000.

## Website architecture
The website consists of a home page, which is also the index page, with a search bar and two different pages to show the individual art works. 

### 1. Home/Index page

<img src="src/assets/art-journey-2.png" alt="Website search results" height="300"/>

The home page consists of the name of the website and a search bar. The user can use a wide range of keywords, from colours to objects and places. When a user has searched for something, the data is pulled using the Rijksmuseum API. The search results appear after half of the images have loaded, showing a spinner before this has happened. Below is the function which counts the loaded images:

```
  handleOnLoad = () => {
    this.setState({
      imageCounter: this.state.imageCounter + 1
    })
    if (this.state.artPieces.length === 1) {
      this.setState({ loaded: true })
    } else if (this.state.imageCounter === this.state.artPieces.length / 2) {
      this.setState({ loaded: true })
    }
  }
```


### 2. Show pages

<img src="src/assets/art-journey-4.png" alt="Website show page" height="300"/> <img src="src/assets/art-journey-3.png" alt="Website show page" height="300"/>

The website has two different show pages, depending on the art works. If it's a horizontal work, the image will be displayed with the details underneath it. Otherwise, the image is placed next to the details. When hovering the mouse over the artwork, those parts are magnified. When known, there is also a map on this page showing where the art piece has been made. 

## Challenges and future improvements
* Because the images of the artworks have a very high resolution, it takes a long time to download them. This was especially problematic on the results page as it took too much time before every work had been downloaded. This has been solved by compressing the images when pulling them for the result page, setting their size in the get request. The spinner also helps with this problem as it shows that something is happening and only disappears when half of the images have been downloaded.

* This website uses the Rijksmuseum API, which is a Dutch museum. As a consequence, some of the titles are in Dutch instead of English. In the future, it would be a good idea to add a translation API and translate the titles before showing them on the page. 

* This project had to be made within 48 hours, so there wasn't enough time to make the website fully responsive and functional on all devices. For example, the magnifying glass makes it harder to scroll on a phone. In the future, this functionality should either be changed or removed when the user is on a mobile device.