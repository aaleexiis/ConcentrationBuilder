# ConcentrationBuilder
JS Game for Tresensa Inc

Developer: Aleksandra Mladenovic
Contact details:
* email: aaleexiis@gmail.com
* phone: +385 91 5697 341
* address: Karla Metikosa 3, 10000 Zagreb, Croatia

## This site is owned and operated by Aleksandra Mladenovic.

## Global Setup

1. install node and npm http://nodejs.org/
2. run `npm install -g grunt-cli`
3. create `~/.tresensa/buildConfig.json` in your home directory. Inside add your aws credentials and path to a checked out CLientSDK directory like so:

```json
{
	"aws": {
		"accessKeyId": "ACCESS_KEY_ID",
		"secretAccessKey": "ACCESS_KEY_SECRET"
	},
	"clientSDKDir": "/Users/netpro2k/Downloads/ClientSDKs/trunk"
}
```

## Repository Setup

1. Copy `Gruntfile.coffee` and `package.json` from https://svn.tresensa.com/TresensaCoreClient/ClientSDKs/trunk/GameBuild into the trunk of the repository (same directory as index.html)
2. From the trunk directory run `npm install`. This will install the dependancies the build script needs from package.json
3. You should set svn to ignore the "dist" and "node_modules" directory as they are both generated and do not need to be versioned
4. If coming from an old project run `grunt migrate` to update the `lib` external to point to the new location

## Available Tasks

When in the directory with Gruntfile.coffee you have access to the following build tasks

- `grunt update`				Pull down latest build script from svn
- `grunt migrate`				Update externals for the project to use new lib directory
- `grunt clean`					Wipe out any files created by build.
- `grunt build`					Build game into dist according to settings in GameConfig.
- `grunt server`				Runs 'grun build', then starts a local server, and opens browser.
- `grunt deploy[:qa|:prod]`		Runs 'grunt build', then deploys to specified environment (default qa).
- `grunt` 						Alias for "server" task.

## Special handling for GameConfig.DEBUG

If the GameConfig has DEBUG set to true, the `grunt server` task will mount lib-debug from your `clientSDKDir`'s dist directory (from you buildConfig.json). This will allow you to test the game against a live version of tresensa SDK. Combined with the new SDK build script this allows for live editing of tresensa SDK.
