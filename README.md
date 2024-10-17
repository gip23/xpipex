# XPipe Vault (Keep this repository private!)

This repository contains all connection information that is designated to be shared.

You can sync with this repository in all XPipe application instances the same way, every change you make in one instance will be reflected in the repository. 

## Category list

- **Connections**
  - [**hdts**](categories/c3098abb-1659-4f18-b972-5193ede72d18)
- **Scripts**

## Connection list

**All connections / hdts**

- [**aura-wp-website**](stores/7e0e6cef-4d80-4e34-afe1-7ddf0ddf8331)
  - [**Shell Environments**](stores/bc7521ac-f6cd-3c87-a4fe-f25359b88b06)
    - [**bash**](stores/0b8dd198-a476-49b0-9644-5d3a0fb6f596)
    - [**dash**](stores/cfce011f-f206-4201-bf9d-a756232f14ff)
- [**hdts-dev**](stores/6f493eac-8399-4c31-8ba5-f15b9254c95d)
- [**hdts-dev2**](stores/013a3606-8c06-4ee5-92b5-923d699c0975)
- [**hdts-prod**](stores/2e3ebf94-a29d-4b55-9c7c-978416d96f23)
  - [**Shell Environments**](stores/4d59b269-1678-3add-8821-d1d30062a3e3)
    - [**bash**](stores/0fa37b7c-4d4d-4a4a-bd1f-7395e06c1212)
    - [**dash**](stores/ed98a04f-7574-4f58-9347-7bec6d3364dc)


## Secret encryption

You have the option to fetch any sensitive information like passwords from outside sources like password managers or enter them at connection time through a prompt window. In that case, XPipe doesn't have to store any secrets itself.

In case you choose to store passwords and other secrets within XPipe, all sensitive information is encrypted when it is saved using AES with either:

- A dynamically generated key file `vaultkey` (The data can then only be decrypted with that file present)
- A custom master passphrase that can be set by you in the settings menu combined with the vault key file (This option is only as secure as the password you choose)

By default, general connection data is not encrypted, only secrets are.
So things like hostnames and usernames are stored without encryption, which is in line with many other tools.
There is an available vault setting to encrypt all connection data if you want to do that.

## Cloning the repository on other systems

Nowadays, most providers require a personal access token (PAT) to authenticate from the command-line instead of traditional passwords.
You can find common (PAT) pages here:
- **GitHub**: [Personal access tokens (classic)](https://github.com/settings/tokens)
- **GitLab**: [Personal access token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)
- **BitBucket**: [Personal access token](https://support.atlassian.com/bitbucket-cloud/docs/access-tokens/)
- **Gitea**: `Settings -> Applications -> Manage Access Tokens section`
Set the token permission for repository to Read and Write. The rest of the token permissions can be set as Read.

Even if your git client prompts you for a password, you should enter your token unless your provider still uses passwords.

If you don't want to enter your credentials every time, you can use any git credentials manager for that.
For more information, see:
- https://git-scm.com/doc/credential-helpers
- https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git

## Troubleshooting

### Adding categories to the repository

To have your connections of a category put inside your git repository,
you need to click on the `⚙️` icon (when hovering over the category)
in your `Connections` tab under the category overview on the left side.
Then click on `Add to git repository`, to sync the category and connections to your git repository.

### Some local connections are not synced

Any connection under the local machine can not be shared as it refers to connections and data that are only available on a specific system.

Certain file-based connections, for example SSH configs, can be shared via git if the underlying data, in this case the file, have been added to the git repository as well in the `data` directory.

### Other issues

If you encounter any other issues, you can try interacting with the cloned repository manually.
You can find it at `%USERPROFILE%\.xpipe\storage\` or `~/.xpipe/storage/`.
XPipe will call your installed git client, so any potential issues with your local git client also transfer to XPipe.

To understand what went wrong, you can also launch XPipe in debug mode at `Settings -> Troubleshoot -> Launch in debug mode`.
This will tell you in detail what git commands are executed.