# A collection of dockerfiles

After a new setup for my laptop I figured I would try to keep it
as clean as possible (depdenency wise).

So here will be a collection of dockerfiles I use to compile vim and other random bits of software.

To get a running version of the software run docker build . -t app

* They will per default compile to /usr/local/stow/app
* After compilation you can start an container (docker run -i -t app)
* Find the container id (docker ps)
* Copy the compiled app to your filesystem (docker cp id:/usr/local/stow/app /usr/local/stow
* Use stow to put all symlinks in place (stow app (has to be run in /usr/local/stow))

Use the software without having to install all build deps

Currently available are

* [tmux](tmux/Dockerfile)
* [vim](vim/Dockerfile)
