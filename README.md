# shopware-platform-contrib

How to get a workable contribution setup using `dockware/dev` and `shopware/platform`.

```bash
# start the container
docker compose up -d

# clonse shopware/platform (renamed shopware/shopware)
mkdir -p src/platform
git clone https://github.com/shopware/shopware src/platform
# add our forked repository
cd src/platform
git remote add forked git@github.com:mromeike/shopware.git
cd ../..

# do your changes
phpstorm src/platform

# enter the container
docker compose exec shopware bash
# set up dependencies
cd platform
sudo composer self-update
sudo composer run setup

# run tests
sudo composer run phpunit
# or filter which tests to run
FILTER='...'
sudo php ./vendor/bin/phpunit -c phpunit.xml.dist --filter=$FILTER

# inspect container in test env
APP_ENV=test bin/console debug:...
```

## Scripts

Make sure to execute any scripts (`scripts/`) from the root directory.