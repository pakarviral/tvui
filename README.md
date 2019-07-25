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


# TradingView Charting Library and Ruby on Rails Integration

## How to add

1. Copy `charting_library` folder from https://github.com/tradingview/charting_library/ to `/vendor/assets/javascripts`. The earliest supported version of the Charting Library is 1.12. If you get 404 then you need to [request an access to this repository](https://www.tradingview.com/HTML5-stock-forex-bitcoin-charting-library/).

1. Copy `datafeeds` folder from https://github.com/tradingview/charting_library/ to `/vendor/assets/javascripts`.

##### Config nginx
```
server {
    .
    .
    .
    root /home/user/peatio/public;
    location ~ ^/(?:trading|trading-ui-assets)\/ {
        passenger_enabled on;
        gzip on;
        passenger_app_env production;
        root  /home/user/trading-ui/public;
    }  
}
```

##### Compiling assets
    bin/rake tmp:clear tmp:create
    bin/rake assets:clobber assets:precompile
    
    sudo service nginx restart    
    
