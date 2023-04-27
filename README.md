# Near-fungible-token
Prerequisites
Before we start, we need to accomplish some prerequisites:

1. Create an account on the Near Testnet: Follow the instructions on the page to create your testnet account.
2. Install node (version ≥ 12): We recommend using NVM (Node Version Manager is a tool that allows you to manage multiple active node.js versions) to install node.
https://github.com/coreybutler/nvm-windows/releases

After you sucessfully installed nvm you have to install node, in our project we used the v12.22.7.
To install node through NVM, use this command.
$ nvm install v12.22.7

3. Make sure you’ve installed yarn: To install yarn, use the following command:
$ npm install -g yarn

4. Install near-cli:
$ npm install -g near-cli

5. After you have successfully installed near-cli, you have to login from your terminal:
$ near login

6.Install git: If you need to install git on your PC, you can find the documentation here.

Let’s start
1. Open your terminal, use git to clone the repository, open the cloned directory in your terminal, and install the dependencies:
$ git clone https://github.com/DiffuseStable/near-fungible-token-example
$ cd near-fungible-token-example
$ yarn install

2. (optional) Open the cloned repository with your favourite editor.

3. After that, in the file: src/main/assembly/index.ts you can edit the function ft_initialize and change the parameters passed in the ft_initialize_impl function.

The parameters used in this example are 4:

“TokenName” is the name of the token to create.
“SYMB” is the symbol of the token.
The third parameter describes the number of the decimals of the tokenbase.
64TokenSvg is the base 64 icon of the token shown in the wallet.

4. Build the project:
$ yarn build:release

5. After your token is successfully built, you need to deploy it:
$ near dev-deploy ./build/release/main.wasm 

output: Starting deployment. Account id: dev-1682507907094-70452316718780, node: https://rpc.testnet.near.org, helper: https://helper.testnet.near.org, file: ./build/release/main.wasm
Transaction Id 3Ucxfw5qU6fJnjBQxrPmiEbCs8b1uey9oaGrc6Vv9iMT
To see the transaction in the transaction explorer, please open this url in your browser
https://explorer.testnet.near.org/transactions/3Ucxfw5qU6fJnjBQxrPmiEbCs8b1uey9oaGrc6Vv9iMT
Done deploying to dev-1682507907094-70452316718780


6. Initialize
near call $CONTRACT ft_initialize — account-id $ID_ACCOUNT
In our case it is near call dev-1682507907094-70452316718780 ft_initialize  --accountId pegasuslp.testnet

7. Mint
$near call dev-1682507907094-70452316718780 ft_mint '{"account": "pegasuslp.testnet", "receiver_id": "pegasuslp.testnet", "amount": "100000000000000000000000"}' --account_id pegasustest3.testnet

# for deploying contract in sub-accounts
near create-account abcd.pegasuslp.testnet --masterAccount pegasuslp.testnet








