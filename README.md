# OpenSelery by Example
A Simple project example showing openselery integration for multiple platforms.    
Just add badges with your Bitcoin address to your README.md and copy `.github/workflows/openselery.yml` to your project.    

Modify the configuration in the `openselery.yml` to your needs.  

[![Actions Status](https://github.com/protontypes/seleryexample/workflows/openselery/badge.svg)](https://github.com/protontypes/seleryexample/actions)
[![Donate with bitcoin](https://en.cryptobadges.io/badge/small/3PVdiyLPR7MgaeFRJLW9mfuESZS2aAPX9w)](https://en.cryptobadges.io/donate/3PVdiyLPR7MgaeFRJLW9mfuESZS2aAPX9w)     

### Continuous Integration  
1. Add the token of libraries.io and coinbase to your [secrets](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets).

2. You can integrate OpenSelery in your CI by copying the `openselery.yml` file into your `.github/actions/` destination project directory. Check the setting before running your CI Pipeline:

  ```
  cat .github/actions/openselery.yml 
  ```
3. Set the simulation parameter to `False` if you want pay developers or `True` to try out OpenSelery on your project.

4. Depending on the `openselery.yml` a payout will be triggered. The default setting runs OpenSelery with every new version of the destination project. 

5. Protect your master branch in the Github Setting under `Branches`. Activate the `Restrict who can push to matching branches` option. 

6. To enable runner diagnostic logging, set the following secret in the repository that contains the workflow.
This also changes the workflow behavior so that Github API calls are more stable:
```
ACTIONS_RUNNER_DEBUG to true. 
```

