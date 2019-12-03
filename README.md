## Install

Node Version

    v8.2.1

`package-lock.json` might has some issues to the repo, disabled it.

I completely forgot the dependencies of the site, had to have a friend reminding me how to install. I'd better start to doc everything toady, it has been a good lesson.

    ruby -v
    gem install bundler
    bundle
    npm i
    npm i -g gulp-cli


Issues when running bundler:

    While executing gem ... (Errno::EPERM)
    Operation not permitted - /usr/bin/bundle

    sudo gem install bundler -n /usr/local/bin

Github page now supports custom domain with HTTPS, don't forget to add or udpate the CNAME next time.

