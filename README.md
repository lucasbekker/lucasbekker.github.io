# [lucasbekker.github.io](https://lucasbekker.github.io)

For local development/deployment:

Using Bash on Windows / Ubuntu 16.04 LTS / Ubuntu 18.04 LTS

    # Install Ruby from the brightbox repository and required components.
    sudo apt-add-repository ppa:brightbox/ruby-ng
    sudo apt update
    sudo apt install ruby2.5 ruby2.5-dev build-essential dh-autoreconf libssl-dev zlib1g-dev

    # Install bundler.
    sudo gem update
    sudo gem install bundler

    # Move to the directory containing the git repository.
    cd lucasbekker.github.io

    # Install the required gems.
    sudo bundle install
    bundle install

    # Locally host the website
    bundle exec jekyll serve
