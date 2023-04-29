# Pound4Pound/
.github/dependabot.yml
const { createAppAuth } = require('@octokit/auth-app');

const { Octokit } = require('@octokit/rest');

const start = async () => {

  const appOctokit = new Octokit({

    authStrategy: createAppAuth,

    auth: {

      appId: process.env.APP_ID,

      privateKey: JSON.parse(process.env.CLIENT_PRIVATE_KEY),

      // installationId: process.env.INSTALLATION_ID,

      clientId: process.env.CLIENT_ID,

      clientSecret: process.env.CLIENT_SECRET,

    },

  });

  const { data } = await appOctokit.request('/app/installations');

  // If you've only installed it once, this should be the one

  const installationId = data[0].app_id;

  console.log(installationId);

};

start();main
