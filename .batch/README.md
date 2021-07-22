# batch.n
Unit testing software for N

## How to use it

### Installation

The first step is to install `batch.n` and create a `config.json` in the local directory where you want it to be. Then you are ready to set up the config.

### Config

The config currently has 4 settings:
- `directory`: This is the directory of the N files you want to test (Default: "./")
- `differentiation`: This is the differentiation between N files, like `test.egg.n` as opposed to `test.n` (Default: "egg")
- `recursive`: Check folders, TBD (Default: false)
- `all`: Check every file that ends with `.n` (Default: false)

### Running

Run `n --file batch.n`, once it is complete it will generate a file called `carton.n`, you can run this with `n --file carton.n`, and you can see the results of your unit tests!

Copied from [the main readme](https://github.com/ashvin-ranjan/batch.n#readme)

## Updating batch.n

To update `batch.n` run `n --file update.n`, this fill fetch the file from github.