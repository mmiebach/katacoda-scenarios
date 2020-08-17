## devonfw setup

Create the directory where the devonfw ide will be installed.

`mkdir devonfw`{{execute}}

`cd devonfw`{{execute}}


To install devonfw execute the following commands. More information about setting up your ide on https://devonfw.com/website/pages/docs/devonfw-ide-introduction.asciidoc.html#setup.asciidoc
`wget -c https://bit.ly/2BCkFa9 -O - | tar -xz`{{execute}}

`bash setup`{{execute}}


The installtion process may take a while.

The installation routine will ask you for a settings url. You can continue with the default settings by pressing return.

Accept the licence agreements.
`yes`{{execute}}

You can decline when asked wether you want to share data with Angular Team `N`{{execute}}

You will need to refresh your terminal in order to be able to use devon. Run `. ~/.bashrc`{{execute}}

## Install cobigen

`devon cobigen`{{execute}}

Cobigen Cli will be installed inside the software directory of your devonfw ide.








