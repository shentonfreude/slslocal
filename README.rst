========
 README
========

Installing core and virtualenv
==============================

::
   nvm use default
   Now using node v9.2.0 (npm v5.5.1)

   npm install --save-dev serverless
   npm install --save-dev serverless-localstack

   pyenv local 3.6.3
   virtualenv .venv3
   source .venv3/bin/activate
   pip install localstack

Create a Serverless project
===========================


   sls create --template aws-python3 --path slslocal --name slslocal
   cd sls local

Start Localstack
================

On Mac we have to avoid TMPDIR symlink docker can't mount::

   TMPDIR=/private$TMPDIR localstack start --docker

There's now a web viewer on http://localhost:8080
