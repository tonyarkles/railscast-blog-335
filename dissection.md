
# How does the deploy.rb stuff work?

Before and after triggers:
* after "deploy" do "deploy:cleanup"
* after "deploy:setup" do "deploy:setup_config"
* after "deploy:finalize_update" do "deploy:symlink_config"
* before "deploy" do "deploy:check_revision"

## What does "cap deploy" do?

Diagram available at https://github.com/capistrano/capistrano/wiki/2.x-Default-Deployment-Behaviour

* deploy:default
  * deploy:update
    * deploy:update_code
    * strategy.deploy!
    * deploy:finalize_update
  * deploy:symlink
  * deploy:restart
 
These tasks are all documented in lib/recipes/deploy.rb in the Capistrano gem. 

# What goes into the nginx.conf?

# What goes into the unicorn stuff? (unicorn_init.sh and unicorn.rb)
