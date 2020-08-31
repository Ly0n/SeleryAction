# SeleryAction
LibreSelery Template for Simple Github Action Integration

[![Join the chat at https://gitter.im/protontypes/LibreSelery](https://badges.gitter.im/protontypes/LibreSelery.svg)](https://gitter.im/protontypes/LibreSelery?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![stability-experimental](https://img.shields.io/badge/stability-experimental-orange.svg)](https://github.com/emersion/stability-badges#experimental)

[![Actions Status](https://github.com/protontypes/seleryaction/workflows/seleryaction/badge.svg)](https://github.com/protontypes/seleryaction/actions) 
![Balance](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/wiki/protontypes/seleryexample/libreselery/balance_badge.json&style=flat&logo=bitcoin)  ![Balance](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/wiki/protontypes/seleryexample/libreselery/native_balance_badge.json&style=flat&logo=bitcoin)
[![Donate with bitcoin](https://badgen.net/badge/Donate/3PVdiyLPR7MgaeFRJLW9mfuESZS2aAPX9w/orange?icon=bitcoin)](https://raw.githubusercontent.com/wiki/protontypes/libreselery/seleryaction/wallet_qrcode.png)  
[![Transaction History](https://badgen.net/badge/icon/Transaction%20History?icon=bitcoin&label)](https://github.com/protontypes/seleryaction/wiki/Transaction-History)

A project template that shows how to integrate [LibreSelery](https://github.com/protontypes/libreselery) into GitHub Action workflows, which allows to pay contributors in cryptocurrency.

## Github Action Integration

### Getting Started
1. Press the "Use this Template" button to integrate LibreSelery into a new project or copy the `.github/actions/libreselery.yml` and `selery.yml` into your existing project.
2. For running LibreSelery, a [GitHub token](https://github.com/settings/tokens) is needed, which you can obtain easily through your GitHub settings (it does not need any scopes). Then add the private access token of your user as a [secret](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) with the name `PAT_SELERY` to your project settings.
3. Set `simulation: True` and `include_dependencies: False` in your `selery.yml` for testing LibreSelery without a Libraries.io token or Coinbase tokens (if you have not created a wallet yet set `perform_wallet_validation: False`).
3. Enable your Github Actions by pressing the Action tab on your project main page.
4. For further testing, create some commits in your project. Verify that the user has a public email address in the GitHub profile. Push these commits to you master branch. LibreSelery should now run in simulation mode on your project. Check the Action logs for further information. Don't be surprised, the action will fail because no payout receipt can be generated in simulation mode.

You can even donate to your favorite open source projects on GitHub by forking them and integrating SeleryAction yourself - this way the original contributors can get funding. Afterwards, you should consider making a Pull Request to the original project.

### Add Dependency Scanning (optional)
1. To support dependency scanning add the [Libraries.io](https://libraries.io/api) token to the GitHub secrets of your projects as `LIBRARIES_API_KEY` and set `include_dependencies: True` in your `selery.yml`. 
2. LibreSelery supports all dependency manifesto files that are supported by [bibliothecary](https://github.com/librariesio/bibliothecary).
3. Push the changes to your master branch and check how LibreSelery gathers contributors of your dependencies, which will be considered for payout. 

### Add Tooling Depdencies (optional)
Apart from the project dependencies, you might have tooling dependencies whose contributors you would like to consider in the payout. You can add manual dependencies in the `tooling_repos.yml`.

1. Add the tooling dependencies in the `tooling_repos.yml` file.
2. Set `include_tooling_and_runtime: True` in your `selery.yml.

### Go Live and Payout Contributors
1. Buy a small amount of cryptocurrency with Coinbase. See the [price list](https://help.coinbase.com/en/coinbase/trading-and-funding/pricing-and-fees/fees.html) for transferring money to the Coinbase account. LibreSelery will require your Coinbase tokens. Configure the [access control settings](https://github.com/protontypes/libreselery/wiki/Coinbase-Settings) of the automated Coinbase account with the required permissions. Do not give the token more permissions than recommended. 
2. Never transfer or store large amounts in automated cryptocurrency wallets. Use [recurring automated buys](https://blog.coinbase.com/easier-recurring-buys-and-sells-on-coinbase-9a3cd7ea934e) to recharge you wallet on a regular base. 
3. Add the token of Coinbase to your project secrets as `COINBASE_TOKEN` and `COINBASE_SECRET`.
4. Set the simulation parameter to `simulation: False` to enable payout. You should simulate the payout at least once before going live with the current setting.
5. Since LibreSelery is using your Wiki to store LibreSelery information like transaction history or QR code you need to create at least one page in your wiki so that Github creates another repository that is connected to the project. A successful run will push Action artifacts to the `libreselery` folder in the wiki.
6. Set the `perform_wallet_validation: True` and `bitcoin_address: "<your Bitcoin Address>"`. You will find your addresses on the coinbase website [here](https://www.coinbase.com/settings/crypto-addresses). Push the changes of the selery.yml to your master branch.
7. Check Action logs to see how LibreSelery is distributing investment into your project. 
8. See the transaction history of your wallet under `https://github.com/<your_namespace>/<your_project_name>.wiki.git/libreselery` and the donation website for your project under `https://github.com/<your_namespace>/<your_project_name>/wiki/Donation`
9. Add a [`FUNDING.yml`](https://github.com/protontypes/seleryaction/blob/master/.github/FUNDING.yml) file to your project .github folder to create a Github Sponsor Button with LibreSelery. 
10. In your wiki you will also find the static badges showing your wallet balance in [EUR](https://raw.githubusercontent.com/wiki/protontypes/libreselery/openselery/balance_badge.json&style=flat&logo=bitcoin) and [BTC](https://raw.githubusercontent.com/wiki/protontypes/libreselery/openselery/native_balance_badge.json&style=flat&logo=bitcoin). 
