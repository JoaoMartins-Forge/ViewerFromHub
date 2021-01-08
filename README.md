# ViewerFromHub
Viewer from BIM 360 documents (.NET Core) where each branch holds a different extension.
# Setup

## Prerequisites

1. **Forge Account**: Learn how to create a Forge Account, activate subscription and create an app at [this tutorial](http://learnforge.autodesk.io/#/account/). 
2. **Visual Studio**: Either Community (Windows) or Code (Windows, MacOS). 
3. **.NET Core**: basic knowledge of C#.
4. **ngrok**: Routing tool, [download here](https://ngrok.com/).

Use of this sample requires Autodesk developer credentials.
Visit the [Forge Developer Portal](https://developer.autodesk.com), sign up for an account
and [create an app](https://developer.autodesk.com/myapps/create) that uses Data Management and Model Derivative APIs.
For this new app, use `http://localhost:3000/api/forge/callback/oauth` as Callback URL, although is not used in a 2-legged flow.
Finally, make a note of the **Client ID** and **Client Secret**.

## Running locally

Clone this project or download it.
We recommend installing [GitHub desktop](https://desktop.github.com/).
To clone it via command line, use the following (**Terminal** on MacOSX/Linux, **Git Shell** on Windows):

    git clone https://github.com/JoaoMartins-Forge/ViewerFromHub


**ngrok**

Run `ngrok http 3000 -host-header="localhost:3000"` to create a tunnel to your local machine, then copy the address into the `FORGE_WEBHOOK_URL` environment variable.

**Environment variables**

At the `.vscode\launch.json`, find the env vars and add your Forge Client ID, Secret and callback URL. Also define the `ASPNETCORE_URLS` variable. The end result should be as shown below:

```json
"env": {
    "ASPNETCORE_ENVIRONMENT": "Development",
    "ASPNETCORE_URLS" : "http://localhost:3000",
    "FORGE_CLIENT_ID": "your id here",
    "FORGE_CLIENT_SECRET": "your secret here",
    "FORGE_CALLBACK_URL": "http://localhost:3000/api/forge/callback/oauth",
    "FORGE_WEBHOOK_URL": "your ngrok address here: e.g. http://abcd1234.ngrok.io"
},
```
### Troubleshooting

1. **Cannot see my BIM 360 projects**: Make sure to provision the Forge App Client ID within the BIM 360 Account; [learn more here](https://forge.autodesk.com/blog/bim-360-docs-provisioning-forge-apps). This requires the Account Admin permission.

2. **error setting certificate verify locations** error: may happen on Windows, use the following: `git config --global http.sslverify "false"`

## License

This sample is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT). Please see the [LICENSE](LICENSE) file for full details.
