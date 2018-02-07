========
 README
========

Installing core and virtualenv
==============================

::
   nvm use default
   Now using node v9.2.0 (npm v5.5.1)

   npm init
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

UPDATE: docker threw errors I couldn't understand; trying to run
locally threw error about not finding python2. Created separate dir
for localstack with python2 venv then non-docker localstack
started. Ran wihtout docker. In serverless dir set AWS_PROFILE then
ran "sls deploy --stage local"::

  2018-02-07T16:56:42:ERROR:localstack.services.generic_proxy: Error forwarding request: list index out of range Traceback (most recent call last):
    File "/Users/chris/Projects/vstudios/slslocal/localstack/.venv2/lib/python2.7/site-packages/localstack/services/generic_proxy.py", line 215, in forward
      updated_response = self.proxy.update_listener.return_response(**kwargs)
    File "/Users/chris/Projects/vstudios/slslocal/localstack/.venv2/lib/python2.7/site-packages/localstack/services/cloudformation/cloudformation_listener.py", line 183, in return_response
      template_deployer.deploy_template(template, req_data.get('StackName')[0])
    File "/Users/chris/Projects/vstudios/slslocal/localstack/.venv2/lib/python2.7/site-packages/localstack/utils/cloudformation/template_deployer.py", line 485, in deploy_template
      resource['__details__'] = stack_resources[0]
  IndexError: list index out of range


Try with "localstack start --docker" and same sls invocation, where I
do get a web console::

  sls reports the same::

      at serverless.init.then (/Users/chris/Projects/vstudios/slslocal/slslocal/node_modules/serverless/bin/serverless:42:50)

 but we get no logging or other output from Docker... because it's
 sealed inside docker.
