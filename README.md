# Peatio Trading UI Tradingview

## Installation steps


### Install JavaScript Runtime

A JavaScript Runtime is needed for Asset Pipeline to work. Any runtime will do but Node.js is recommended.

    curl -sL https://deb.nodesource.com/setup | sudo bash -
    sudo apt-get install nodejs

### Setup production environment variable

    echo "export RAILS_ENV=production" >> ~/.bashrc
    source ~/.bashrc
    

##### Clone the Source

    mkdir -p ~/peatio
    git clone git@github.com:irmaster/peatio-trading-ui.git ~/peatio/trading-ui
    cd peatio/current

    ＃ Install dependency gems
    bundle install --without development test --path vendor/bundle

##### Configure Peatio

**Prepare configure files**
    bin/init_config

**Config settings**
    vim config/application.yml
    
##### Compiling assets
    bin/rake tmp:clear tmp:create
    bin/rake assets:clobber assets:precompile
    
    sudo service nginx restart    
    
