# Install Node.js

Please install `Node.js, version 12.18.*LTS or higher`:

```sh
apt install nodejs
apt install npm
```

## Add `node` and `npm` to `PATH`
Please execute the suggested command to add the node `bin` directory to the `PATH` (this line can be different based in your shell):

```sh
echo 'export PATH="/home/cedar-dev/.nvm/versions/node/v14.17.0/bin"'
```

## Check the installation

Close the previously active terminal (or source your profile) to have `node` and `npm` in your `PATH`.

`Node.js` will come with `npm` as well.
You can check if both of them are installed:
 
```sh
node --version
npm --version
```

You should see the following:

```
v14.17.0
7.15.0
```
