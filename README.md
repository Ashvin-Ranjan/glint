# GLINT
Github Logistics In N Technology

## Setup

### Setting up N

Follow the [install instructions](https://github.com/nbuilding/N-lang#install-n) for N

### Config setup

To control settings in GLINT, in the `config` folder create a `config.json`, this will allow you to put settings in to control GLINT, here are the fields you are able to control:

`config.json` is the main config file for GLINT, the options here are:
- `repoAuthor`: The author of the repo (Default: "")
- `repoName`: The name of the repo (Default: "")
- `export`: Should it export the data to `export.json` (Default: `false`)
- `checkTeams`: Query teams instead of users (Default: `false`)

After you are done setting up the `config.json` if the repo is public then you are ready to go!
### Private Repos

If the repo is private create a user token and echo it into `/config/.token`, then you are ready to go!

## Running GLINT

Run `n --file glint.n` to start up the server then you can go to http://localhost:8080

You can also make a `GET` request to http://localhost:8080/data to get the json data

## Maintaining GLINT

Please see [maintaining.md](./docs/maintaining.md)