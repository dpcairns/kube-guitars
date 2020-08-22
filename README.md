the problem now is that I bundled the localhost:3000 into the react build when i built my docker image . . . no way to adjust the REACT_APP_API_KEY without a fresh build. but no way to know ahead of time what the NodePort endpoint will be in kubernetes land . . . hmmm

Therefore, right now i'm cheating by exposing the backend publically. Now both have a lodebalancer exposing them to outside traffic. The react app is served through nginx on port 80, and the backend through the node app on port 3000.

I'd like to find a way to use the NodePort to do this instead . . . but maybe this is fine. Using the NodePort would mean, like, building the react app again? With the URL of the internal network? Somehow?

I was able to get it to work by plugging in a heroku postgres...now to get it running with my own SQL pod