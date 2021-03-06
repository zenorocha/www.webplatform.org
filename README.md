# [WebPlatform](http://www.webplatform.org/)

This is the homepage served at [www.webplatform.org](http://www.webplatform.org/). We are
serving them as non dynamic content due to the fact that we do not need to change the content frequently.

Although this workspace is for the static content of the site, it can also be used to work locally on HTML
and CSS markup and patterns for various projects inside WebPlatform Docs.

The pages are generated through a Node.js static site generator called [DocPad](http://docpad.org/) and allows us to
keep edition DRY by not copy-pasting code in many places while allowing us to have static documents to serve. To learn
more about DocPad, you can refer to their [DocPad documentation](http://docpad.org/docs).

## Installation

*NOTE*: Directives assumes you are using a Unix like Operating System, but [DocPad also works with Microsoft Windows](http://bevry.me/learn/node-install).

1. Install NodeJS and NPM

    You can download node from [nodejs.org](http://nodejs.org/).

    As for NPM, it depends of the Operating system you are using. You can see the NPM installation instruction
    from the [nodejs](http://nodejs.org/) website.

2. As an administrator, install the following packages as global on your workstation

        npm install -g docpad@6.64 gulp

3. Fork the project, and checkout the code

        mkdir -p ~/workspace/webplatform/www
        cd ~/workspace/webplatform/www
        git clone git@github.com:renoirb/www.webplatform.org.git .
        npm install

    This installs all dependencies to work on the project.

4. Create a branch and start your work.

        git checkout -b improving-flexbox-markup

5. Code is managed from the `src/` folder, and what gets changed in it gets regenerated automatically
    by what we call a "watcher", files are regenerated at every changes into `out/` folder.

        docpad run

    You can also leverage work with CSS and JavaScript using built in tools:

    * JavaScript Linting

            gulp lint

    * Compiling SASS files

            ... in progress ...

    * Testing before pushing to the repository

            docpad generate --env=production
            gulp minify --env=production
            npm start

    This gives you an equivalent of what gets deployed in production without watchers.

    * Everything works? Make a pull request from your branch :D

## Deploying

1. Prepare for deploying

        docpad generate --env=production
        gulp minify --env=production
        tar cfz static-$(date '+%Y%m%d').tar.gz out/
        scp static-$(date '+%Y%m%d').tar.gz deployment.webplatform.org:/srv/code/www/archives/

2. ... In progress... 

    Current plan is that when a person who has rights to merge to master, a deployment system will pull from github, run the scripts in the previous step, sync the files with all web servers. Automatically.




## Related

### Depdencies

For more details, see `package.json` file.

* [Gulp](http://gulpjs.com/), JavaScript build system
* [DocPad](http://docpad.org/), static pages generation
* [DocPad plugin "eco"](https://github.com/docpad/docpad-plugin-eco), templating
  * [eco source](https://github.com/sstephenson/eco)
* [DocPad plugin "frontend"](https://github.com/sergeche/docpad-plugin-frontend), managing assets
* [DocPad plugin "livereload"](https://github.com/docpad/docpad-plugin-livereload/), workspace live reload
* [DocPad plugin "marked"](https://github.com/docpad/docpad-plugin-marked), MarkDown support
  * [Marked source](https://github.com/chjj/marked)
* [DocPad plugin "nodesass"](https://github.com/jking90/docpad-plugin-nodesass), NodeJS SASS support
  * [node-sass](https://github.com/andrew/node-sass)
* [DocPad plugin "partials"](https://github.com/docpad/docpad-plugin-partials), view partials

### Useful documentation

Besides reading the source, I found those pages useful.

* [DocPad TemplateData](http://docpad.org/docs/template-data)
* [DocPad Beginner Guide](http://docpad.org/docs/begin)
* [DocPad Meta Data](http://docpad.org/docs/meta-data)
* [Emmet site source (made using DocPad)](https://github.com/emmetio/emmet-docs)
* [DocPad site source (made using DocPad)](https://github.com/docpad/website)
