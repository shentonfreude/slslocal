========
 README
========

Installing core
===============

::
   pyenv local 3.6.3

   nvm use default
   Now using node v9.2.0 (npm v5.5.1)

   npm install --save-dev serverless
   npm install --save-dev serverless-localstack

   sls create --template aws-python3 --path slslocal --name slslocal
   
