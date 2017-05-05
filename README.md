# Build a GitHub bot!

This guide will walk you through building a simple [GitHub Integration](https://developer.github.com/early-access/integrations/) that ensures every commit has the word bananas and get it running on a test repository. All of the source code you need is in this gist.

Here's what it will look like when your commits are not bananas:

![](https://cloud.githubusercontent.com/assets/173/25726554/57668568-30ea-11e7-8100-3c425893c7d8.png)

…and here's what it will look like when your commits are bananas:

![](https://cloud.githubusercontent.com/assets/173/25726631/bc81adba-30ea-11e7-96e1-2fde42ab9fed.png)


Ready? Let's get started!

1. Clone this gist

        $ git clone https://gist.github.com/bkeepers/546efd41fa08f1af418d5c58e02ec696 bananas

1. Make sure you have a recent version of [Node.js](https://nodejs.org/) installed. If you're on a Mac, `brew install node` will do it for you.

        $ node --version
        v7.8.0

1. `package.json` lists the dependencies for our app. Check it out, and then run:

        $ npm install

1. `index.js` is the meat of the integration. Read through the code and see if you can make sense of what it's doing.

1. [Create a new GitHub Integration](https://github.com/settings/integrations/new) with:

    - **Integration Name**: `yourusername-bananas`, replacing `yourusername` with your GitHub username.

    - **Homepage URL**, **User authorization callback URL**, and **Webhook URL**: Set to `https://yourusername.localtunnel.com/`, again replacing `yourusername` with your GitHub username.

    - **Webhook Secret:** `development`

    - **Permissions**:
      - Commit statuses: **Read & Write**
      - Pull requests: **Read-only**
        - [x] Check the box for **Pull request** events
      - Repository contents: **Read-only**

    - Click **Create integration**

1. Most importantly, your bot needs an adorable icon. Feel free to use `bananas.jpg`.

1. Generate a private key and move it to the project directory.
    ![](https://cloud.githubusercontent.com/assets/173/25724787/c87eb534-30e2-11e7-84df-ecac34a98040.png)

1. Edit `.env` and set `INTEGRATION_ID` to the ID of the integration you just created, and `SUBDOMAIN` to your GitHub username.
    ![](https://cloud.githubusercontent.com/assets/173/25724878/1ef2be60-30e3-11e7-9615-453f1489e942.png)

1. Click the **Install** button on your integration page, and install it on a repository.

1. Go back to your terminal and run `$ npm start` to start the server, which will output `Listening on https://yourusername.localtunnel.me`;

1. Now go to your repository and create a new file, commit it to a branch, and open a pull request.

Want to learn more:

- [other Probot plugins](https://github.com/search?utf8=%E2%9C%93&q=topic%3Aprobot-plugin&type=Repositories)
- [Probot plugin documentation](https://github.com/probot/probot/blob/master/docs/plugins.md)
- [node-github client documentation](https://mikedeboer.github.io/node-github/)
