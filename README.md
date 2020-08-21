# SeleryAction
> OpenSelery Template for Simple Github Action Integration

[![](https://img.shields.io/gitter/room/protontypes/openselery)](https://gitter.im/protontypes/openselery)        
[![Actions Status](https://github.com/protontypes/seleryexample/workflows/openselery/badge.svg)](https://github.com/protontypes/seleryexample/actions) 
[![stability-experimental](https://img.shields.io/badge/stability-experimental-orange.svg)](https://github.com/emersion/stability-badges#experimental)
![Balance](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/wiki/protontypes/seleryexample/openselery/balance_badge.json&style=flat&logo=bitcoin)  ![Balance](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/wiki/protontypes/seleryexample/openselery/native_balance_badge.json&style=flat&logo=bitcoin)
[![Donate with bitcoin](https://badgen.net/badge/Donate/3PVdiyLPR7MgaeFRJLW9mfuESZS2aAPX9w/orange?icon=bitcoin)](https://raw.githubusercontent.com/wiki/protontypes/openselery/seleryaction/wallet_qrcode.png)  

A project template that shows how to integrate payouts in cryptocurrency with [OpenSelery](https://github.com/protontypes/openselery) into Github Action workflows: 
* Software defined developer payout for your github project - fully transparent in every way.
* Fully customizable payout weights.
* Transparent payout history.
* Scanning dependencies for most programming languages to include all developers. 	
* Only the donor needs a coinbase account at first.	
* Donor creates a transparent payout in your project CI logs and artifacts.	
* Payout is triggered when merging pull requests. 

## Github Action Integration

### Getting Started
1. Press the "Use this Template" button to integrate OpenSelery into a new project or copy the `.github/actions/openselery.yml` and `selery.yml` into your existing project. You can donate to your favorite open source projects on github by forking them and integrating ActionSelery.
2. The [Github](https://github.com/settings/tokens) token is easy to obtain. Add a private access token of your user as a [secret](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) with the name `PAT_SELERY` to your project settings. Set `simulation = True` and `include_dependencies = False` in your `selery.yml` for testing OpenSelery without a Libraries.io token or Coinbase tokens.
3. Enable your Github Actions by pressing the Action tab on on your project main page.
4. Create some commits in your project with a user who publishes their email address in their Github profile. Push these commits to you master branch. OpenSelery should now run in simulation mode on your project. Check the Action logs for further information.

### Add Dependency Scanning
1. To support dependency scanning add the [Libraries.io](https://libraries.io/api) token the Github secrets of your projects as `LIBRARIES_API_KEY` and set `include_dependencies = True`. 
2. OpenSelery supports all dependency manifesto files that are supported by [bibliothecary](https://github.com/librariesio/bibliothecary).
3. Push the changes to your master branch and see OpenSelery gather contributors of your dependencies to include in the payout. 

### Go Live and Payout
1. Buy a small amount of cryptocurrency with Coinbase. See the [price list](https://help.coinbase.com/en/coinbase/trading-and-funding/pricing-and-fees/fees.html) for transferring money to the Coinbase account. OpenSelery will require your Coinbase tokens. Configure the [access control settings](https://github.com/protontypes/openselery/wiki/Coinbase-Settings) of the automated Coinbase account with the required permissions. Do not give the token more permissions than recommended. 
2. Never transfer or store large amounts in automated cryptocurrency wallets. Use [recurring automated buys](https://blog.coinbase.com/easier-recurring-buys-and-sells-on-coinbase-9a3cd7ea934e) to recharge you wallet on a regular base. 
3. Add the token of Coinbase to your project secrets as `COINBASE_TOKEN` and `COINBASE_SECRET`.
4. Set the simulation parameter to `False` to enable payout. You should go live before simulating once with the current setting.
5. Since OpenSelery is using your Wiki to store OpenSelery information like transaction history or QR code you need to create at least one page in your wiki so that Github creates another repository that is connected to project. A successful run will push Action artefacts to the `openselery` folder in the wiki.
6. Push the changes to the selery.yml to your master branch.
7. Check Action logs of selery.yml to see how OpenSelery is distributing investment into your project.  
8. See the transaction history of your wallet under `https://github.com/<your_namespace>/<your_project_name>.wiki.git/openselery`
